---
layout: default
title: RAG Pipelines
parent: Chapter 04 — Building AI Systems
nav_order: 5
---

# RAG Pipelines

> Understanding the complete flow of how information moves from enterprise documents to AI-generated responses.

---

# Why This Topic Matters

In the previous chapter we learned:

```plaintext
Question
        ↓
Retrieve Information
        ↓
Inject Into Context
        ↓
Generate Response
```

This describes RAG conceptually.

However, real-world RAG systems are significantly more complex.

Organizations often assume:

```plaintext
Upload Documents
        ↓
AI Works
```

Reality looks more like:

```plaintext
Documents
        ↓
Processing
        ↓
Chunking
        ↓
Embedding
        ↓
Storage
        ↓
Retrieval
        ↓
Context Construction
        ↓
Generation
```

Every stage influences:

- quality,
- performance,
- cost,
- scalability,
- and user experience.

This complete workflow is called:

# The RAG Pipeline

---

# The Big Picture

A production RAG system usually consists of two separate workflows:

---

## Ingestion Pipeline

Responsible for:

```plaintext
Preparing Knowledge
```

---

## Retrieval Pipeline

Responsible for:

```plaintext
Answering Questions
```

---

Conceptually:

```plaintext
Knowledge Preparation
        ↓
Knowledge Retrieval
```

These are independent systems.

---

# The Two-Pipeline Architecture

```plaintext
Documents
        ↓
Ingestion Pipeline
        ↓
Knowledge Store

---------------------

User Question
        ↓
Retrieval Pipeline
        ↓
Response
```

Most people only see the second half.

Architects must understand both.

---

# Part 1 — The Ingestion Pipeline

The ingestion pipeline prepares enterprise knowledge for retrieval.

Without this phase:

```plaintext
Nothing Can Be Retrieved
```

---

# Step 1 — Document Collection

The journey begins with source content.

Examples:

```plaintext
PDF Files

Word Documents

SharePoint

Confluence

ServiceNow

Wikis

Emails

Runbooks

Policies
```

These sources become:

```plaintext
Raw Knowledge
```

---

# Infrastructure Analogy

Think of this as:

```plaintext
Data Acquisition
```

before analytics can occur.

AI systems require a similar preparation phase.

---

# Step 2 — Document Parsing

Raw documents are rarely AI-friendly.

Example:

```plaintext
PDF
```

contains:

- text,
- images,
- tables,
- headers,
- footers,
- formatting.

The system extracts usable content.

---

Example:

Before:

```plaintext
Complex PDF
```

After:

```plaintext
Plain Text
```

This becomes the foundation for later stages.

---

# Step 3 — Chunking

Recall Chapter 2:

Vector databases usually store:

```plaintext
Chunks
```

not:

```plaintext
Entire Documents
```

Example:

Document:

```plaintext
100 Pages
```

becomes:

```plaintext
Chunk 1

Chunk 2

Chunk 3

...
```

This is one of the most important stages in the entire pipeline.

---

# Why Chunking Matters

Retrieval happens at:

```plaintext
Chunk Level
```

not:

```plaintext
Document Level
```

Poor chunking creates:

- weak retrieval,
- fragmented context,
- incomplete answers.

Many failed RAG systems are actually:

```plaintext
Chunking Problems
```

disguised as AI problems.

---

# Step 4 — Metadata Enrichment

Each chunk often receives metadata.

Example:

```plaintext
Source Document

Author

Department

Date

Document Type

Security Classification
```

Metadata later improves:

- filtering,
- retrieval,
- governance,
- and citations.

---

# Step 5 — Embedding Generation

Each chunk is converted into:

```plaintext
Vector Representation
```

using an embedding model.

Conceptually:

```plaintext
Chunk
        ↓
Embedding Model
        ↓
Vector
```

Now semantic search becomes possible.

---

# Step 6 — Storage

At this stage:

Two things are typically stored.

---

## Original Chunk

```plaintext
Actual Text
```

---

## Embedding

```plaintext
Numerical Representation
```

These may reside in:

- vector databases,
- document stores,
- search platforms,
- hybrid architectures.

---

# Important Observation

Recall our earlier discussion.

Vector databases often store:

```plaintext
Vectors
```

and frequently:

```plaintext
Associated Chunk Text
```

as metadata.

However large enterprise architectures often separate:

```plaintext
Vector Storage
```

from:

```plaintext
Document Storage
```

for scalability reasons.

Both patterns exist.

---

# The Ingestion Pipeline Ends

At this point:

```plaintext
Knowledge Is Prepared
```

The system is now ready to answer questions.

---

# Part 2 — The Retrieval Pipeline

Everything changes when a user submits a question.

---

# Step 1 — User Question

Example:

```plaintext
What is our annual leave policy?
```

---

# Step 2 — Query Embedding

The question is converted into:

```plaintext
Vector Form
```

using the same embedding model.

Conceptually:

```plaintext
Question
        ↓
Embedding
        ↓
Vector
```

---

# Step 3 — Similarity Search

The vector database searches for:

```plaintext
Most Similar Chunks
```

Example:

```plaintext
Question Vector
        ↓
Vector Search
        ↓
Top Matching Chunks
```

This is the retrieval stage.

---

# Step 4 — Chunk Selection

The system may retrieve:

```plaintext
Top 5

Top 10

Top 20
```

matching chunks.

The exact strategy varies.

---

# Step 5 — Context Construction

Retrieved chunks are assembled into:

```plaintext
Prompt Context
```

Example:

```plaintext
System Prompt

Retrieved Chunks

User Question
```

All combined into one context window.

---

# This Is The Critical Moment

The model does not directly access:

```plaintext
Vector Database
```

The model only sees:

```plaintext
Constructed Context
```

This distinction is crucial.

---

# Step 6 — Generation

Now the LLM receives:

```plaintext
Question

Retrieved Information

Instructions
```

and generates:

```plaintext
Final Response
```

This is the generation phase.

---

# The Complete RAG Pipeline

Putting everything together:

```plaintext
Documents
        ↓
Parsing
        ↓
Chunking
        ↓
Metadata
        ↓
Embeddings
        ↓
Storage

--------------------------------

User Question
        ↓
Embedding
        ↓
Similarity Search
        ↓
Chunk Retrieval
        ↓
Context Construction
        ↓
LLM
        ↓
Response
```

This architecture powers most enterprise RAG systems today.

---

# Why Pipeline Thinking Matters

Many teams blame:

```plaintext
The Model
```

when results are poor.

In reality failures may occur in:

```plaintext
Parsing

Chunking

Metadata

Embeddings

Retrieval

Context Construction
```

The model may be performing perfectly.

---

# The Weakest-Link Principle

RAG quality often follows:

```plaintext
Weakest Component
        ↓
System Quality
```

Example:

Excellent model:

```plaintext
GPT
```

Poor retrieval:

```plaintext
Poor Response
```

---

Conversely:

Good retrieval:

```plaintext
Relevant Information
```

plus

Medium-sized model:

```plaintext
Strong Response
```

This surprises many organizations.

---

# Why Enterprise AI Becomes Architecture

Notice how little of this pipeline involves:

```plaintext
Model Training
```

Most effort goes into:

- data,
- retrieval,
- governance,
- orchestration,
- and context delivery.

This is why enterprise AI increasingly resembles:

```plaintext
Systems Architecture
```

rather than:

```plaintext
Machine Learning Research
```

---

# Common Misconceptions

## Misconception 1

### RAG is a single component.

Reality:

RAG is an end-to-end pipeline composed of multiple stages.

---

## Misconception 2

### The model performs retrieval.

Reality:

Retrieval occurs before the model receives the prompt.

---

## Misconception 3

### Better models automatically fix poor RAG.

Reality:

Weak retrieval often remains weak regardless of model quality.

---

## Misconception 4

### Vector databases are the entire RAG solution.

Reality:

Vector databases are only one component of a much larger pipeline.

---

# The Bigger Architectural Realization

RAG introduced a new architectural pattern:

```plaintext
Knowledge Systems
        +
Retrieval Systems
        +
Language Models
```

The value no longer comes solely from:

```plaintext
Model Intelligence
```

but from:

```plaintext
Information Delivery
```

This is one reason enterprise AI projects increasingly resemble platform engineering initiatives.

---

# Foundational Takeaway

A RAG pipeline fundamentally provides:

> A structured workflow that transforms enterprise knowledge into retrievable context and delivers that context to an LLM during inference.

The quality of a RAG system depends not only on the model, but on every stage of the pipeline that prepares, retrieves, and delivers information.

In enterprise AI:

> The retrieval pipeline is often just as important as the model itself.

---

[⬅ Series Home](index.md) | [⬅Retrieval Augmented Generation (RAG)](04-retrieval-augmented-generation-rag.md) | [Hybrid Search➡](06-hybrid-search.md)