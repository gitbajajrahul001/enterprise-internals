---
layout: default
title: ACME Overview
nav_exclude: true
---

# Quantization and AI Deployment Models

## Introduction

As Large Language Models (LLMs) continue to grow in size, the infrastructure required to run them becomes increasingly expensive. One of the most important techniques that makes modern AI practical is **quantization**.

Quantization allows models to run with significantly less memory and hardware while preserving most of their capabilities.

This document explains:

- What quantization is
- Why it exists
- How model weights are stored
- Training precision vs inference precision
- Why quantization matters for enterprises
- The difference between Self-Hosted AI, Private AI, On-Prem AI, Sovereign AI, and Edge AI

---

# Understanding Model Weights

A trained AI model is fundamentally a massive collection of numbers called **weights**.

Example:

```text
0.8273648293
-1.2746382934
0.0038473829
2.9384738291
```

These weights represent everything the model has learned during training.

Modern models may contain:

- Billions of parameters
- Hundreds of billions of parameters
- Trillions of parameters

The larger the model, the more memory is required to store these weights.

---

# What is Quantization?

## Simple Definition

Quantization is the process of storing model weights with lower numerical precision.

Instead of storing:

```text
0.8273648293
```

Store:

```text
0.83
```

Instead of:

```text
-1.2746382934
```

Store:

```text
-1.27
```

The goal is to reduce memory consumption while maintaining acceptable model quality.

---

# Real-World Analogy

Imagine someone asks for your height.

Exact:

```text
178.423891 cm
```

Rounded:

```text
178.4 cm
```

Or:

```text
178 cm
```

In most situations, nothing meaningful is lost.

Quantization applies the same concept to billions of model weights.

---

# Why Quantization Works

A neural network does not depend on perfect precision for every individual weight.

Example:

```text
0.823847293
```

versus

```text
0.82
```

The difference is extremely small.

Because intelligence is distributed across billions of weights, small precision losses often have minimal impact on model behavior.

---

# Common Precision Formats

| Format | Bits per Weight | Typical Usage |
|----------|----------|----------|
| FP32 | 32 | Traditional training |
| FP16 | 16 | Inference and training |
| BF16 | 16 | Modern large-scale training |
| INT8 | 8 | Quantized inference |
| INT6 | 6 | Aggressive optimization |
| INT5 | 5 | Local LLM deployments |
| INT4 | 4 | Highly popular for self-hosted AI |
| INT3 | 3 | Noticeable quality loss |
| INT2 | 2 | Often impractical |

---

# Example Memory Savings

Assume a model contains:

```text
7 Billion Parameters
```

## FP16

```text
7B × 2 bytes
≈ 14 GB
```

## INT8

```text
7B × 1 byte
≈ 7 GB
```

## INT4

```text
7B × 0.5 bytes
≈ 3.5 GB
```

Same model.

Much lower memory requirement.

---

# Training Precision vs Inference Precision

This is one of the most misunderstood concepts in AI infrastructure.

## During Training

Historically:

```text
FP32
```

was used everywhere.

Modern frontier models usually use:

```text
BF16 + FP32 Mixed Precision
```

Typical workflow:

```text
Master Weights      -> FP32
Forward Pass        -> BF16
Backward Pass       -> BF16
Optimizer Updates   -> FP32
```

This approach reduces memory usage while maintaining numerical stability.

---

## After Training

The trained model is typically saved as:

```text
BF16
```

or

```text
FP16
```

This becomes the model's "full precision" release.

---

## After Release

The model may then be converted into:

```text
INT8
INT6
INT5
INT4
```

versions for efficient inference.

This process is quantization.

---

# The Model Lifecycle

```text
Training
(BF16 + FP32)

        ↓

Published Model
(BF16 / FP16)

        ↓

Quantized Versions
(INT8 / INT6 / INT5 / INT4)

        ↓

Production Inference
```

---

# Why Quantization Matters

## Benefits

### Reduced Memory

Models require significantly less RAM and VRAM.

### Lower Infrastructure Cost

Fewer GPUs are needed.

### Faster Inference

Less data movement between memory and compute units.

### Increased Scalability

More users can be served simultaneously.

### Local Deployment

Large models can run on commodity hardware.

---

## Trade-Offs

As quantization becomes more aggressive:

### Advantages

```text
Lower Cost
Lower Memory
Higher Throughput
```

### Disadvantages

```text
Reduced Accuracy
Reduced Reasoning Quality
More Hallucinations
```

The objective is to find the optimal balance.

---

# Enterprise Relevance

## Managed AI Services

Examples:

- OpenAI APIs
- Anthropic APIs
- Gemini APIs

In these scenarios:

```text
Quantization is largely invisible.
```

Organizations focus on:

- Cost per token
- Latency
- Governance
- Security
- Model selection

The AI provider manages model optimization internally.

---

## Self-Hosted AI

Quantization becomes a major architectural decision.

Example:

### Full Precision

```text
70B Parameters
≈ 140 GB BF16
```

May require:

- Multiple GPUs
- Expensive infrastructure
- Significant operational cost

### INT4 Quantized

```text
70B Parameters
≈ 35 GB
```

May fit on a single high-memory GPU.

This dramatically changes deployment economics.

---

# AI Deployment Models

Many organizations use the following terms interchangeably.

They are related, but they describe different architectural dimensions.

---

# Self-Hosted AI

## Question

Who operates the infrastructure?

## Answer

```text
The organization itself.
```

Examples:

- Self-managed Kubernetes
- Self-managed GPU clusters
- Self-hosted LLM deployments

Characteristics:

- Full operational ownership
- Full infrastructure control

---

# Private AI

## Question

Who can access the data?

## Answer

```text
Only authorized parties.
```

Focus areas:

- Data privacy
- Governance
- Security
- Isolation

Private AI may be:

- Self-hosted
- Cloud-hosted
- Provider-hosted

Privacy is the defining characteristic.

---

# On-Prem AI

## Question

Where is the hardware located?

## Answer

```text
Inside the organization's facilities.
```

Examples:

- Corporate datacenter
- Colocation facility
- Internal GPU clusters

Every On-Prem AI deployment is self-hosted.

However:

```text
Not every self-hosted deployment is on-prem.
```

A self-managed deployment in AWS or Azure is self-hosted but not on-prem.

---

# Sovereign AI

## Question

Under whose laws and jurisdiction does the AI operate?

## Focus Areas

- National regulations
- Data residency
- Legal control
- Government requirements

Examples:

- Government AI platforms
- Defense systems
- Regulated financial workloads

The defining factor is regulatory control, not hardware ownership.

---

# Edge AI

## Question

Where does inference occur?

## Answer

```text
Close to the data source.
```

Examples:

- Manufacturing equipment
- Retail stores
- Hospitals
- Vehicles
- Industrial IoT systems

Instead of:

```text
Device
    ↓
Cloud
    ↓
Inference
```

You get:

```text
Device
    ↓
Local Inference
```

The objective is low latency and reduced dependency on central infrastructure.

---

# Understanding the Relationship

These are not mutually exclusive categories.

They are independent architectural dimensions.

Example:

A manufacturing company runs a quantized LLM:

- On local factory servers
- Managed by internal teams
- Data never leaves the country
- Inference occurs at the factory

This deployment is simultaneously:

```text
✓ Self-Hosted
✓ Private AI
✓ On-Prem AI
✓ Sovereign AI
✓ Edge AI
```

---

# Enterprise Architecture Framework

When evaluating an AI platform, ask five separate questions:

| Dimension | Key Question |
|------------|------------|
| Self-Hosted | Who operates the infrastructure? |
| Private AI | Who can access the data? |
| On-Prem AI | Where is the hardware located? |
| Sovereign AI | Which jurisdiction governs the platform? |
| Edge AI | Where does inference execute? |

Treat these as independent design decisions rather than deployment categories.

---

# Key Takeaways

## Quantization

- Reduces model precision to reduce memory usage.
- Makes large models cheaper and faster to run.
- Enables local and self-hosted AI deployments.
- Introduces a trade-off between quality and efficiency.

## Training

- Modern frontier models are typically trained using BF16 and FP32 mixed precision.
- Published model weights are usually BF16 or FP16.

## Inference

- Quantized models are commonly distributed as INT8, INT6, INT5, or INT4 variants.

## Enterprise Impact

- Managed AI consumers rarely need to think about quantization.
- Self-hosted AI deployments depend heavily on quantization decisions.

## Deployment Models

- Self-Hosted = Operational ownership
- Private AI = Data privacy
- On-Prem AI = Hardware location
- Sovereign AI = Jurisdiction and compliance
- Edge AI = Inference location

These dimensions can coexist within the same AI platform.