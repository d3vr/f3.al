---
title: "ChatGPT: The Latest and Greatest of Large Language Models from OpenAI [Examples and Resources]"
url: "/chatgpt-definitive-resource/"
date: 2022-12-11
draft: false
highlightCode: true
toc: true
categories: ["Artificial Intelligence"]
tags: ["nlp", "gpt", "openai"]
keywords: ["ChatGPT", "NLP", "Large Language Models", "AI", "Resources", "Examples"]
cover: "assets/covers/chatgpt-definitive-resource.webp"
coverAlt: "Robot and human looking at each other"
---

If you've been anywhere near Twitter or tech news for the past two weeks,
you've seen talk about {{< a "https://chat.openai.com/" "ChatGPT" >}} all over
the place. In case you haven't heard already, ChatGPT is the latest AI large
language model from OpenAI, {{< a "https://openai.com/blog/chatgpt/" 
"released November 30th, 2022" >}}. 
{{< br >}} In this post I'll show you (impressive) examples of how you can use
it and ways it can be useful for you. I'll also share some tips and tricks I've
learned by tinkering around with it as well as a list of resources if you wish
to learn more.

<!--more-->

{{< toc >}}

## Introduction
ChatGPT is known as what's called Language Models, which are AI models
specifically designed for Natural Language Processing applications such as:
- Machine translation
- Text comprehension
- Information retrieval
- Summarization
- Classification
- Text generation
- Answering questions 

Among other applications.

{{<br>}}

### Timeline
Language models have come a long way in the few past years, in fact the rate of
progress in AI research is so fast, you can barely even keep up. So To
contextualize ChatGPT and for a better idea of how we got here, here's a
(non-exhaustive) timeline of notable events relating to language models:

{{<image src="/assets/posts/chatgpt-definitive-resource/timeline.webp" alt="Robot schematics" lazy="true">}}

#### 2017
- **`June`** — A research team at Google {{<a
    "https://arxiv.org/abs/1706.03762" "publishes a paper" >}} {{< a
    "https://ai.googleblog.com/2017/08/transformer-novel-neural-network.html"
    "introducing Transformer" >}}, a novel neural network architecture.
#### 2018
- **`November`** — Google {{< a
    "https://ai.googleblog.com/2018/11/open-sourcing-bert-state-of-art-pre.html"
    "open-sources BERT" >}} ({{< a "https://arxiv.org/abs/1810.04805"
    "paper">}}), a pre-trained Natural Language Processing model.
- **`June`** — OpenAI {{< a
    "https://openai.com/blog/language-unsupervised/" "introduces GPT" >}} ({{<a
    "https://cdn.openai.com/research-covers/language-unsupervised/language_understanding_paper.pdf"
    "paper">}}).
#### 2019
- **`February`** — OpenAI {{<a
    "https://openai.com/blog/better-language-models/" "publishes GPT-2">}}
    ({{<a
    "https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf"
    "paper" >}}), an improvement on GPT capable of generating coherent
    paragraphs of text, it also achieves better performance on text
    comprehension tasks.
- **`October`** — Google starts using BERT to {{< a
    "https://blog.google/products/search/search-language-understanding-bert/"
    "improve the accuracy of search results" >}}.
#### 2020
- **`May`** — OpenAI publishes a {{<a "https://arxiv.org/abs/2005.14165"
    "paper introducing GPT-3" >}}, a much larger model than its predecessor
    GPT-2.
- **`June`** — OpenAI {{<a "https://openai.com/blog/openai-api/" "launches an API" >}}
    allowing third-parties to {{< a
    "https://openai.com/blog/gpt-3-apps/" "build applications" >}} on top of
    OpenAI's models such as GPT-3.
- **`September`** — OpenAI {{<a "https://arxiv.org/abs/2009.01325" "publishes a paper" >}}
    {{<a "https://openai.com/blog/learning-to-summarize-with-human-feedback/"
    "detailing their approach">}}  of using {{<abbr "RLHF" "Reinforcement Learning from Human Feedback" >}}
    to achieve better results for generating text summaries.
#### 2021
- **`June`** — OpenAI {{<a "https://cdn.openai.com/palms.pdf" "publishes a paper">}}
    showcasing their results for {{<a "https://openai.com/blog/improving-language-model-behavior/"
    "improving language model behavior by training on a curated dataset">}}.
    They've fine-tuned GPT-3 on a 120KB dataset which is about 0.000000211% of
    the original training data.
- **`August`** — OpenAI {{<a "https://openai.com/blog/openai-codex/"
    "launches Codex">}} ({{<a "https://arxiv.org/abs/2107.03374" "paper">}}),
    an AI system that translates natural language to code. It's the same model
    that powers {{<a "https://copilot.github.com/" "Github Copilot" >}}.
- **`September`** — OpenAI {{<a "https://arxiv.org/abs/2109.10862" "publishes a paper" >}}
    showcasing their technique of {{<a "https://openai.com/blog/summarizing-books/" 
    "fine-tuning a GPT-3 model to summarize entire books">}}. You can play with 
    the {{<a "https://openaipublic.blob.core.windows.net/recursive-book-summ/website/index.html#/"
    "demo they published">}}  for this model for a better idea of how it performs. 
- **`December`** — OpenAI {{<a "https://openai.com/blog/customized-gpt-3/"
    "adds the possibility to fine-tune a GPT-3 model">}} via 
    {{< a "https://beta.openai.com/docs/guides/fine-tuning" "their API">}} using
    your own data. The fine-tuned model is deployed on their API and you can
    use it to improve results and lower costs.
- **`December`** — OpenAI  {{<a "https://openai.com/blog/webgpt/"
    "demonstrates WebGPT">}} ({{<a "https://arxiv.org/abs/2112.09332"
    "paper">}}), a fine-tuned GPT-3 model with web access (via Bing's Web
    Search API). The goal is to answer open-ended questions using a text-based
    web browser while mimicing how a human researches questions online. It also
    cites the sources for the answers it makes.
#### 2022
- **`March`** — OpenAI {{<a "https://openai.com/blog/gpt-3-edit-insert/"
    "adds Editing & Insertion capabilities to GPT-3" >}}. 
- **`Jane`** — OpenAI {{<a "https://openai.com/blog/instruction-following/"
    "introduces InstructGPT" >}} ({{<a "https://arxiv.org/abs/2203.02155"
    "paper">}}), a fine-tuned GPT-3 model (using {{<abbr "RLHF" "Reinforcement Learning from Human Feedback" >}})
    to better follow instructions and achieve better alignment with users' intents.
- **`December`** — OpenAI {{<a "https://openai.com/blog/chatgpt/" "introduces ChatGPT" >}},
    a model trained to interact in a conversational way which works great as a
    chatbot. It has the capability to answer questions (and followup questions)
    while taking the context into consideration, it also admits its mistakes,
    challenges incorrect statements and refuses inappropriate requests. OpenAI
    {{<a "https://chat.openai.com/chat" "opened up access" >}} to try ChatGPT
    as a "Free Research Preview".

### Learn More {#background-learn-more}
#### Videos {#background-videos}
- {{<a "https://www.youtube.com/watch?v=aQguO9IeQWE" 
    "But How Does ChatGPT Actually Work?">}}: Explainer video from Till
    Musshoff

- {{<a "https://www.youtube.com/watch?v=StLtMcsbQes" 
    "Large Language Models and the Future of AI">}}: Excellent talk by 
    {{<a "https://twitter.com/npcollapse" "Connor Leahy">}} from 
    {{<a "https://www.eleuther.ai/" "EleutherAI">}}. It provides a good overview
    of large language models and their potential.

#### Articles {#background-articles}
- {{<a "https://medium.com/nlplanet/a-brief-timeline-of-nlp-from-bag-of-words-to-the-transformer-family-7caad8bbba56" 
    "A Brief Timeline of NLP from Bag of Words to the Transformer Family">}}: A
    more detailed timeline of {{< abbr "NLP" "Natural Language Processing" >}}
    developments.
- {{<a "https://towardsdatascience.com/bert-explained-state-of-the-art-language-model-for-nlp-f8b21a9b6270" 
    "BERT Explained: State of the art language model for NLP" >}}.
- {{<a "https://www.springboard.com/blog/data-science/machine-learning-gpt-3-open-ai/" 
    "OpenAI GPT-3: Everything You Need to Know">}}:  This provides a good
    overview of how GPT-3 is different and what are some of its possible
    applications.
- {{<a "https://dugas.ch/artificial_curiosity/GPT_architecture.html" 
    "The GPT-3 Architecture, on a Napkin">}}: GPT-3 architecture explained with
    lots of diagrams.

#### Discussions
- {{<a "https://news.ycombinator.com/item?id=33939805" 
    "HackerNews: How does ChatGPT work?">}}


{{<br>}}

---

{{<br>}}


## Examples
Now that we've got a good understanding of what ChatGPT is and a timeline that 
shows how we got here, let's have some fun playing around with ✨ ChatGPT ✨!

Before we proceed, please note I'll be copying the output I get from ChatGPT as
text here for better readability and accessiblity (instead of screenshotting
everything), I'll also share a link for each example on 
{{<a "https://sharegpt.com/" "ShareGPT">}}. Here's the convention used for the
following examples:

{{< diag >}}
{{< diag-item prompt="🤔 > " >}}The prompt I write, fully human-made text.{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}ChatGPT's output, machine-produced.{{< /diag-item >}}
{{< /diag >}}

I might also use `[...]` to truncate ChatGPT's output if it's not necessary to 
clarify a point. Output tends to get long.{{<br>}}
Other than that, I will copy ChatGPT's output as is, unmodified.


With that out of the way, let's see the examples!
{{<br>}}
{{<br>}}
{{<br>}}

### Programming and Code-Related Uses {#programming}
ChatGPT has shown impressive capabilities when it comes to generating code,
explaining code, writing documentation and providing help debugging.

{{<image src="/assets/posts/chatgpt-definitive-resource/programming-and-code.webp" alt="Man typing in front of 6 computer screens" lazy="true">}}

{{<br>}}
Jump to:
1. [Generate a Bash script](#bash-script)
2. [Explain code and fix possible errors](#explain-and-improve)

{{<br>}}

#### Example 1: Generate a Bash script {#bash-script}
{{<a "https://shareg.pt/a9Hws5s" "See it on ShareGPT">}}
{{<br>}}

{{< diag >}}
{{< diag-item prompt="🤔 > " >}}Make a bash script that takes a program name as an argument and checks if
there's a running process for it using pgrep
{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}To create a bash script that takes a program name as an argument and checks if
there's a running process for it using pgrep, you can use the following code:{{< /diag-item >}}
{{< code language="bash" noheader="true" >}}
#!/bin/bash

# Check if the user provided a program name as an argument
if [ $# -eq 0 ]; then
  # If not, print an error message and exit
  echo "Error: Please provide a program name as an argument."
  exit 1
fi

# Use pgrep to search for a running process with the given name
pgrep $1

# Check the exit code of the previous command
if [ $? -eq 0 ]; then
  # If the exit code is 0, that means a process was found, so print a message
  # indicating that the program is running
  echo "The program '$1' is currently running."
else
  # If the exit code is not 0, that means no process was found, so print a
  # message indicating that the program is not running
  echo "The program '$1' is not currently running."
fi
{{< /code >}}
{{< diag-item prompt="🤖 > " color="true" >}}Save the code to a file named `check_program.sh`, make the file executable by
running `chmod +x check_program.sh`, and then you can run the script by calling
`./check_program.sh` followed by the name of the program you want to check. For
example:
{{< /diag-item >}}
{{< code language="bash" noheader="true" >}}
./check_program.sh bash
{{< /code >}}
{{< diag-item prompt="🤖 > " color="true" >}}This will search for a running process with the name "bash" and print a message
indicating whether or not it is running.
{{< /diag-item >}}
{{< /diag >}}

{{<br>}}
Okay that's a great start, however when you run this, if the program is running 
it also outputs the process IDs for the program. I also want the script to exit 
with a non-zero status code, let's see if we can get it to update the script to 
match our needs.
{{<br>}}
{{<br>}}

{{< diag >}}
{{< diag-item prompt="🤔 > " >}}Thanks, can you also not show the process IDs if the program is running? And if
the program is not running, exit with a non-zero status code
{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}To modify the script to not show the process IDs when the program is running
and to exit with a non-zero status code when the program is not running, you
can use the following code:
{{< /diag-item >}}
{{< code language="bash" noheader="true" >}}
#!/bin/bash

# Check if the user provided a program name as an argument
if [ $# -eq 0 ]; then
  # If not, print an error message and exit
  echo "Error: Please provide a program name as an argument."
  exit 1
fi

# Use pgrep to search for a running process with the given name
pgrep $1 &> /dev/null

# Check the exit code of the previous command
if [ $? -eq 0 ]; then
  # If the exit code is 0, that means a process was found, so print a message
  # indicating that the program is running
  echo "The program '$1' is currently running."
else
  # If the exit code is not 0, that means no process was found, so print a
  # message indicating that the program is not running and exit with a non-zero
  # status code
  echo "The program '$1' is not currently running."
  exit 1
fi
{{< /code >}}
{{< diag-item prompt="🤖 > " color="true" >}}This updated script will not show the process IDs when the program is running,
and it will exit with a non-zero status code when the program is not running.
Save the code to a file named `check_program.sh`, make the file executable by
running `chmod +x check_program.sh`, and then you can run the script as before by
calling `./check_program.sh` followed by the name of the program you want to
check. For example:
{{< /diag-item >}}
{{< code language="bash" noheader="true" >}}
./check_program.sh bash
{{< /code >}}
{{< diag-item prompt="🤖 > " color="true" >}}This will search for a running process with the name "bash" and print a message
indicating whether or not it is running. If the program is not running, the
script will exit with a non-zero status code.
{{< /diag-item >}}
{{< /diag >}}

{{<br>}}
A little repetitive, but that sure gave us what we asked for!{{<br>}}
As you can see, with minimal effort you can quickly generate working scripts,
or at least get a very good starting point. I can see this being super helpful 
to avoid spending too much time on boilerplate code.
{{<br>}}
{{<br>}}

#### Example 2: Explain code and fix possible errors {#explain-and-improve}
{{<a "https://sharegpt.com/c/Wv5EHK6" "See it on ShareGPT">}}

I wanted to test its capabilities in explaining code and helping out with
identifying possible issues and adding error handling. So I first asked ChatGPT
to write a python script:

{{<br>}}

{{< diag >}}
{{< diag-item prompt="🤔 > " >}}Write a python script that fetches a popular quote form an API endpoint, it
then appends the quote to a file
{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}Here is a python script that fetches a popular quote from an API endpoint and
appends it to a file:
{{< /diag-item >}}

{{< code language="python" noheader="true" >}}
import requests

# API endpoint for fetching popular quotes
QUOTE_API_ENDPOINT = 'https://api.quotable.io/random'

# file to append the quote to
QUOTE_FILE = 'quotes.txt'

# fetch a quote from the API endpoint
response = requests.get(QUOTE_API_ENDPOINT)

# parse the response as JSON
quote = response.json()

# extract the quote text from the JSON object
quote_text = quote['content']

# append the quote to the file
with open(QUOTE_FILE, 'a') as f:
    f.write(quote_text)
    f.write('\n')

print(f'Successfully appended quote to {QUOTE_FILE}')
{{< /code >}}
{{< diag-item prompt="🤖 > " color="true" >}}This script uses the requests library to make an HTTP GET request to the API
endpoint, which returns a JSON object containing a quote. The script then
parses the JSON response and extracts the quote text, and appends it to a file.

Note that this script is just an example and may not work as-is, since it is
not connected to a real API endpoint. You will need to provide your own API
endpoint and modify the script accordingly.
{{< /diag-item >}}
{{< /diag >}}

{{<br>}}
I then copied the Python code, removed all the comments, started a new session,
pasted the code and asked ChatGPT to explain the code and add comments. 
{{<a "https://sharegpt.com/c/lbVUznN" "See it on ShareGPT">}}

{{<br>}}
{{< diag >}}
{{< diag-item prompt="🤔 > " >}}I don't understand what the following python script does, can you add comments
in the code and also explain what it's doing?
{{< /diag-item >}}
{{< code language="python" noheader="true" >}}
import requests

QUOTE_API_ENDPOINT = 'https://api.quotable.io/random'

QUOTE_FILE = 'quotes.txt'

response = requests.get(QUOTE_API_ENDPOINT)

quote = response.json()

quote_text = quote['content']

with open(QUOTE_FILE, 'a') as f:
    f.write(quote_text)
    f.write('\n')

print(f'Successfully appended quote to {QUOTE_FILE}')
{{< /code >}}
{{< diag-item prompt="🤖 > " color="true" >}}This script uses the `requests` library to make a GET request to the
`QUOTE_API_ENDPOINT` which is a URL for a quote API. This API returns a quote in
JSON format, which the script then parses to extract the quote text. The quote
text is then written to the `QUOTE_FILE`, which is specified as `'quotes.txt'`,
using the `with open` statement in Python. This will open the file in append
mode, meaning that the quote will be appended to the end of the file. Finally,
the script prints a message indicating that the quote was successfully appended
to the file.

Here is the script with added comments:
{{< /diag-item >}}
{{< code language="python" noheader="true">}}
import requests  # Import the requests library

QUOTE_API_ENDPOINT = 'https://api.quotable.io/random'  # URL for the quote API
QUOTE_FILE = 'quotes.txt'  # File to store the quotes

# Make a GET request to the quote API
response = requests.get(QUOTE_API_ENDPOINT)

# Parse the JSON response to extract the quote text
quote = response.json()
quote_text = quote['content']

# Append the quote text to the quotes file
with open(QUOTE_FILE, 'a') as f:
    f.write(quote_text)
    f.write('\n')

# Print a success message
print(f'Successfully appended quote to {QUOTE_FILE}')
{{< /code >}}
{{< /diag >}}

{{<br>}}

Yep, it perfectly explains what the script is doing.{{<br>}}
Now let's try and see if
it can help us identify possible issues with the code and maybe even implement
a fix for us?

{{<br>}}

{{< diag >}}
{{< diag-item prompt="🤔 > " >}}Can you find any possible bugs in this code ? 
{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}There are no obvious bugs in this code, but there are a few potential issues
that could arise. For example, if the `QUOTE_API_ENDPOINT` is not available or is
not responding, the `requests.get()` call will raise an exception, which will
cause the script to crash. Additionally, if the JSON response from the API does
not contain a `'content'` field, trying to access `quote['content']` will raise a
`KeyError`.

Here is a modified version of the script that includes error handling for these
cases:
{{< /diag-item >}}
{{< code language="python" noheader="true" >}}
import requests  # Import the requests library

QUOTE_API_ENDPOINT = 'https://api.quotable.io/random'  # URL for the quote API
QUOTE_FILE = 'quotes.txt'  # File to store the quotes

try:
    # Make a GET request to the quote API
    response = requests.get(QUOTE_API_ENDPOINT)

    # Parse the JSON response to extract the quote text
    quote = response.json()
    quote_text = quote['content']
except requests.exceptions.RequestException as e:
    # Handle any errors that occurred while making the request
    print(f'An error occurred while making the request: {e}')
except KeyError as e:
    # Handle cases where the JSON response does not have the expected format
    print(f'Invalid response from the API: {e}')
else:
    # Append the quote text to the quotes file
    with open(QUOTE_FILE, 'a') as f:
        f.write(quote_text)
        f.write('\n')

    # Print a success message
    print(f'Successfully appended quote to {QUOTE_FILE}')
{{< /code >}}
{{< /diag >}}

{{<br>}}

So it correctly identified troublesome code, implemented safeguards and added
descriptive error messages. Isn't that something!

{{<br>}}
{{<inline-newsletter>}}
{{<br>}}

### Writing / Marketing {#writing-marketing}
ChatGPT is capable of producing great results when it comes to writing / text generation related tasks!

{{<image src="/assets/posts/chatgpt-definitive-resource/writing.webp" 
alt="Typewriter on a desk next to a stack of books, a plant and a coffee mug" 
lazy="true">}}

{{<br>}}
Jump to:
1. [Generate a draft for a blog post](#blog-post-draft)
2. [Generate marketing copy](#marketing-copy)
3. [Writing prompts and inspiration](#writing-prompts)
4. [Emails](#emails)

{{<br>}}

#### Example 1: Generate a draft for a blog post {#blog-post-draft}

{{<a "https://shareg.pt/XAG3OpF" "See it on ShareGPT">}}
{{<br>}}

{{< diag >}}
{{< diag-item prompt="🤔 > " >}}Generate a draft for a blog post about AI large language models and their
use-cases, divide the draft into sections with headers and subheaders
{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}
Blog Post Draft:

Title: The Power of AI Large Language Models: Exploring their Use-Cases

Intro:

AI large language models, such as GPT-3 and BERT, have taken the world of
natural language processing (NLP) by storm. With the ability to understand and
generate human-like language, these models have the potential to revolutionize
a variety of industries and applications. In this blog post, we will explore
some of the most promising use-cases for AI large language models and discuss
how they can benefit businesses and individuals alike.

Section 1: Text Generation

One of the most exciting applications of AI large language models is their
ability to generate human-like text. This can be used in a variety of ways,
such as automatically generating content for websites or social media, or
creating personalized emails and responses. By using these models, businesses
can save time and resources on content creation, while still providing
high-quality, engaging material.

Subsection 1: Content Creation

One of the most common uses for text generation is the creation of content for
websites and social media. With AI large language models, businesses can
automatically generate articles, blog posts, and other written material, saving
time and resources on content creation. Additionally, these models can be
trained on a specific brand's tone and style, ensuring that the generated
content is consistent with the company's voice.

Subsection 2: Personalized Communications

Another promising use for text generation is the creation of personalized
emails and responses. AI large language models can be trained to understand a
person's individual preferences and needs, and then generate custom-tailored
responses that are engaging and relevant. This can be especially useful for
customer service, where the ability to quickly and accurately respond to
individual inquiries can improve the customer experience and build brand
loyalty.

Section 2: Sentiment Analysis

In addition to generating text, AI large language models can also be used to
analyze and understand human emotions and opinions. This is known as sentiment
analysis, and it can be incredibly useful for a variety of applications. For
example, businesses can use sentiment analysis to understand how their
customers feel about their products or services, and then use that information
to improve their offerings and increase customer satisfaction.

Subsection 1: Customer Feedback

One of the most common uses for sentiment analysis is the analysis of customer
feedback. By using AI large language models to analyze customer reviews and
comments, businesses can gain a better understanding of what their customers
like and dislike about their products or services. This can help them identify
areas for improvement and make changes that will increase customer
satisfaction.

Subsection 2: Social Media Monitoring

Another potential use for sentiment analysis is the monitoring of social media.
By using AI large language models to analyze social media posts and comments,
businesses can gain insight into how their brand is perceived by the public.
This can help them identify potential issues or concerns, and take steps to
address them before they become major problems.

Conclusion:

AI large language models have the potential to revolutionize a variety of
industries and applications. Whether it's generating high-quality content,
providing personalized communications, or analyzing sentiment, these models
have the power to benefit businesses and individuals alike. With their ability
to understand and generate human-like language, AI large language models are
poised to become an essential tool for anyone looking to improve their NLP
capabilities.
{{< /diag-item >}}
{{< /diag >}}

{{<br>}}

#### Example 2: Generate marketing copy {#marketing-copy}
{{<a "https://sharegpt.com/c/XBSRtek" "See it on ShareGPT">}}
{{<br>}}

{{< diag >}}
{{< diag-item prompt="🤔 > " >}}Write a short marketing copy for an app that generates profile pictures using
AI in any style you want
{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}Are you tired of using the same old profile picture on your social media
accounts? With our new app, you can generate unique and personalized profile
pictures using AI technology. Choose from a variety of styles to suit your mood
or personality, and let our advanced algorithms create a one-of-a-kind image
for you. Say goodbye to boring profile pictures and stand out from the crowd
with AI-generated images from our app. Try it now!
{{< /diag-item >}}
{{< diag-item prompt="🤔 > " >}}Give me 4 bullet points for why a user might consider using the app
{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}
- Generate unique and personalized profile pictures
- Choose from a variety of styles to suit your mood or personality
- Stand out from the crowd with AI-generated images
- Say goodbye to boring profile pictures
{{< /diag-item >}}
{{< diag-item prompt="🤔 > " >}}Give me some options for text that goes on the call-to-action button on the
landing page for this app
{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}
- "Generate my profile picture"
- "Try it now"
- "Get started"
- "Create my image"
- "Make my profile picture"
- "Pick my style"
{{< /diag-item >}}
{{< /diag >}}

{{<br>}}

#### Example 3: Writing prompts and inspiration {#writing-prompts}
{{<a "https://shareg.pt/XUwAxKu" "See it on ShareGPT">}}

Sounds like you won't be staring at a blank page for much longer.
{{<br>}}

{{< diag >}}
{{< diag-item prompt="🤔 > " >}}I want a few short writing prompts about a sci-fi story in a post-apocalyptic
setting
{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}
1. After a catastrophic event wipes out most of humanity, a small group of
   survivors must band together to navigate the dangerous new world and search
   for a way to rebuild society.

2. In a world where the air is toxic and resources are scarce, a young woman
   must journey across the ruins of a once-great city to find a mysterious
   device that could hold the key to their survival.

3. In the aftermath of a massive alien invasion, a small group of humans must
   fight to survive against the extraterrestrial threat and the treacherous
   landscape of a post-apocalyptic world.

4. In a future where technology has advanced beyond recognition, a group of
   rebels must use their unique abilities to overthrow an oppressive government
   and restore freedom to the people.

5. After a devastating war between rival factions, a lone survivor must
   navigate the treacherous landscape of a post-apocalyptic world and confront
   the demons of their past in order to find a way to start anew.
{{< /diag-item >}}
{{< /diag >}}

{{<br>}}

#### Example 4: Emails {#emails}

{{<a "https://sharegpt.com/c/0qx6V7u" "See it on ShareGPT">}}
{{<br>}}

{{< diag >}}
{{< diag-item prompt="🤔 > " >}}Write an email to my English Literature professor asking for help on an issue
I'm having with my thesis
{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}
Dear Professor,

I am writing to request your help with an issue I am having with my thesis. I
am having difficulty organizing my ideas and developing a clear argument. I was
wondering if you could offer some guidance or suggestions on how to improve my
thesis.

I would greatly appreciate any advice you have to offer. Thank you for your
time and consideration.

Sincerely, [Your Name]
{{< /diag-item >}}
{{< /diag >}}

{{<br>}}

### AI Art
Let's see if we can get ChatGPT to generate prompts that we can directly use to
generate AI Art using {{< a "https://midjourney.com/" "Midjourney" >}}.

{{<br>}}

{{< diag >}}
{{< diag-item prompt="🤔 > " >}}Describe an image that shows a futuristic utopian city in vivid detail under
one paragraph
{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}In the image, the futuristic city is bustling with activity as flying cars zip
through the air above gleaming skyscrapers. The buildings are sleek and modern,
with intricate architectural designs and vibrant, neon-lit windows. The streets
are clean and free of pollution, with trees and greenery lining the sidewalks.
People of all ages and backgrounds can be seen walking, talking, and going
about their business, giving the city a vibrant and diverse feel. In the
distance, a massive space elevator can be seen reaching up into the sky,
signaling the city's advanced technology and progress. Overall, the city exudes
a sense of prosperity, progress, and harmony.
{{< /diag-item >}}
{{< /diag >}}

{{<br>}}
I then used that output on Midjourney v4:
{{<br>}}

{{< diag >}}
{{< diag-item prompt="🤔 > " >}}/imagine futuristic city is bustling with activity as flying cars zip through
the air above gleaming skyscrapers. The buildings are sleek and modern, with
intricate architectural designs and vibrant, neon-lit windows. The streets are
clean and free of pollution, with trees and greenery lining the sidewalks.
People of all ages and backgrounds can be seen walking, talking, and going
about their business, giving the city a vibrant and diverse feel. In the
distance, a massive space elevator can be seen reaching up into the sky,
signaling the city's advanced technology and progress --v 4
{{< /diag-item >}}
{{< /diag >}}

{{<br>}}
And here are the stunning results (I ran it 4 times with the same prompt):
{{<br>}}

{{<image src="/assets/posts/chatgpt-definitive-resource/utopia.webp" lazy="true">}}
{{<image src="/assets/posts/chatgpt-definitive-resource/utopia2.webp" lazy="true">}}
{{<image src="/assets/posts/chatgpt-definitive-resource/utopia3.webp" lazy="true">}}
{{<image src="/assets/posts/chatgpt-definitive-resource/utopia4.webp" lazy="true">}}

{{<br>}}
### Recommendations
Wouldn't be great if you had a friend knowledgeable in many different fields
that you could ask for recommendations on anything? Well now you do, sort of.

{{<image src="/assets/posts/chatgpt-definitive-resource/magic-library.webp" alt="A magical portal in a library corridor" lazy="true">}}

{{<br>}}
Jump to:
1. [Books](#books)
2. [Musicians](#musicians)
3. [YouTube Channels](#youtube)
{{<br>}}
{{<br>}}

#### Example 1: Books {#books}

{{<a "https://shareg.pt/FtSYvfg" "See it on ShareGPT">}}
{{<br>}}

{{< diag >}}
{{< diag-item prompt="🤔 > " >}}What are some books like "The Pragmatic Programmer" ?
{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}Here are some books that are similar to "The Pragmatic Programmer":

- "Clean Code" by Robert C. Martin "Code Complete" by Steve McConnell "The Art
- of Readable Code" by Dustin Boswell and Trevor Foucher "Refactoring:
- Improving the Design of Existing Code" by Martin Fowler "The Clean Coder: A
- Code of Conduct for Professional Programmers" by Robert C. Martin

All of these books focus on best practices and techniques for writing
high-quality, maintainable code. They cover a range of topics, including
design, testing, debugging, and refactoring.
{{< /diag-item >}}
{{< diag-item prompt="🤔 > " >}}Give more titles
{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}Here are some additional titles that might be of interest:

- "The Mythical Man-Month" by Frederick P. Brooks Jr.
- "Design Patterns: Elements of Reusable Object-Oriented Software" by Erich
- Gamma, Richard Helm, Ralph Johnson, and John Vlissides
- "Working Effectively with Legacy Code" by Michael Feathers
- "Agile Software Development, Principles, Patterns, and Practices" by Robert
    C. Martin
- "Don't Make Me Think: A Common Sense Approach to Web Usability" by Steve Krug
- "How to Solve It: A New Aspect of Mathematical Method" by George Pólya
- "The Logic of Computer Science" by Kees Doets and Jan van Eijck
- "Structure and Interpretation of Computer Programs" by Harold Abelson and
    Gerald Jay Sussman
- "Introduction to the Theory of Computation" by Michael Sipser

These books cover a wide range of topics in computer science and software
engineering. Some focus on specific areas, such as design patterns or
usability, while others provide a broader overview of the field. All of them
offer valuable insights and advice for software developers.
{{< /diag-item >}}
{{< /diag >}}


{{<br>}}

#### Example 2: Musicians {#musicians}

{{<a "https://sharegpt.com/c/k8j7Jci" "See it on ShareGPT">}}
{{<br>}}

{{< diag >}}
{{< diag-item prompt="🤔 > " >}}What are some artists that make music similar in to Ludovico Einaudi ?
{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}Ludovico Einaudi is a contemporary classical composer and pianist, known for
his minimalist and evocative style. Some artists who make music similar to his
include Max Richter, Olafur Arnalds, and Nils Frahm. All of these musicians are
known for creating beautiful and emotive music that often incorporates elements
of classical, ambient, and electronic music.
{{< /diag-item >}}
{{< /diag >}}


{{<br>}}

#### Example 3: YouTube Channels {#youtube}

{{<a "https://sharegpt.com/c/vb16cEj" "See it on ShareGPT">}}
{{<br>}}

{{< diag >}}
{{< diag-item prompt="🤔 > " >}}Give me YouTube channels that do engineering projects, similar to "Stuff Made
Here" and "Wintergatan"
{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}There are many YouTube channels that feature engineering projects and
experiments. Some popular ones include "The King of Random," "Mark Rober," and
"Adam Savage's Tested." These channels feature a wide variety of engineering
projects, from simple DIY experiments to more complex builds and inventions. If
you're looking for something similar to "Stuff Made Here" and "Wintergatan," I
would recommend checking out these channels.
{{< /diag-item >}}
{{< diag-item prompt="🤔 > " >}}Do you have more?
{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}Yes, there are many other YouTube channels that feature engineering projects
and experiments. Some other popular ones include "Smarter Every Day," "The
Backyard Scientist," and "NightHawkInLight." These channels offer a unique
blend of science, engineering, and experimentation, and are sure to provide
plenty of inspiration for your own projects. I would also recommend checking
out "Practical Engineering," which features in-depth explanations of
engineering principles and how they are applied in real-world projects.
Additionally, "The Q" is a great channel for anyone interested in engineering
and technology, as it features a wide variety of projects and experiments that
showcase the latest advances in these fields.
{{< /diag-item >}}
{{< /diag >}}


{{<br>}}

### Language Learning
ChatGPT can also be a great tool for learning languages and enriching your
vocabulary.

{{<image src="/assets/posts/chatgpt-definitive-resource/language.webp" alt="A robot and a woman in front of the Eiffel tower" lazy="true">}}

{{<br>}}
Take a look at this example ({{<a "https://sharegpt.com/c/VXrlTau" "ShareGPT">}}):
{{<br>}}



{{< diag >}}
{{< diag-item prompt="🤔 > " >}}I'm trying to learn French, I have very basic understanding of the language. I
want to ask you questions in English and you reply in French using words a
beginner would understand, also provide the English translation just in case I
don't understand. Can you do that ? 
{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}Oui, je peux vous aider à apprendre le français. Je vais répondre à vos
questions en utilisant des mots simples que les débutants peuvent comprendre.
Si vous ne comprenez pas quelque chose, n'hésitez pas à me demander une
traduction en anglais. Voici quelques phrases de base en français pour vous
aider à démarrer :

- Bonjour ! Comment ça va ? (Hello! How are you?)
- Je m'appelle... (My name is...)
- Je viens des États-Unis. (I come from the United States.)
- Je suis ici pour apprendre le français. (I am here to learn French.)
- Je suis débutant en français. (I am a beginner in French.)
- Pouvez-vous parler plus lentement, s'il vous plaît ? (Can you speak more
    slowly, please?)

N'hésitez pas à me poser d'autres questions si vous avez besoin d'aide pour
apprendre le français. Je suis là pour vous aider !
{{< /diag-item >}}
{{< diag-item prompt="🤔 > " >}}How are you doing today?
{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}Je vais bien, merci. Comment allez-vous aujourd'hui ? (I'm doing well, thank
you. How are you today?)
{{< /diag-item >}}
{{< diag-item prompt="🤔 > " >}}Doing great, having fun learning a new language! What did you have for
breakfast ? 
{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}Je suis un programme informatique, je ne mange pas de petit déjeuner. Mais je
suis toujours là pour vous aider à apprendre le français ! (I'm a computer
program, I don't eat breakfast. But I'm always here to help you learn French!)
{{< /diag-item >}}
{{< diag-item prompt="🤔 > " >}}Tell me a short joke
{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}Voici une blague courte en français : Pourquoi est-ce qu'un pneu est triste ?
Parce qu'il est dégonflé ! (Here is a short joke in French: Why is a tire sad?
Because it's deflated!)

La traduction en anglais : Why is a tire sad? Because it's deflated!
{{< /diag-item >}}
{{< diag-item prompt="🤔 > " >}}Thanks, I gotta go, talk to you soon!
{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}De rien, c'était un plaisir de vous aider à apprendre le français. Au revoir !
(You're welcome, it was a pleasure to help you learn French. Goodbye!)
{{< /diag-item >}}
{{< /diag >}}

{{<br>}}

### Some Other Shenanigans {#miscellaneous}
ChatGPT is capable of so much more, and the examples shown here so far are
just scratching the surface of what it's capable of.{{<br>}}

{{<image src="/assets/posts/chatgpt-definitive-resource/galaxy.webp" alt="A group of planets and colorful dust clouds" lazy="true">}}

{{<br>}}
Jump to:
1. [Write songs](#write-songs)
2. [Explain like I'm 5](#ELI5)
2. [Summarize long text](#summarize)

{{<br>}}

#### Example 1: Write songs {#write-songs}
{{<a "https://sharegpt.com/c/J7SI68l" "See it on ShareGPT">}}
{{<br>}}

{{< diag >}}
{{< diag-item prompt="🤔 > " >}}Write a 1940s country song about the hardships of being a programmer
{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}
In a time before computers were widespread,
When coding was a new and daunting task,
We sat and stared at lines of code all day,
Trying to make the machine do our bidding,
But oh, the hardships we faced back then.

We battled bugs and glitches all night long,
Our fingers cramped from typing on the keys,
Our eyes strained from staring at the screen,
But still we pressed on, driven by our dreams,
To make the machine bend to our will.

But oh, the hardships we faced back then,
With no Google to search for our answers,
No Stack Overflow to guide our way,
We had to figure it out on our own,
And oh, the hardships we faced back then.

But still we persevered, day after day,
Until at last our code was running smooth,
And though the hardships may have weighed us down,
We never let them keep us from our goals,
And oh, the pride we felt back then.

So here's a toast to all the programmers,
Who've faced the hardships and come out on top,
We may have struggled, but we never gave up,
And though the road was rough, we made it through,
And oh, the hardships we faced back then.
{{< /diag-item >}}
{{< /diag >}}

{{<br>}}

#### Example 2: Explain like I'm 5 {#ELI5}
{{<a "https://sharegpt.com/c/UgHDTq0" "See it on ShareGPT">}}
{{<br>}}

{{< diag >}}
{{< diag-item prompt="🤔 > " >}}Explain to me like I'm 5 years old how robots are made
{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}Sure, I'd be happy to explain how robots are made! Here's a simple explanation:
robots are made by people called engineers using a lot of different parts. The
parts might include things like metal or plastic for the body, motors to make
the robot move, sensors to help the robot see or hear, and a computer brain to
help the robot make decisions. The engineers put all of these parts together to
make a robot that can do different tasks. For example, a robot might be able to
pick up and move objects, or it might be able to talk to people. It's kind of
like building a toy, but with a lot more advanced parts!
{{< /diag-item >}}
{{< /diag >}}

{{<br>}}

#### Example 3: Summarize long text {#summarize}
I asked ChatGPT to summarize one part of Vannevar Bush's essay 
"{{<a "https://www.theatlantic.com/magazine/archive/1945/07/as-we-may-think/303881/" "As We May Think">}}}". 
{{<a "https://sharegpt.com/c/PhlBT6U" "See it on ShareGPT">}}

{{<br>}}

{{< diag >}}
{{< diag-item prompt="🤔 > " >}}Please give me a summary of the following text:
"Of what lasting benefit has been man's use of science and of the new
instruments which his research brought into existence? First, they have
increased his control of his material environment. They have improved his food,
his clothing, his shelter; they have increased his security and released him
partly from the bondage of bare existence. They have given him increased
knowledge of his own biological processes so that he has had a progressive
freedom from disease and an increased span of life. They are illuminating the
interactions of his physiological and psychological functions, giving the
promise of an improved mental health.

Science has provided the swiftest communication between individuals; it has
provided a record of ideas and has enabled man to manipulate and to make
extracts from that record so that knowledge evolves and endures throughout the
life of a race rather than that of an individual.

There is a growing mountain of research. But there is increased evidence that
we are being bogged down today as specialization extends. The investigator is
staggered by the findings and conclusions of thousands of other
workers—conclusions which he cannot find time to grasp, much less to remember,
as they appear. Yet specialization becomes increasingly necessary for progress,
and the effort to bridge between disciplines is correspondingly superficial."
{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}The use of science and new technology has improved human life by increasing
control over the environment, improving health and longevity, facilitating
communication, and providing a way to record and build upon knowledge. However,
the increasing specialization of research is creating a barrier to further
progress.
{{< /diag-item >}}
{{< /diag >}}

{{<br>}}


### Seen in the Wild {#misc-examples}
Examples I've seen on Twitter and elsewhere:

#### Videos
- {{<a "https://www.youtube.com/watch?v=k50Y0b3g5WY" 
    "What if OpenAI did Blender scripts?">}}: Generate Blender Python scripts.

#### Articles
- {{<a "https://medium.com/@ovd.iliescu/chatgpt-and-the-future-of-software-engineering-8dda95493db3" 
    "ChatGPT and the future of software engineering">}}: Using ChatGPT to 
    define a new programming language and instruct it to write programs in 
    that language. Also shows examples of just telling ChatGPT to come up with 
    its own language.
- {{<a "https://notesbylex.com/disputing-a-parking-fine-with-chatgpt.html"
    "Disputing A Parking Fine with ChatGPT">}}
- {{<a "https://www.lesswrong.com/posts/RYcoJdvmoBbi5Nax7/jailbreaking-chatgpt-on-release-day" 
    "Jailbreaking ChatGPT on Release Day">}}
- {{<a "https://www.engraved.blog/building-a-virtual-machine-inside/" 
    "Building A Virtual Machine inside ChatGPT">}}: Jonas Degrave shows how 
    ChatGPT can simulate a linux shell and even create a virtual machine!
- {{<a "https://codewithandrea.com/articles/dart-flutter-chatgpt/" 
    "Dart & Flutter with ChatGPT: Is it worth it?">}}: Using ChatGPT to
    generate Dart & Flutter code.

#### Twitter
- {{<a "https://twitter.com/zswitten/status/1598380220943593472" 
"Twitter Thread of known ChatGPT jailbreaks">}}: Some ways people have
successfully bypassed ChatGPT's filters.
- {{<a "https://twitter.com/SergeyI49013776/status/1598430479878856737" 
"Examples showing Where ChatGPT fails">}}
- {{<a "https://twitter.com/zswitten/status/1598855548581339138" 
    "Parse search result">}}: Extract information from a search result
- {{<a "https://twitter.com/hashtag/ChatGPT" "#ChatGPT Twitter hashtag">}}: You
    can find plenty of examples on Twitter. 

{{<br>}}
{{<inline-newsletter>}}
{{<br>}}

## Tips & Tricks {#tips-tricks}

Okay, now that you've seen plenty of examples that show the potential of 
ChatGPT, let's have a look at some tips and tricks that'll help you get the 
output you want.

{{<image src="/assets/posts/chatgpt-definitive-resource/magic-wand.webp" alt="Magic wand with a big star at the end" lazy="true">}}

{{<br>}}

### Output cutoff
The output produced by ChatGPT sometimes cuts off when it's too long, here you
can try saying: `continue output` or `continue where you left off` and it will
usually finish writing where it stopped.

### Getting better answers
If you don't get the result you expected, you can either press the `Try again
button` or send a new prompt to guide it into giving you the result you want.

### Get more details
When ChatGPT returns a list and you want more detail on one or more items, you can
always ask it to elaborate.

**Example:**
{{< diag >}}
{{< diag-item prompt="🤔 > " >}}Give me a list of short helpful tips to improve my writing style{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}
1. Start by using simple, clear, and concise language. [...]

3. Use specific, concrete examples and evidence to support your points. This
   will help your writing be more persuasive and convincing. [...]
7. Don't be afraid to revise and edit your work. Writing is often a process of
   trial and error, and it's important to take the time to refine and improve
   your writing. [...]
10. Finally, remember that practice makes perfect. [...]
{{< /diag-item >}}
{{< diag-item prompt="🤔 > " >}}Elaborate on 3 and 7{{< /diag-item >}}
{{< diag-item prompt="🤖 > " color="true" >}}
1. Using specific, concrete examples and evidence to support your points is an
   important part of effective writing. This helps to make your writing more
   persuasive and convincing, as it shows that you have thought carefully about
   your argument and [...].

2. Revising and editing your work is an important part of the writing process.
   Writing is often a process of trial and error, and it's important to take
   the time to [...].{{< /diag-item >}}
{{< /diag >}}

{{<br>}}

## Limitations
While the examples I've shown here are very impressive, it is important to 
keep in mind that ChatGPT does have some limitations:
- It can produce answers that sound plausible but are in fact incorrect,
    misleading or nonsensical. [^1]
- It might fail at seemingly simple logical questions, since it currently 
    doesn't have access to any source of truth. [^2]
- Answers are not always consistent. You can prompt it for something and it
    claims it doesn't know the answer, but if you try rephrasing your prompt
    you might get a correct answer.
- It can be verbose and repetitive, for example it will often remind you that
    it's a large language model trained by OpenAI:

{{< diag >}}
{{< diag-item prompt="🤖 > " color="true" >}}I am a large language model trained by OpenAI, so I have a lot of general
    knowledge, but [...]{{< /diag-item >}}
{{< /diag >}}

- While OpenAI has filters in place that limits the model's output, you might 
    still be able to get it to respond to "inappropriate requests" with the
    right prompt, or it might produce insensitive, unsafe or harmful content.
- You don't necessarily get the same answers if you use the same prompts.

{{<br>}}

## Tools / Resources {#tools-resources}
### Communities
- {{<a "https://www.reddit.com/r/ChatGPT/" "/r/chatGPT">}}: ChatGPT's subreddit.

### Prompts / Repositories
- {{<a "https://www.learngpt.com/" "LearnGPT">}}: Lists examples of prompts and
    their output
- {{<a "https://github.com/f/awesome-chatgpt-prompts" 
    "awesome-chatgpt-prompts">}}: Github repo containing curated list of prompts
- {{<a "https://github.com/humanloop/awesome-chatgpt" 
    "humanloop/awesome-chatgpt">}}: Links to helpful ChatGPT resources.

### Browser extensions
- {{<a "https://sharegpt.com/" "ShareGPT">}}: Browser extension to share
    ChatGPT threads (instead of having to rely on screenshots).
    - {{<a "https://github.com/domeccleston/sharegpt" "Source code">}}
    - {{<a "https://twitter.com/steventey/status/1599816553490366464" "Announcement">}}
- {{<a "https://github.com/wong2/chat-gpt-google-extension" 
    "Display ChatGPT results alongside Google results">}}: Browser extension to
    show ChatGPT output alongside Google search result pages.

### Bots
- {{<a "https://github.com/altryne/chatGPT-telegram-bot/" "Telegram Bot">}}
  - {{<a "https://twitter.com/altryne/status/1598822052760195072" "Announcement">}}
- {{<a "https://github.com/transitive-bullshit/chatgpt-twitter-bot" "Twitter bot">}}

### Scripts / Wrappers
- {{<a "https://github.com/acheong08/ChatGPT" "acheong08/ChatGPT">}}: Python
    wrapper for the ChatGPT API

{{<br>}}

## Impact & Reception {#impact-reception}
The response from ChatGPT's release varies from complete bewilderment to
skepticism or outright calling for OpenAI to shut down the public access [^3].

{{<image src="/assets/posts/chatgpt-definitive-resource/asteroid-impact.webp" 
alt="Asteroid impact in the middle of a snowy forest" lazy="true">}}

{{<br>}}
### Response
- {{<a "https://meta.stackoverflow.com/questions/421831/temporary-policy-chatgpt-is-banned" "StackOverflow introduces a new policy banning the influx of ChatGPT-generated answers">}} because of concerns about their quality and accuracy. ({{<a "https://stackoverflow.com/help/gpt-policy" "Explanation">}})
- {{<a "https://news.ycombinator.com/item?id=33945628" "HackerNews discussion on banning ChatGPT-generated content" >}}

{{<br>}}

### Press
- Wired: {{<a "https://www.wired.com/story/large-language-models-critique/" 
    "ChatGPT, Galactica, and the Progress Trap">}}
- The Verge: {{<a "https://www.theverge.com/2022/12/8/23499728/ai-capability-accessibility-chatgpt-stable-diffusion-commercialization" 
    "ChatGPT proves AI is finally mainstream — and things are only going to get weirder">}}
- Mashable: {{<a "https://mashable.com/article/chatgpt-amazing-wrong" 
    "The ChatGPT chatbot from OpenAI is amazing, creative, and totally wrong">}}
- TechCrunch: {{<a "https://techcrunch.com/2022/12/09/is-chatgpt-a-virus-that-has-been-released-into-the-wild/" 
    "Is ChatGPT a ‘virus that has been released into the wild’?">}}

{{<br>}}
### Videos
- Yannic Kilcher: {{<a "https://www.youtube.com/watch?v=0A8ljAkdFtg" 
    "ChatGPT: This AI has a JAILBREAK?! (Unbelievable AI Progress)">}}
- MKBHD: {{<a "https://www.youtube.com/watch?v=0gNauGdOkro" 
    "The Truth About AI Getting \"Creative\"">}}

{{<br>}}

## Conclusion
I think we've seen enough in this post to say AI has come a long way and is
proving to be very useful in various domains. {{<br>}} Will this (and
subsequent iterations of this technology) change the way we work forever? I
don't know, I think the long-term effects of this technology will become
apparent as more time goes by.

I would love to hear what you think of ChatGPT? Do you think this would be
useful for your work or other areas of your life? Let me know in the comments
below!

{{< br >}}
{{< br >}}

---

## Changelog
My aim for this post is to be a definitive resource for ChatGPT and have a list
of tools and resources that relate to it. I'll try to keep it up to date as
much as I can. If you think something should be in this post, please let me
know (either in the comments here or {{< a "https://twitter.com/imd3vr" 
"on Twitter">}}) and I'll try to add it in.

In this section I'll state the changes made to
the post and the date they were made.

### `12/13/22`
- Updated [Learn More](#background-learn-more) and [Seen in the Wild](#misc-examples)
    sections.

### `12/12/22`
- Updated [Learn More](#background-learn-more), [Impact &
    Reception](#impact-reception) and [Tools / Resources](#tools-resources)
    sections.

### `12/11/22`
- Initial publication

{{<br>}}
{{<br>}}

---
{{<br>}}

Get notified when I publish new posts:
{{<newsletter>}}
{{<br>}}


[^1]: {{<a "https://twitter.com/paniterka_ch/status/1599893718214901760" "Plausible-sounding answers">}}
[^2]: {{<a "https://twitter.com/SergeyI49013776/status/1598430479878856737" "Examples showing Where ChatGPT fails">}}
[^3]: {{<a "https://twitter.com/pkedrosky/status/1600889992103895041" "Paul Kedrosky raises concerns about ChatGPT">}}
