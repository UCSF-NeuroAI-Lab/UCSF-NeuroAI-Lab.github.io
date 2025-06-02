---
layout: post
title: "AI Copilot for Pathology, Prompting Techniques, Open Source collective power and some fun"
date: 2024-06-14
---

Hi MAC AI, happy Friday!
 
Find below some very interesting papers!

## A Multimodal Generative AI Copilot for Human Pathology
 
Lu, M.Y., Chen, B., Williamson, D.F.K. et al. (2024) A Multimodal Generative AI Copilot for Human Pathology. Nature.

[https://www.nature.com/articles/s41586-024-07618-3](https://www.nature.com/articles/s41586-024-07618-3)

The field of computational pathology[1,2] has witnessed remarkable progress in the development of both task-specific predictive models and task-agnostic self-supervised vision encoders[3,4]. However, despite the explosive growth of generative artificial intelligence (AI), there has been limited study on building general purpose, multimodal AI assistants and copilots[5] tailored to pathology. Here we present PathChat, a vision-language generalist AI assistant for human pathology. We build PathChat by adapting a foundational vision encoder for pathology, combining it with a pretrained large language model and finetuning the whole system on over 456,000 diverse visual language instructions consisting of 999,202 question-answer turns. We compare PathChat against several multimodal vision language AI assistants and GPT4V, which powers the commercially available multimodal general purpose AI assistant ChatGPT-4[7]. PathChat achieved state-of-the-art performance on multiple-choice diagnostic questions from cases of diverse tissue origins and disease models. Furthermore, using open-ended questions and human expert evaluation, we found that overall PathChat produced more accurate and pathologist-preferable responses to diverse queries related to pathology. As an interactive and general vision-language AI Copilot that can flexibly handle both visual and natural language inputs, PathChat can potentially find impactful applications in pathology education, research, and human-in-the-loop clinical decision making.

## The Prompt Report: A Systematic Survey of Prompting Techniques
 
Schulhoff et al. (2024) The Prompt Report: A Systematic Survey of Prompting Techniques. Arxiv.

[https://arxiv.org/abs/2406.06608](https://arxiv.org/abs/2406.06608)

Generative Artificial Intelligence (GenAI) systems are being increasingly deployed across all parts of industry and research settings. Developers and end users interact with these systems through the use of prompting or prompt engineering. While prompting is a widespread and highly researched concept, there exists conflicting terminology and a poor ontological understanding of what constitutes a prompt due to the area's nascency. This paper establishes a structured understanding of prompts, by assembling a taxonomy of prompting techniques and analyzing their use. We present a comprehensive vocabulary of 33 vocabulary terms, a taxonomy of 58 text-only prompting techniques, and 40 techniques for other modalities. We further present a meta-analysis of the entire literature on natural language prefix-prompting.

## Mixture-of-Agents Enhances Large Language Model Capabilities
 
Wang et al. (2024) Mixture-of-Agents Enhances Large Language Model Capabilities. Arxiv.

Recent advances in large language models (LLMs) demonstrate substantial capabilities in natural language understanding and generation tasks. With the growing number of LLMs, how to harness the collective expertise of multiple LLMs is an exciting open direction. Toward this goal, we propose a new approach that leverages the collective strengths of multiple LLMs through a Mixture-of-Agents (MoA) methodology. In our approach, we construct a layered MoA architecture wherein each layer comprises multiple LLM agents. Each agent takes all the outputs from agents in the previous layer as auxiliary information in generating its response. MoA models achieves state-of-art performance on AlpacaEval 2.0, MT-Bench and FLASK, surpassing GPT-4 Omni. For example, our MoA using only open-source LLMs is the leader of AlpacaEval 2.0 by a substantial gap, achieving a score of 65.1% compared to 57.5% by GPT-4 Omni.

Llama Index implementation: [https://github.com/run-llama/llama_index/blob/main/llama-index-packs/llama-index-packs-mixture-of-agents/README.md](https://github.com/run-llama/llama_index/blob/main/llama-index-packs/llama-index-packs-mixture-of-agents/README.md)

I'm happy to help you set this up if you want! It is indeed pretty awesome, totally free, private (runs locally if you want and have the computational resources) and open source!
 
## AND SOME FUN!

### AMAZING LLM visualization

[https://bbycroft.net/llm](https://bbycroft.net/llm)

### MS Paint Anything

An open source image generator for MS Paint themes!

[https://glif.app/@fab1an/glifs/clxa7m2f80004lkozza8ralld](https://glif.app/@fab1an/glifs/clxa7m2f80004lkozza8ralld)

### Dream Machine by Luma Labs AI

An open source text-to-video generator.

[https://lumalabs.ai/dream-machine](https://lumalabs.ai/dream-machine)