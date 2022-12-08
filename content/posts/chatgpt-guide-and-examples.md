---
title: "ChatGPT: The Latest and Greatest of Large Language Models from OpenAI [Examples and Resources]"
url: "/chatgpt-definitive-resource/"
date: "2022-12-08"
showLastUpdated: false
highlightCode: true
toc: true
categories: ["Artificial Intelligence"]
tags: ["nlp", "gpt", "openai"]
---

If you've been anywhere near Twitter or tech news for the past 7 days, you've
seen talk about {{< a "https://chat.openai.com/" "ChatGPT" >}} all over the
place. In case you haven't heard already, ChatGPT is the latest AI large language
model from OpenAI, {{< a "https://openai.com/blog/chatgpt/" "released November 30th, 2022" >}}.
{{< br >}} In this post I'll show you (impressive) examples of
how you can use it and ways it can be useful for you. I'll also share some tips
and tricks I've learned by tinkering around with it as well as a list of resources if you wish to learn more.

<!--more-->

{{< toc >}}

## Introduction
Language Models are AI models specifically designed for Natural Language
Processing applications such as:
- Machine translation
- Text comprehension
- Information retrieval
- Summarization
- Classification
- Text generation
- Answering questions 

Among other applications.

### Timeline
Language models have come a long way in the few past years, in fact the rate of
progress in AI research is so fast, you can barely even keep up. So To
contextualize ChatGPT and for a better idea of how we got here, here's a
(non-exhaustive) timeline of notable events relating to language models:

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

### Learn More
#### Articles
- {{<a "https://medium.com/nlplanet/a-brief-timeline-of-nlp-from-bag-of-words-to-the-transformer-family-7caad8bbba56" "A Brief Timeline of NLP from Bag of Words to the Transformer Family">}}: A more detailed timeline of {{< abbr "NLP" "Natural Language Processing" >}} developments.
- {{<a "https://towardsdatascience.com/bert-explained-state-of-the-art-language-model-for-nlp-f8b21a9b6270" "BERT Explained: State of the art language model for NLP" >}}.
- {{<a "https://www.springboard.com/blog/data-science/machine-learning-gpt-3-open-ai/" "OpenAI GPT-3: Everything You Need to Know">}}:  This provides a good overview of how GPT-3 is different and what are some of its possible applications.

## Examples

### Code

### Writing

### AI Art
### Language Learning
- [Mek Chinese](https://twitter.com/mekarpeles/status/1599485358022225921)
### RPG / D&D


## Limitations
While the examples I've shown here are very impressive, it is important to 
keep in mind that ChatGPT does have some limitations:
- It can produce answers that sound plausible but are in fact incorrect,
    misleading or nonsensical.
- It might fail at seemingly simple logical questions, since it currently 
    doesn't have access to any source of truth.
- Answers are not always consistent. You can prompt it for something and it
    claims it doesn't know the answer, but if you try rephrasing your prompt
    you might get a correct answer.
- It can be verbose and repetitive, for example it will often remind you that
    it's a large language model trained by OpenAI:
    ```
    I am a large language model trained by OpenAI, so I have a lot of general
    knowledge, but [...]
    ```
- While OpenAI has filters in place that limits the model's output, you might 
    still be able to get it to respond to "inappropriate requests" with the
    right prompt, or it might produce insensitive, unsafe or harmful content.

## Tips & Tricks

## Tools & Resources
### Tools
- [ShareGPT](https://twitter.com/steventey/status/1599816553490366464)
- [Telegram Bot](https://twitter.com/altryne/status/1598822052760195072)
    - [Source](https://github.com/altryne/chatGPT-telegram-bot/)
- [Access to Search?](https://twitter.com/zswitten/status/1598855548581339138)
### Articles

## Impact & Reception


## Conclusion
### Learn More
### Acknowledgements

---
I hope you've learned something new or found this post useful in some way!{{<
br >}} Now I'd like to hear from you, what do you think of ChatGPT, would you
find it useful in your work or life? Did I miss something? Let me know in the
comments below!

{{< br >}}
{{< br >}}

---

## Changelog
My aim for this post is to be a definitive resource for ChatGPT and have a list
of tools and resources that relate to it. I'll try to keep it up to date as
much as I can. If you think something should be in this post, please let me
know (either in the comments here or {{< a "https://twitter.com/imd3vr" "on Twitter">}}) and I'll try to add it in.

In this section I'll state the changes made to
the post and the date they were made.

#### 12.06.22
- Initial publication
