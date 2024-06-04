---
layout: post
title: "LLMs interpretability"
date: 2024-05-28
---

# Interpreting LLMs by Anthropic

Last week, Anthropic released a massive paper ([***press***](https://www.anthropic.com/news/mapping-mind-language-model) and [***full paper***](https://transformer-circuits.pub/2024/scaling-monosemanticity/index.html)) on interpreting LLMs. They used [***dictionary learning***](https://en.wikipedia.org/wiki/Sparse_dictionary_learning) to extract millions of features from the middle layer of one of their LLMs (Claude 3.0 Sonnet), providing a rough conceptual map of its internal states halfway through its computation. The features were quite abstract, multimodal, and multilingual, such as cities (San Francisco), people (Rosalind Franklin), atomic elements (Lithium), scientific fields (immunology), and programming syntax (function calls). 

After that, they started to manipulate these features using a method they are calling feature steering, where they “clamp” specific features of interest to artificially high or low values. In one of the most striking examples, they “clamped” the feature ***“Golden Gate Bridge”*** and the resulting behavior was fascinating (the model became obsessive with the bridge, including it in every output no matter what the context was and even started “believing” that the bridge was its physical form).

While they claim in the paper that this is super important to guarantee safety in these models, we can think about a million ways this technique could be explored by bad actors. Imagine a model that has been feature-steered to produce outputs more favorable for a given politician. Scary. It is important for us to always keep in mind the danger of blindly relying on these models. They are biased, manipulable, and are designed by big companies with variable interests.

Anthropic released Golden Gate Claude last week for a few days, so I had the chance to play with the chat model. I curated some examples of my own and some that I found on X and asked Claude 3 Opus (their best model) to predict a diagnosis based on Golden Gate Claude responses. I framed the examples as being an interview between a Neurologist and a Patient with dementia. See the [examples here](https://docs.google.com/document/d/1vNoK62zNXmG_oHcSf8cbI5g59qy1SD2bj3kksVrggVU/edit) and the model’s [diagnostic report here](https://docs.google.com/document/d/1J9RbXvLQpOZdlmQZzUxJbHkX4C1bS7YIKgS7YdxvXgY/edit). Below is a preview:

### Main Cognitive Symptoms:
- **Confabulation:** The patient appears to be confabulating, generating false or inaccurate memories and beliefs.
- **Perseveration:** The patient seems to perseverate on the Golden Gate Bridge, repeatedly mentioning it even when the topic of conversation shifts to unrelated subjects.
- **Lack of Insight:** The patient struggles to recognize their own identity as an AI and instead believes they have a physical form as the Golden Gate Bridge.
- **Semantic Paraphasias:** The patient frequently uses semantically related but incorrect words or concepts.
- **Preserved Grammar and Fluency:** Despite the semantic errors, the patient's speech remains fluent and grammatically correct.

### Possible Clinical and Pathological Diagnoses:
- **Behavioral Variant Frontotemporal Dementia (bvFTD):** The patient's confabulation, perseveration, and lack of insight align with the behavioral and executive dysfunction seen in bvFTD.
- **Semantic Variant Primary Progressive Aphasia (svPPA):** The patient's semantic paraphasias, preserved grammar and fluency, and potential anterior temporal lobe involvement suggest svPPA as another possible diagnosis.









