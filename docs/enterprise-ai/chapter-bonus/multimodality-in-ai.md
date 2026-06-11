---
layout: default
title: ACME Overview
nav_exclude: true
---

# Multimodality in AI

## What Is Multimodality?

Multimodality refers to an AI system's ability to understand, process, and generate multiple forms of information, known as **modalities**.

A modality is simply a type of data.

Examples include:

- Text
- Images
- Audio
- Video
- Documents (PDFs, PowerPoint, Word files)
- Code
- Sensor Data

Instead of being limited to a single input type, a multimodal AI system can work across several types of information simultaneously.

---

# Understanding Modalities

Humans naturally process multiple modalities.

For example, during a meeting you may:

- Listen to speech
- Read slides
- Watch body language
- Take notes

Your brain combines all of these information sources into a unified understanding.

Modern AI systems are increasingly designed to work in a similar way.

---

# Single-Modal AI

Traditional AI systems were typically built for one specific modality.

Examples:

| System Type | Input | Output |
|-------------|---------|---------|
| Chatbot | Text | Text |
| OCR System | Image | Text |
| Speech Recognition | Audio | Text |
| Image Classifier | Image | Label |
| Translation System | Text | Text |

Each system performed one specialized task.

```text
Text AI
Image AI
Audio AI
Video AI
```

Separate models.

Separate capabilities.

---

# Multimodal AI

A multimodal model can process multiple data types using a unified architecture.

Examples:

| Input | Output |
|---------|---------|
| Text | Text |
| Image | Text |
| Audio | Text |
| Video | Text |
| Text | Image |
| Audio | Audio |
| Image + Text | Text |

The model can reason across different types of information rather than treating each one separately.

---

# Example 1: Image Understanding

Suppose you upload a photograph of a server rack.

You ask:

> What is wrong in this setup?

The model can:

1. Analyze the image.
2. Identify disconnected cables.
3. Read labels and indicators.
4. Explain findings in text.

Input:

```text
Image
```

Output:

```text
Text
```

---

# Example 2: Document Analysis

Suppose you upload a cloud architecture document containing:

- Text
- Diagrams
- Tables
- Screenshots

You ask:

> Summarize the migration strategy.

The model can:

1. Read text.
2. Interpret diagrams.
3. Analyze tables.
4. Generate a summary.

Inputs:

```text
PDF
Text
Images
Tables
```

Output:

```text
Text
```

---

# Example 3: Voice Conversation

You speak:

> What will the weather be tomorrow?

The AI system:

1. Receives audio.
2. Converts speech into internal representations.
3. Understands intent.
4. Generates a response.
5. Converts response back into speech.

Input:

```text
Audio
```

Output:

```text
Audio
```

This creates a natural conversational experience.

---

# Example 4: Video Understanding

Suppose you upload a Kubernetes deployment walkthrough video.

You ask:

> Explain what is happening in this deployment.

The model can:

1. Analyze video frames.
2. Read terminal output.
3. Understand spoken narration.
4. Combine all information.
5. Produce a summary.

Input:

```text
Video
+
Audio
```

Output:

```text
Text
```

---

# Why Multimodality Matters

The real world is naturally multimodal.

Humans communicate through:

```text
Text
Speech
Images
Video
Documents
Gestures
```

An AI system restricted to text alone misses a significant portion of available information.

Multimodality allows AI systems to operate more like humans by combining information from multiple sources.

---

# Evolution of AI Systems

## Phase 1: Specialized Models

Early AI systems used separate models.

```text
Image
  ↓
Vision Model

Audio
  ↓
Speech Model

Text
  ↓
Language Model
```

Each model handled only one task.

Cross-modal reasoning was difficult.

---

## Phase 2: Connected Pipelines

Organizations started connecting multiple models together.

Example:

```text
Image
  ↓
Vision Model
  ↓
Text
  ↓
Language Model
```

This worked but introduced complexity and inefficiencies.

---

## Phase 3: Unified Multimodal Models

Modern frontier models increasingly use a single architecture.

```text
Text
Image
Audio
Video
   ↓
Unified Model
   ↓
Output
```

This allows the model to reason across modalities directly.

---

# How Modern Multimodal Models Work

The key idea is converting different data types into a common representation.

Conceptually:

```text
Text
  ↓

Image
  ↓

Audio
  ↓

Video
  ↓

Tokens
```

Once converted into tokens, the same transformer architecture can process all of them.

```text
Text    ─┐
Image   ─┼─> Tokens ─> Transformer ─> Output Tokens
Audio   ─┤
Video   ─┘
```

This is one of the biggest innovations behind modern multimodal systems.

---

# What Are Tokens?

A token is the internal unit a model processes.

For text:

```text
"Cloud Computing"
```

may become:

```text
[Token 182]
[Token 493]
```

For images:

```text
Pixels
    ↓
Image Encoder
    ↓
Visual Tokens
```

For audio:

```text
Sound Waves
      ↓
Audio Encoder
      ↓
Audio Tokens
```

Eventually everything becomes tokens that the transformer can understand.

---

# Why This Is Powerful

Because all information is converted into a common format, the model can reason across modalities.

Example:

```text
Image of Architecture Diagram
             +
Question About Design
             ↓
Reasoning
             ↓
Architecture Review
```

The model can connect visual information with textual understanding.

---

# Multimodality vs Multi-Model Systems

Many people confuse these concepts.

## Multi-Model System

```text
Vision Model
      +
Speech Model
      +
Language Model
```

Several specialized models connected together.

---

## Multimodal Model

```text
One Model
    ↓
Understands
Text
Images
Audio
Video
```

A single architecture capable of handling multiple modalities.

---

# Examples of Multimodal Tasks

## Infrastructure and Cloud

- Analyze architecture diagrams
- Review Terraform screenshots
- Interpret monitoring dashboards
- Explain network topologies

---

## Enterprise Documentation

- Read PDFs
- Summarize PowerPoint presentations
- Analyze spreadsheets
- Review technical documentation

---

## Software Development

- Read source code
- Analyze screenshots
- Review logs
- Generate explanations

---

## Voice Interaction

- Speech understanding
- Spoken responses
- Meeting summaries
- Voice assistants

---

# Multimodality in ChatGPT

Modern versions of ChatGPT support multiple modalities including:

- Text
- Images
- Voice
- Documents
- Code
- Image Generation

Examples:

```text
Upload Architecture Diagram
             ↓
Receive Design Review
```

```text
Upload Terraform Screenshot
             ↓
Receive Infrastructure Analysis
```

```text
Speak A Question
             ↓
Receive Spoken Response
```

```text
Describe An Architecture
             ↓
Generate An Image
```

---

# The Big Picture

The progression of AI can be viewed as:

```text
Single-Modal AI
        ↓
Connected Multi-Model Systems
        ↓
Unified Multimodal Models
```

The long-term industry direction is toward models that can seamlessly understand and generate:

```text
Text
Images
Audio
Video
Documents
Code
```

within a single architecture.

---

# Key Takeaway

Multimodality is the ability of an AI system to understand, reason over, and generate multiple forms of information using a unified model.

Conceptually:

```text
Text
Image
Audio
Video
   ↓
Common Representation
   ↓
Transformer
   ↓
Reasoning
   ↓
Output
```

The goal of multimodality is to allow AI systems to interact with information in a way that more closely resembles how humans perceive and understand the world.