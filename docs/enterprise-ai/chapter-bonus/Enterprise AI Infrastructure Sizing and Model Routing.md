---
layout: default
title: ACME Overview
nav_exclude: true
---

# Enterprise AI Infrastructure Sizing and Model Routing

## Introduction

One of the most common misconceptions when designing an enterprise AI platform is:

> If a model fits into GPU memory, then the infrastructure sizing problem is solved.

In reality, model size is only one part of the equation.

The real challenge is:

- Concurrent users
- Throughput
- Latency
- Cost per request
- GPU utilization

This document explains why AI platform sizing is primarily a capacity-planning problem rather than a model-storage problem.

---

# Model Size vs Platform Capacity

Consider a Llama 70B model.

## Memory Requirement

### BF16

```text
70B × 2 bytes
≈ 140 GB
```

### INT8

```text
70B × 1 byte
≈ 70 GB
```

### INT4

```text
70B × 0.5 bytes
≈ 35 GB
```

A modern high-memory GPU can host such a model.

Many people stop the analysis here.

However:

```text
Model Fits ≠ Platform Scales
```

---

# The Real Question

The important question is not:

```text
Can I load the model?
```

The important question is:

```text
How many users can I serve simultaneously?
```

This is the same distinction that exists in traditional infrastructure.

Example:

```text
One web server can host a website.
```

But:

```text
Can it support 100,000 users?
```

That depends on capacity, not installation.

The same principle applies to LLMs.

---

# Example Enterprise

| Metric | Value |
|----------|----------|
| Employees | 50,000 |
| Peak Concurrent Users | 3,000 |
| Requests Per Day | 100,000 |
| Average Prompt Size | 2,000 Tokens |
| Average Response Size | 800 Tokens |
| Model | Llama 70B |
| Quantization | INT8 |
| Latency Target | <5 Seconds |

---

# Daily Workload

Total tokens per request:

```text
2,000 Input
+
800 Output
=
2,800 Tokens
```

Daily token volume:

```text
100,000 Requests
×
2,800 Tokens
=
280 Million Tokens Per Day
```

---

# The Most Important Metric

Many architects focus on:

```text
50,000 Users
```

The more important metric is:

```text
3,000 Concurrent Users
```

Concurrency typically drives infrastructure requirements far more than total user count.

---

# Why One GPU Is Not Enough

Assume:

```text
Llama 70B INT8
```

is hosted on a high-memory GPU.

Even though the model fits:

```text
70-120 GB VRAM
```

the GPU still has finite inference capacity.

The limiting factor becomes:

```text
Tokens Per Second
```

rather than memory.

---

# Enterprise Sizing Reality

A single high-end GPU might support:

```text
20-50 Active Sessions
```

depending on:

- Model size
- Context length
- Response size
- Batching strategy
- Latency targets

Using:

```text
40 Concurrent Sessions Per GPU
```

as a planning estimate:

```text
3,000 Concurrent Users
÷
40
=
75 GPUs
```

Adding:

- High availability
- Maintenance capacity
- Growth headroom

results in:

```text
90-100 GPUs
```

for a production-grade deployment.

---

# Why Concurrency Matters More Than Storage

Consider two organizations.

## Organization A

```text
1 Million Requests Per Day
```

but spread evenly.

Low concurrency.

May require relatively modest infrastructure.

---

## Organization B

```text
100,000 Requests Per Day
```

but concentrated into:

```text
3,000 Concurrent Users
```

May require significantly larger GPU infrastructure.

---

# Single Model Architecture

A common initial design is:

```text
All Requests
       ↓
Llama 70B
```

Advantages:

- Simple architecture
- Consistent model behavior

Disadvantages:

- Expensive
- Low throughput
- Large GPU footprint

Every request uses the most expensive model.

---

# Why This Is Inefficient

Many enterprise requests are simple.

Examples:

- Summarize an email
- Create meeting minutes
- Explain a company policy
- Retrieve information from internal documentation
- Draft a response

Using a 70B model for all requests is similar to:

```text
Using a senior enterprise architect
to reset user passwords.
```

It works, but it is inefficient.

---

# Multi-Model Architecture

A more mature approach is:

```text
80% Requests → 8B Model

15% Requests → 70B Model

5% Requests → Frontier Model API
```

---

# Typical Routing Strategy

## Small Model (8B)

Handles:

- Summarization
- Email drafting
- FAQ responses
- Internal documentation queries
- Policy lookups
- Basic RAG workloads

---

## Large Model (70B)

Handles:

- Complex reasoning
- Architecture analysis
- Advanced coding
- Multi-document synthesis
- Deep technical tasks

---

## Frontier API

Handles:

- Rare, high-value requests
- Specialized reasoning tasks
- Workloads not justified for self-hosting

Examples:

- Strategic planning
- Large-scale analysis
- Advanced research tasks

---

# Why Multiple Models Reduce Infrastructure Costs

At first glance:

```text
More Models
=
More Infrastructure
```

appears logical.

In practice:

```text
More Models
=
Less Total GPU Consumption
```

because most requests are routed to smaller, cheaper models.

---

# Illustrative Example

## Everything on 70B

```text
100,000 Requests
×
70B Compute Cost
=
Very Large GPU Requirement
```

---

## Routed Architecture

```text
80,000 Requests → 8B

15,000 Requests → 70B

5,000 Requests → Frontier API
```

The majority of GPU demand shifts away from the expensive model.

This significantly reduces:

- GPU count
- Cost
- Power consumption
- Infrastructure complexity

---

# Throughput Advantage of Smaller Models

Smaller models typically provide:

```text
Lower VRAM Usage
Higher Throughput
Lower Latency
```

Example:

### 70B Model

```text
~40 Concurrent Sessions/GPU
```

### 8B Model

```text
Hundreds of Concurrent Sessions/GPU
```

Actual values vary by hardware and software stack, but the scaling advantage is substantial.

---

# Why Frontier APIs Remain Useful

Some workloads occur too infrequently to justify dedicated infrastructure.

Example:

```text
Generate a complete enterprise transformation strategy
for 500 applications.
```

If such requests occur:

```text
5 times per day
```

it may be more economical to use a frontier API than to provision additional GPU capacity.

---

# Recommended Enterprise Architecture

```text
Users
   ↓
AI Gateway
   ↓
Request Classification
   ↓
 ┌──────────────┬──────────────┬──────────────┐
 │              │              │
 ↓              ↓              ↓

8B Model      70B Model    Frontier API
```

The routing layer determines the most cost-effective model for each request.

---

# Key Lessons

## Model Fit Is Only the Starting Point

A model fitting into GPU memory does not guarantee platform scalability.

---

## Concurrency Drives Infrastructure

The most important sizing metric is often:

```text
Peak Concurrent Users
```

rather than total user count.

---

## GPU Time Is the Expensive Resource

The primary cost driver is:

```text
Inference Compute
```

not model storage.

---

## Multi-Model Platforms Are More Efficient

Most mature enterprise AI platforms use:

- Small models for common tasks
- Large models for advanced tasks
- Frontier APIs for exceptional workloads

---

## Routing Is a Core Platform Capability

The goal is not:

```text
One Model For Everything
```

The goal is:

```text
Right Model For The Right Task
```

This approach typically delivers:

- Better scalability
- Lower cost
- Higher throughput
- More efficient GPU utilization
- Improved enterprise economics