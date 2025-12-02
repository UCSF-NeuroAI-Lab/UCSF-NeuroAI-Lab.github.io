---
layout: post
title: "Building MAC RAG: A Retrieval-Augmented Generation System for Neuroscience Research"
date: 2025-11-12
---

# Building MAC RAG: A Retrieval-Augmented Generation System for Neuroscience Research

**Yichen Zeng¹, Felicity Aktan¹, Sanjana Avinash Taware¹**

¹University of California, Berkeley - Undergraduate Research Apprentice Program (URAP) and 
UCSF NeuroAI Lab, Fein Memory and Aging Center, Department of Neurology, University of California, San Francisco

*{yzeng, felicitya, sanjana.taware}@berkeley.edu*

## Introduction

During our time as interns at the UCSF NeuroAI Lab, we had the incredible opportunity to develop MAC RAG—a Retrieval-Augmented Generation system designed to enhance LLMs with the knowledge of the UCSF Fein Memory and Aging Center. We curated thousands of papers from MAC faculty to create a comprehensive knowledge base that helps researchers and clinicians access decades of neuroscience literature instantly.

This blog post walks through what we built, why RAG matters, and how this system works under the hood.

## Try It Yourself!

We've deployed MAC RAG on Hugging Face Spaces, which includes both a live demo and the full implementation code. You can interact with the system and see how it retrieves and synthesizes information from neuroscience literature in real-time:

**[Try MAC-RAG on Hugging Face](https://huggingface.co/spaces/ucsf-neuroai-lab/MAC-RAG)**

The demo allows you to:
- Ask complex questions about neurodegenerative diseases
- See which papers and passages the system retrieves
- View full citations for all source material
- Explore how semantic search finds relevant information even with different terminology

We encourage you to try queries like:
- "What are the diagnostic criteria for primary progressive aphasia?"
- "How does Alzheimer's disease affect the hippocampus?"
- "What imaging biomarkers are used for frontotemporal dementia?"

## Summer Research Overview

### What is Retrieval-Augmented Generation?

Retrieval-Augmented Generation (RAG) enhances large language models by grounding their responses in external knowledge sources. Instead of relying solely on training data, RAG systems first retrieve relevant documents from a knowledge base, then use those documents to generate informed, contextually accurate responses.

The architecture involves three key components:
1. **Document Indexing**: Converting documents into searchable embeddings
2. **Retrieval**: Finding the most relevant passages for a given query
3. **Generation**: Using retrieved context to produce accurate, grounded answers

### Why RAG for the Memory and Aging Center?

The Memory and Aging Center at UCSF has published extensively on neurodegenerative diseases, cognitive disorders, and neuroimaging. Researchers and clinicians often need quick access to specific findings.

Traditional keyword search falls short because medical terminology is complex and interconnected. A RAG system understands semantic meaning, not just keywords, making it far more effective at surfacing the right information.

## System Architecture

### The MAC RAG Pipeline

MAC RAG follows a chunk-based RAG architecture designed to handle long scientific papers efficiently:
```
User Query -> Embedding -> Vector Search -> Top-K Chunks -> LLM Processing -> Cited Answer
```

**1. Document Processing and Chunking**

Rather than indexing entire papers, we implemented a chunking strategy that splits documents into overlapping segments of approximately 1,000 characters with a 100-character overlap. This ensures context isn't lost at chunk boundaries and allows the system to pinpoint specific relevant passages.
```python
def chunk_text(text, chunk_size=1000, overlap=100):
    """Split text into chunks with overlap to preserve context."""
    chunks = []
    for i in range(0, len(text), chunk_size - overlap):
        chunks.append(text[i:i + chunk_size])
    return chunks
```

**2. Semantic Indexing with FAISS**

Each chunk is converted into a dense vector embedding using the `all-MiniLM-L6-v2` sentence transformer model. These embeddings capture semantic meaning, allowing the system to find conceptually similar content even when exact keywords don't match.

We used FAISS (Facebook AI Similarity Search) to build a vector index that enables fast nearest-neighbor searches across thousands of document chunks.

**3. Metadata and Citation Tracking**

One of the most important features of MAC RAG is proper citation tracking. Every chunk is linked to its source paper through a metadata system that includes:
- First author
- Publication year
- Full paper title
- Journal name
- PubMed ID (PMID)

This ensures that every answer the system generates can be traced back to its source, maintaining scientific rigor and enabling users to verify information.

**4. Query Processing and Retrieval**

When a user asks a question, the system converts the query into an embedding, performs a vector similarity search to find the top-k most relevant chunks (default k=10), and ranks chunks by relevance.

**5. LLM-Powered Answer Generation**

The retrieved chunks are assembled into a structured prompt for Azure OpenAI's GPT-4 Turbo:
```python
llm_prompt = (
    f"The following chunks are relevant to your question:\n\n"
    f"{chunks_text}\n\n"
    f"Question: {query}\n\n"
    f"Please provide an answer based on the information above."
)
```

This prompt engineering ensures the LLM stays grounded in the retrieved documents rather than generating information from its training data alone.

### The User Interface

We built the interface using Gradio. The interface displays the synthesized answer, full bibliographic citations, and the actual text passages that informed the answer. This transparency allows users to validate the AI's reasoning and dive deeper into source materials.

## Results and Impact

### Performance Observations

MAC RAG demonstrated strong performance across various query types:

The system excelled at answering complex clinical queries, demonstrated strong semantic understanding across different terminology, and maintained citation accuracy through rigorous metadata tracking.

### Real-World Application

During our internship, we had the privilege of witnessing MAC RAG in action during a Clinical Pathology Conference. The system was used to quickly reference diagnostic criteria and treatment approaches, demonstrating its practical value in clinical workflows.

## Technical Deep Dive: Key Implementation Details

### Vector Embedding Strategy

The choice of `all-MiniLM-L6-v2` balances performance with computational efficiency. This 384-dimensional model generates embeddings quickly for real-time querying and captures semantic relationships well within the medical domain.

### Chunking Trade-offs

The 1,000-character chunks with 100-character overlap represent a careful balance between context preservation and retrieval precision.

### FAISS Index Selection

We used `IndexFlatL2`, which performs exact nearest-neighbor search using L2 distance, providing perfect recall and reasonable query latency for our current document set size.

## Challenges and Solutions

### Key Challenges and Solutions

**Handling Long Papers**: Overlapping chunks ensure information spanning boundaries isn't lost while keeping chunk count manageable.

**Citation Accuracy**: Rigorous metadata tracking at the chunk level ensures every piece of information maintains its connection to the source document.

**Retrieval Balance**: After experimentation, k=10 emerged as optimal—enough to capture diverse relevant passages without overwhelming the LLM.

## Looking Forward

### Potential Enhancements

**1. Multi-modal Integration**: We could extend MAC RAG to retrieve and reason over imaging data, not just text.

**2. Fine-tuned Embeddings**: Training domain-specific embeddings on MAC literature could improve retrieval precision.

**3. Conversation Memory**: Adding conversation history would enable multi-turn dialogues.

**4. Dynamic Knowledge Updates**: Implementing automated pipelines to index new papers as they're published would keep the knowledge base current.

## Our Internship Experience

Working at the UCSF NeuroAI Lab was transformative. Beyond building MAC RAG, we:

- Attended multidisciplinary team meetings bringing together neurologists, radiologists, data scientists, and AI researchers
- Shadowed clinicians during patient visits
- Participated in Clinical Pathology Conferences where MAC RAG proved its value in real clinical workflows
- Collaborated with other interns on diverse projects

The most important lesson we learned is that AI in medicine isn't about automation—it's about augmentation. MAC RAG doesn't replace clinical expertise; it amplifies it by making decades of research instantly accessible.

## Conclusion

MAC RAG represents a practical application of RAG technology to a real-world research environment. By combining semantic search with large language models and maintaining rigorous citation practices, the system provides a powerful tool for navigating complex medical literature.

This project demonstrated that well-designed RAG systems can bridge the gap between vast knowledge repositories and the researchers who need them. For the Memory and Aging Center, this means faster literature review and better-informed clinical and research decisions.


## Acknowledgments

We're deeply grateful to the Berkeley Undergraduate Research Apprentice Program (URAP) for making this opportunity possible.

---

*For questions or collaboration opportunities, feel free to reach out or explore the code repository.*

## References

Gao, Y., Xiong, Y., Gao, X., Jia, K., Pan, J., Bi, Y., Dai, Y., Sun, J., Wang, M., & Wang, H. (2023). Retrieval-Augmented Generation for Large Language Models: A Survey. *arXiv preprint arXiv:2312.10997*.

Amazon Web Services. (n.d.). What is Retrieval-Augmented Generation? Retrieved from https://aws.amazon.com/what-is/retrieval-augmented-generation/

Google Cloud. (n.d.). Retrieval-Augmented Generation Use Cases. Retrieved from https://cloud.google.com/use-cases/retrieval-augmented-generation