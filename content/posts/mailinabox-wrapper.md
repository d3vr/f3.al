---
title: "Mail-in-a-Box Aliases API bash script wrapper"
date: 2022-11-21T18:19:14+01:00
draft: true
---

I use a self-hosted instance of Mail-in-a-box for most of my email needs, and 
one recurrent task that I find myself doing manually each time is creating new
aliases for new accounts I create.

Doing this through the [Mail-in-a-Box API](https://mailinabox.email/api-docs.html) is pretty straightforward, you just send
a POST request to the `admin/mail/aliases/add` [(docs)](https://mailinabox.email/api-docs.html#operation/upsertMailAlias) endpoint with `address=alias@domain.com` and `forwards_to=address@domain.com` in the body.




