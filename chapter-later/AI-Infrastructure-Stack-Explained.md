---
layout: default
title: ACME Overview
nav_exclude: true
---

# AI Infrastructure Stack Explained

## Purpose

This document explains the major layers that power modern AI systems such as ChatGPT, Claude, Gemini, DeepSeek, Qwen, and enterprise AI platforms.

The goal is to understand:

- What a model actually is
- What an inference engine does
- Why GPUs are required
- Why CPUs are still important
- How AI chips are manufactured
- The roles of NVIDIA, AMD, TSMC, ASML, and others

---

# 1. The AI Stack

A modern AI solution consists of multiple layers.

```text
Application Layer
       ↓
AI Agent / Copilot
       ↓
Foundation Model
       ↓
Inference Engine
       ↓
GPU Infrastructure
       ↓
Semiconductor Supply Chain
```

Example:

```text
Microsoft Copilot
        ↓
GPT-5
        ↓
OpenAI Inference Runtime
        ↓
NVIDIA Blackwell GPUs
        ↓
TSMC Manufacturing
        ↓
ASML Lithography Machines
```

---

# 2. Models vs Inference Engines

Many people confuse these two concepts.

## Model

A model contains the intelligence.

Examples:

- GPT-5
- Claude
- Gemini
- DeepSeek
- Qwen
- Llama

The model contains:

- Learned patterns
- Language understanding
- Reasoning capabilities
- Coding capabilities
- Domain knowledge

Think of a model as:

```text
Application Code
```

in traditional software.

---

## Inference Engine

The inference engine executes the model.

Examples:

- vLLM
- TensorRT-LLM
- Hugging Face TGI
- SGLang

The inference engine:

- Loads model weights
- Uses GPU resources
- Schedules execution
- Streams responses
- Optimizes throughput

Think of an inference engine as:

```text
JVM
.NET Runtime
```

for AI models.

---

## Simple Analogy

```text
Model = Intelligence

Inference Engine = Runtime

GPU = Compute Resource
```

The model generates the response.

The inference engine enables the model to execute efficiently.

---

# 3. Frontier Models

A frontier model is not a hardware term.

It refers to the most capable AI models currently available.

Examples:

- GPT-5
- Claude Opus
- Gemini
- Grok

The term "frontier model" is an industry term.

There is no official certification body that awards this title.

---

# 4. Enterprise AI Platforms

Examples:

- Microsoft Copilot
- Google Workspace AI
- Salesforce Agentforce
- ServiceNow AI Agents
- Internal Enterprise AI Assistants

These platforms are usually:

```text
Agent Platforms
AI Orchestration Layers
Multi-Model Gateways
```

They typically do not contain:

- Foundation Models
- Inference Engines

Instead they connect to:

- OpenAI
- Anthropic
- Google
- Self-hosted Llama
- Self-hosted DeepSeek
- Self-hosted Qwen

---

# 5. Why GPUs Matter

AI workloads consist primarily of:

```text
Matrix Multiplication
Attention Computation
Vector Operations
```

These tasks are massively parallel.

GPUs are optimized for this type of work.

---

## CPU vs GPU

### CPU

Good at:

- Operating systems
- Scheduling
- Networking
- Storage
- Application logic

### GPU

Good at:

- Parallel mathematics
- Neural network computation
- Tensor operations

---

## AI Server Example

```text
2 x AMD EPYC CPUs
8 x NVIDIA B200 GPUs
```

The CPU coordinates.

The GPU performs the heavy computation.

---

# 6. Why GPUs Still Need CPUs

A GPU is not a standalone computer.

The CPU handles:

- Linux
- Kubernetes
- Networking
- API requests
- Tokenization
- RAG retrieval
- Memory management

The GPU handles:

- Neural network execution

Think of:

```text
CPU = Manager

GPU = Workforce
```

---

# 7. RAM vs CPU vs GPU

Many beginners assume:

```text
More RAM = Faster AI
```

This is incorrect.

## RAM

Determines:

```text
Can the model fit?
```

## CPU/GPU

Determines:

```text
How fast can the model respond?
```

## Simplified Rule

```text
RAM = Capacity

CPU/GPU = Performance
```

---

# 8. Why Frontier AI Data Centers Use AMD CPUs

Historically:

```text
Intel Xeon
+
Enterprise Servers
```

was the standard.

Today many AI systems use:

```text
AMD EPYC
+
NVIDIA GPUs
```

Reasons:

- High memory bandwidth
- Large memory capacity
- High PCIe lane counts
- High core density

The CPU's role is increasingly to feed data to GPUs efficiently.

---

# 9. Why Intel Lost Ground

Intel dominated when:

```text
CPU = Primary Compute Resource
```

AI changed the industry.

The center of gravity moved to:

```text
GPU = Primary Compute Resource
```

Meanwhile:

- NVIDIA dominated AI acceleration
- AMD became highly competitive in server CPUs
- TSMC overtook Intel manufacturing leadership

Intel remains important but no longer dominates AI infrastructure.

---

# 10. The Semiconductor Supply Chain

Many people think:

```text
AMD builds CPUs
NVIDIA builds GPUs
```

This is only partially true.

The supply chain is much larger.

## End-to-End Flow

```text
Sand
  ↓
Purified Silicon
  ↓
Silicon Wafer
  ↓
Transistors
  ↓
Integrated Circuits
  ↓
CPU/GPU Dies
  ↓
Packaged Chips
```

---

# 11. Who Does What?

## AMD / NVIDIA

Responsible for:

- Chip architecture
- Core design
- Cache design
- Memory controllers
- Logic design

They own the blueprint.

## TSMC

Responsible for:

- Wafer fabrication
- Process technology
- Transistor manufacturing
- Yield optimization
- Advanced packaging

TSMC turns the blueprint into a physical chip.

## ASML

Responsible for:

- EUV lithography machines

ASML builds the machines that TSMC uses to manufacture advanced chips.

Without ASML:

```text
No modern TSMC
No modern Intel
No modern Samsung
```

---

# 12. What Is a Silicon Wafer?

A wafer is:

```text
Highly Purified Silicon
```

formed into a thin circular disk.

Typical size:

```text
300 mm diameter
```

It acts as the foundation for building chips.

---

# 13. What Is a Transistor?

A transistor is:

```text
An Electronic Switch
```

It can:

```text
Allow Current
or
Block Current
```

This creates:

```text
1 = ON
0 = OFF
```

which forms the basis of digital computing.

---

# 14. Why Modern Transistors Look Different

The transistors seen in electronics textbooks are:

```text
Discrete Transistors
```

Modern CPUs and GPUs do not contain billions of those components.

Instead:

```text
Billions of microscopic transistor structures
```

are built directly into silicon.

---

# 15. How Are Transistors Created?

They are not assembled one by one.

They are effectively printed.

Process:

```text
Wafer
  ↓
Photoresist
  ↓
Light Exposure
  ↓
Chemical Processing
  ↓
Etching
  ↓
Material Deposition
```

Repeated hundreds of times.

---

# 16. What Is Lithography?

Lithography is the process of projecting microscopic circuit patterns onto a wafer.

Think:

```text
Blueprint
    ↓
Mask
    ↓
Light
    ↓
Wafer
```

The pattern becomes part of the silicon structure.

---

# 17. Why ASML Is So Important

Modern chips require:

```text
EUV Lithography
```

(EUV = Extreme Ultraviolet)

ASML is effectively the only commercial supplier of advanced EUV systems.

Major customers:

- TSMC
- Samsung
- Intel

---

# 18. The Relationship Between AMD, TSMC, and ASML

Think of a construction project.

## AMD

```text
Architect
```

Designs the building.

## TSMC

```text
Construction Company
```

Builds the building.

## ASML

```text
Construction Equipment Manufacturer
```

Builds the machines required to construct the building.

---

# 19. The Dependency Chain Behind ChatGPT

When a user asks ChatGPT a question:

```text
User
   ↓
ChatGPT
   ↓
GPT-5
   ↓
Inference Engine
   ↓
NVIDIA GPU
   ↓
TSMC Fabrication
   ↓
ASML EUV Machine
```

Every layer depends on the one below it.

---

# 20. Key Industry Players by Layer

| Layer | Major Players |
|---------|--------------|
| AI Applications | ChatGPT, Copilot, Gemini Apps, Claude |
| Agent Platforms | Copilot Studio, Agentforce, ServiceNow AI |
| Foundation Models | OpenAI, Anthropic, Google, xAI, DeepSeek, Alibaba |
| Inference Engines | vLLM, TensorRT-LLM, TGI, SGLang |
| GPUs | NVIDIA, AMD |
| CPUs | AMD, Intel, NVIDIA Grace |
| Foundries | TSMC, Samsung, Intel Foundry |
| Lithography | ASML |
| EDA Tools | Synopsys, Cadence, Siemens EDA |

---

# Key Takeaways

1. Models contain intelligence.
2. Inference engines execute models.
3. GPUs perform AI computation.
4. CPUs coordinate AI computation.
5. RAM determines capacity, not speed.
6. AMD and NVIDIA design chips.
7. TSMC manufactures chips.
8. ASML builds the lithography machines.
9. Modern chips are printed using light and chemistry.
10. The AI revolution ultimately depends on a highly specialized global semiconductor ecosystem.
11. No single company owns the entire AI stack.
12. Modern AI exists because thousands of companies contribute to different layers of the ecosystem.
