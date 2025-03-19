---
title: UCSF NeuroAI Lab
layout: default
---

## Health AI 
**Discovery, diagnosis, and care of neurodegenerative diseases.** We use a human-centered approach to design agentic systems that have advanced reasoning, and are scientifically grounded and interpretable. We comgine generative AI with traditional machine learning methods to leverage multimodal data, such as unstructured clinical notes, psychological and biological markers. [➔ **Research**](/research)

## Cognitive Neuroscience
**Human symbolic cognition**. We study the development and decline of symbolic systems like **mathematics** and written language, as well as self-referential reasoning. We combine electrophysiology, neuroimaging, psychophysics,  neuropsychology, and electrical stimulation to study the processing stages and representational codes underlying cognitive operations.[➔ **Research**](/research)

<!-- - ↻ **Insights from neuroscience** help us power our AI systems, which recursively help us better understand the brain ↺ -->


&nbsp;

The **NeuroAI Lab** operates at the [**UCSF Memory and Aging Center**](https://memory.ucsf.edu/){:target="_blank"}-[Department of Neurology](https://neurology.ucsf.edu/) - [**Weill Institude for Neuroscience**](https://weill.ucsf.edu/). We are also affiliated with the [**Bakar Computational Health Sciences Institute**](https://bakarinstitute.ucsf.edu/){:target="_blank"} and the [**Center for Intelligent Imaging (ci2)**](https://c2i2.ucsf.edu/){:target="_blank"}.




### Bits
<ul class="posts">
  {% for post in site.posts limit:3 %}
    <li><span>{{ post.date | date_to_string }}</span> » <a href="{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

