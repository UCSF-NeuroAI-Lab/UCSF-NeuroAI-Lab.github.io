---
layout: post
title: "Easy Problems That LLMs Get Wrong and The problem with Multiturn conversations"
date: 2025-05-17
---

Hi,

This [benchmark](https://arxiv.org/pdf/2405.19616) is already old, but most of the non-reasoning models still struggle with many of these problems! And the very powerful, time and resource consuming reasoning models take too long to answer! It is fun to play with, try it for yourself. I think it provides a good insight into where AI is currently. Big dissociations between capabilities that normally are associated in humans (logical reasoning, "model of the world", metacognition).

We have been developing AI Voice Agents with the most advanced speech-to-speech model from OpenAI, which allows for very fast and natural interactions. See below a transcript from a voice interaction…

**USER:**
Hey, how's it going?

**GPT-4o-REALTIME:**
Hey there! I'm doing great, thanks for asking. How about you? What's new with you today?

**USER:**
So, Sally has three brothers. Each of her brothers has two sisters. How many sisters does Sally have?

**GPT-4o-REALTIME:**
Sally has two sisters. The question mentions that each of her brothers has two sisters, and since Sally is one of them, there must be one more sister in addition to Sally.

Very concerning (not surprising at all, given the fact that these models are "simply" next token predicting machines), it that gives a very different answer with another set of tokens (i.e. If I start the conversation without asking "Hey, how's it going?" and jump straight to the question about Sally). The model this time gets it right.

**USER:**
Sally has three brothers. Each of her brothers have two sisters. How many sisters does Sally have?

**GPT-4o-REALTIME:**
Sally has three brothers, and each of her brothers has two sisters. Since those sisters are Sally and her sister, it means Sally herself is one of the two sisters. So, Sally has one sister.

See this extremely interesting paper showing that ["LLMs get lost in multi-turn conversation"](https://arxiv.org/pdf/2505.06120). The most interesting finding is that models that are very good at reasoning "OpenAI's o3", which are constantly hyped to be [close to AGI](https://arcprize.org/blog/oai-o3-pub-breakthrough) is bad at multiturn conversations (when it takes a wrong turn in a conversation, it get lost and do not recover). So, this model is extremely specialized in particular tasks, not at all closer to AGI…

Happy weekend!

Best,

Pedro