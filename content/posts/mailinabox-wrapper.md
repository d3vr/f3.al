---
title: "Why I use unique email addresses and how I automate this using Mail-in-a-Box"
slug: "create-email-addresses-using-bash"
date: 2022-11-24
showLastUpdated: false
draft: false
cover: "covers/create-email-addresses-using-bash.webp"
tags: ["bash", "email", "automation"]
categories: ["tutorials"]
---

I use a self-hosted instance of {{< a "https://mailinabox.email/"
"Mail-in-a-Box" >}} for most of my email needs, and one recurrent task that I
find myself doing manually each time is creating new aliases. {{< br >}} In
this post I'll be going into the reasons of why I do this and how I automated
this task using a bash script.

<!--more-->


> **TL;DR**: I make a Bash script to quickly create and delete email aliases in Mail-in-a-Box while handling {{< abbr "MFA" "Multi-factor authentication" >}} and API key generation. [Skip to the script](#the-script).

## Why create and use different aliases?

There's a couple of reasons:

1. **Separation of Concerns**. I like to have a separate email address for each
   account on each website, this way if there's a data breach and there's
   suddenly an influx of spam I'll know who the culprit is. Or other times, the
   website operators freely share your email with other parties and you end up
   receiving unwanted spam, it would be hard to trace it back to the culprit if
   you weren't using different addresses or aliases.
2. **Hard shutdown**. If the website starts sending email I'm not interested
    in and there's no way to unsubscribe (yes I've come across this before), or
    they make it unnecessarily hard to do so, I can just delete the alias or
    assign it to a separate folder.
3. **Privacy**. Assuming you use a different username & password for each
    account, your accounts won't be (easily) traced back to you, although you
    could make the argument that using your own domain, one could assume all
    the accounts belong to you. So maybe if privacy is your main concern, don't
    go this route or give it some more thought.

## How?

Doing this through the {{< a "https://mailinabox.email/api-docs.html"
"Mail-in-a-Box API" >}} is pretty straightforward, you just send a POST request
to the `/mail/aliases/add`[^1] endpoint with `address=alias@example.com`
and `forwards_to=address@example.com` in the body:

{{< code language="bash" title="Create alias request example" collapse="—" expand="+" >}}
curl -X POST "https://box.example.com/admin/mail/aliasses/add" \
            -d "address=alias@example.com" \
            -d "forwards_to=address@example.com" \
            -u "user@example.com:str0ngP4ssw0rd!"
{{< /code >}}

If you have {{< abbr "MFA" "Multi-factor authentication" >}} enabled for your
account however, it becomes slightly more complicated. You either have to:
- Supply the {{< abbr "TOTP" "Time-based One-Time Password" >}} token via
    the `x-auth-token` header each time you make a request
- Or you can generate a
    session API key which you can reuse for future requests without having to
    provide the {{< abbr "TOTP" "Time-based One-Time Password" >}} token.

I went with the latter.

You can generate a session API key for
your user via the `/login`[^2] endpoint and then use the returned API key
instead of the password in the request above:

{{< code language="bash" title="Generate session API key for user" collapse="—" expand="+" >}}
curl -X POST "https://box.example.com/admin/login" \
            -u "user@example.com:str0ngP4ssw0rd!"
{{< /code >}}

Which returns a JSON response like this:

{{< code language="json" title="Returned response" collapse="—" expand="+" >}}
{
  "api_key": "...",
  "email": "user@example.com",
  "privileges": [
    "admin"
  ],
  "status": "ok"
}
{{< /code >}}

Now we can make a request using the returned API key:
{{< code language="bash" title="Create alias request using the API key" collapse="—" expand="+" >}}
curl -X POST "https://box.example.com/admin/mail/aliasses/add" \
            -d "address=alias@example.com" \
            -d "forwards_to=address@example.com" \
            -u "user@example.com:api_key_we_generated_earlier"
{{< /code >}}

Okay this is great and all, but I don't want to do this manually and renew the
session API key in case it's expired. I don't want to think about it, I just
want to execute a script, give it the alias I want created and be done. Let's
do that!

## Automate using a Bash script

Here are the things I want the Bash script to do for me:

1. Support users that have {{< abbr "MFA" "Multi-factor authentication" >}} 
enabled
2. Generate an API key if one doesn't exist already
3. Check the validy of the API key if one has previously been generated
    1. Renew the key in case it's expired
4. Either add or delete an alias

I use a password manager ({{< a "https://github.com/gopasspw/gopass" "gopass"
>}}) to store passwords, usernames, email addresses for all my accounts. And I
use {{<a "https://github.com/evansmurithi/cloak" "cloak">}} as my authenticator
application to generate {{< abbr "TOTP" "Time-based One-Time Password" >}}
tokens.{{< br >}} I want the script to use these to get the user's password and
generate the {{< abbr "TOTP" "Time-based One-Time Password" >}} to generate the
API key.

### The script

The script uses a configuration file (`~/.config/mailinabox_alias.conf`) to
make things easy to customize. When you first run the script it will
create an example configuration file for you in:
`~/.config/mailinabox_alias.conf.example`. {{< br >}} For convenience, I just put the
script in my `~/.local/bin` folder and renamed it to `malias`.{{< br >}} It has
two commands: `add` and `del`.

{{< code language="bash" title="Script example" collapse="—" expand="+" >}}
malias add my-fancy-alias@example.com     # Create alias
malias del my-fancy-alias@example.com     # Deletes alias
{{< /code >}}

You can find the (up-to date) {{< a "https://github.com/d3vr/scripts/blob/master/mailinabox-alias.sh" "finished script" >}} in my {{< a "https://github.com/d3vr/scripts" "scripts repo" >}}. Its content is reproduced here if you don't want to get it from Github:

{{< code language="bash" title="Mail-in-a-Box Alias API Bash script" collapse="—" expand="+" isCollapsed="true" >}}
#!/bin/bash

# Adds/Deletes an email alias to/from a Mail-in-a-Box instance
# Dependencies: curl
# Optional dependencies: cloak, gopass

CONF_PATH="$HOME/.config/mailinabox_alias.conf"

# If no argument is provided, show the help screen
if [[ $# -ne 2 ]]; then
  echo "Mail-in-a-Box Aliases API Wrapper"
  echo ""
  echo "Usage:"
  echo "malias <command> <alias>"
  echo ""
  echo "Commands:"
  echo "add        Create a new alias"
  echo "del        Delete an existing alias"
  echo ""
  echo "Config file:"
  echo "$CONF_PATH"
  exit
fi

# Check dependencies
if [[ -x curl ]]; then
  echo "curl seems to be missing, please install before using this script."
  exit 1
fi


# Check for existence of config file
if [ ! -s "$CONF_PATH" ]; then
  echo "Config file not found, please create the file at $CONF_PATH"
  echo "An example config file has been created for you at: $CONF_PATH.example"

  EXAMPLE_CONF_PATH=$CONF_PATH.example
  echo -n "" > $EXAMPLE_CONF_PATH
  echo "USE_OTP=false # If your you use 2FA with your account, enable this setting" > $EXAMPLE_CONF_PATH
  echo "OTP_CMD=\$(cloak view mailinabo) # Command to get 2FA token" >> $EXAMPLE_CONF_PATH
  echo 'USER_EMAIL="user@domain.com"' >> "$CONF_PATH.example"
  echo 'USER_PASSWORD="passw0rd!" # Or you can use a command to get the password from a password manager' >> $EXAMPLE_CONF_PATH
  echo '                          # e.g: USER_PASSWORD=$(gopass show -o mailinabox)' >> $EXAMPLE_CONF_PATH
  echo 'FORWARD_TO="forward@domain.com"' >> $EXAMPLE_CONF_PATH
  echo 'HOST="https://box.domain.com/admin"' >> $EXAMPLE_CONF_PATH
  echo 'API_KEY_FILE=/tmp/mbox_api_key' >> $EXAMPLE_CONF_PATH
  exit 1
else
. $CONF_PATH
fi

# Check config file validity
if [[ -z "$USE_OTP" ]]; then
  echo "Missing USE_OTP declaration in config file!"
  exit 1
fi
if [[ ! -z "$USE_OTP" ]]; then
  if [[ -z "$OTP_CMD" ]]; then
    echo "Missing OTP_CMD declaration in config file!"
    exit 1
  fi
fi
if [[ -z "$USER_EMAIL" ]]; then
  echo "Missing USER_EMAIL declaration in config file!"
  exit 1
fi
if [[ -z "$USER_PASSWORD" ]]; then
  echo "Missing USER_PASSWORD declaration in config file!"
  exit 1
fi
if [[ -z "$FORWARD_TO" ]]; then
  echo "Missing FORWARD_TO declaration in config file!"
  exit 1
fi
if [[ -z "$HOST" ]]; then
  echo "Missing HOST declaration in config file!"
  exit 1
fi
if [[ -z "$API_KEY_FILE" ]]; then
  API_KEY_FILE=/tmp/mbox_api_key
fi

COMMAND=$1
ALIAS=$2
STALE_API_KEY_ERROR="Incorrect email address or password."

# Generate new API key
get_api_key() {
  curl -s -X POST "$HOST/login" -H "x-auth-token: $OTP_CMD" -u "$USER_EMAIL:$USER_PASSWORD" | jq -r ".api_key"
}

# Renew API key when it's stale
renew_api_key_if_stale() {
  privilege_test=$(curl -s "$HOST/mail/users/privileges?email=$USER_EMAIL" -u "$USER_EMAIL:`stored_api_key`")
  if [[ "$privilege_test" == $STALE_API_KEY_ERROR ]]; then
    get_api_key > $API_KEY_FILE
  fi
}

# Get API key from tmp file
stored_api_key() {
  cat $API_KEY_FILE
}

add_alias() {
  curl -s -X POST "$HOST/mail/aliases/add" -d "address=$ALIAS" -d "forwards_to=$FORWARD_TO" -u "$USER_EMAIL:`stored_api_key`"
}

remove_alias() {
  curl -s -X POST "$HOST/mail/aliases/remove" -d "address=$ALIAS" -u "$USER_EMAIL:`stored_api_key`"
}

# Store API key in a tmp file and reuse it if it exists
if [ ! -s "$API_KEY_FILE" ]; then
  get_api_key > $API_KEY_FILE
fi

renew_api_key_if_stale

case $COMMAND in
  add)
    output=$(add_alias)
    if [[ add_alias != "alias added" ]]; then
      echo "Alias added successfully: $ALIAS"
    else
      echo "Adding alias failed!"
      exit 1
    fi
    ;;

  del)
    output=$(remove_alias)
    if [[ "$output" == "alias removed" ]]; then
      echo "Alias removed successfully"
    else
      echo "Removing alias failed: $output"
      exit 1
    fi
    ;;

  *)
    echo "Unknown command!"
    exit 1
    ;;
esac

{{< /code >}}

## That's all folks!

You've made it all way to here? You deserve a cookie: 🍪 !
{{< br >}}
Thank you for reading and I hope you've found this useful in some way!


The following resources were helpful in the making of this post and script:
- {{< a "https://mailinabox.email/api-docs.html"
"Mail-in-a-Box API docs" >}}
- {{< a "https://devhints.io/bash" "Bash Cheatsheet" >}}

{{< br >}}

[^1]: {{< a "https://mailinabox.email/api-docs.html#operation/upsertMailAlias" "`/mail/aliases/add` endpoint reference" >}}
[^2]: {{< a "https://mailinabox.email/api-docs.html#operation/login" "`/login` endpoint reference" >}}
