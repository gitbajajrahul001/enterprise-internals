---
layout: default
title: What Is an Agent
parent: Chapter 05 — Agents and Tool Use
nav_order: 2
---

# What Is an Agent?

> Understanding the internal architecture of an AI agent and why agents are fundamentally different from chatbots, workflows, and traditional automation systems.

---

# Why This Topic Matters

The term:

```plaintext
Agent
```

has become one of the most overused words in AI.

Today you will hear:

- AI Agents
- Autonomous Agents
- Enterprise Agents
- Agentic AI
- Multi-Agent Systems

Unfortunately many discussions stop at:

```plaintext
Agent
=
AI That Does Stuff
```

This is not particularly useful.

To understand agents properly we must answer:

> What actually happens inside an agent?

Because once you understand the architecture, most of the industry hype becomes much easier to evaluate.

---

# Revisiting The Previous Chapter

We established:

---

## Chatbot

```plaintext
Question
        ↓
Response
```

---

## Agent

```plaintext
Goal
        ↓
Plan
        ↓
Act
        ↓
Outcome
```

This is directionally correct.

But still incomplete.

---

# The Simplest Definition

An agent is:

> A system that uses an LLM to decide what actions should be taken in order to achieve a goal.

Notice something important.

The definition does NOT say:

```plaintext
An Agent Is A Model
```

because it is not.

---

# Important Mental Model

An agent is usually:

```plaintext
LLM
        +
Tools
        +
Memory
        +
Execution Logic
```

The model is only one component.

This is one of the most important concepts in modern AI.

---

# The Historical Comparison

Traditional software often follows:

```plaintext
Input
        ↓
Code
        ↓
Output
```

The workflow is predefined.

Developers decide every step.

---

Agents introduce:

```plaintext
Input
        ↓
Reasoning
        ↓
Decision
        ↓
Action
        ↓
Output
```

The sequence is no longer entirely predetermined.

---

# The Core Idea

Instead of hardcoding:

```plaintext
Step 1

Step 2

Step 3
```

developers increasingly provide:

```plaintext
Goal
```

and allow the agent to determine:

```plaintext
How To Reach It
```

This is a major architectural shift.

---

# Human Analogy

Imagine asking:

```plaintext
Book a flight to London.
```

You do not specify:

```plaintext
Open Browser

Visit Website

Search Flights

Compare Prices

Complete Booking
```

The employee determines those steps.

Agents attempt to behave similarly.

---

# The Internal Architecture

A simplified agent often looks like:

```plaintext
User Goal
        ↓
LLM
        ↓
Reasoning
        ↓
Tool Selection
        ↓
Execution
        ↓
Result
```

The critical new capability is:

```plaintext
Tool Selection
```

---

# Why Tools Matter

Recall:

An LLM alone can only generate:

```plaintext
Text
```

It cannot:

- create a VM,
- send an email,
- query a database,
- create a ticket,
- restart a server.

Without tools:

```plaintext
Knowledge Exists

Action Does Not
```

This limitation is fundamental.

---

# Example Without Tools

User:

```plaintext
Create a Jira ticket.
```

LLM:

```plaintext
Here is how you create a Jira ticket...
```

Useful.

But nothing actually happened.

---

# Example With Tools

User:

```plaintext
Create a Jira ticket.
```

Agent:

```plaintext
Determine Intent
        ↓
Call Jira API
        ↓
Create Ticket
        ↓
Return Ticket Number
```

Now action occurs.

---

# The Agent Loop

Most agents operate through a loop.

Conceptually:

```plaintext
Goal
        ↓
Think
        ↓
Act
        ↓
Observe
        ↓
Think Again
        ↓
Act Again
```

This repeats until:

```plaintext
Goal Achieved
```

or

```plaintext
Failure Occurs
```

---

# Why This Is Important

A chatbot usually performs:

```plaintext
One Pass
```

An agent often performs:

```plaintext
Multiple Iterations
```

This distinction is enormous.

---

# Example Agent Loop

User:

```plaintext
Find the latest Azure outage affecting storage services.
```

Agent may:

```plaintext
Search Status Sources
        ↓
Review Results
        ↓
Identify Relevant Incident
        ↓
Summarize Findings
        ↓
Return Response
```

Multiple actions occurred internally.

---

# The Four Core Components

Most agents contain four major components.

---

# Component 1 — Reasoning

Responsible for:

```plaintext
Understanding Goal
```

Examples:

```plaintext
What Is The User Trying To Achieve?

What Information Is Missing?

Which Tool Should Be Used?
```

The LLM typically performs this role.

---

# Component 2 — Tools

Responsible for:

```plaintext
Taking Action
```

Examples:

```plaintext
APIs

Databases

Cloud Platforms

Search Systems

Enterprise Applications
```

Without tools:

Agents remain largely informational.

---

# Component 3 — Memory

Responsible for:

```plaintext
Retaining Context
```

Examples:

```plaintext
Conversation History

Preferences

Past Actions

Retrieved Information
```

We will explore this in detail later.

---

# Component 4 — Orchestration

Responsible for:

```plaintext
Managing Workflow
```

Examples:

```plaintext
When To Call Tools

When To Stop

How To Recover

How To Retry
```

This often lives outside the LLM.

---

# The Hidden Reality

Many people imagine:

```plaintext
Agent
=
Very Smart Model
```

Reality:

```plaintext
Agent
=
System Architecture
```

The surrounding platform often matters more than the model itself.

---

# Agent Versus Workflow

This is a critical distinction.

---

## Workflow

Predefined:

```plaintext
Step 1
        ↓
Step 2
        ↓
Step 3
```

Always identical.

---

## Agent

Dynamic:

```plaintext
Goal
        ↓
Determine Steps
        ↓
Execute
```

The path may change.

---

# Infrastructure Analogy

Think of:

```plaintext
Workflow
```

as:

```plaintext
Terraform Plan
```

Predetermined.

---

Think of:

```plaintext
Agent
```

as:

```plaintext
Cloud Engineer
```

given an objective.

The path may vary depending on circumstances.

---

# Why Enterprises Care

Enterprise work is often:

```plaintext
Semi-Structured
```

Not fully predictable.

Examples:

```plaintext
Incident Response

Customer Support

Architecture Reviews

Employee Onboarding

Operational Troubleshooting
```

These tasks require judgment.

Agents attempt to automate parts of that judgment.

---

# Why Agents Are Expensive

Recall Chapter 3:

```plaintext
Inference Costs Money
```

Agents often perform:

```plaintext
Multiple Inference Cycles
```

instead of one.

Example:

```plaintext
Think
        ↓
Tool
        ↓
Think
        ↓
Tool
        ↓
Think
```

Costs can grow quickly.

This is one reason agent economics matter.

---

# Why Observability Becomes Critical

Agent behavior can be difficult to predict.

Questions emerge:

```plaintext
Why Did The Agent Choose That Tool?

Why Did It Fail?

How Many Steps Did It Execute?
```

This makes observability even more important than in traditional AI systems.

---

# The Evolution Of AI Architecture

The industry is gradually moving through:

```plaintext
Models
        ↓
RAG Systems
        ↓
Agents
```

Each stage introduces:

```plaintext
More Capability

More Complexity
```

This tradeoff is unavoidable.

---

# Common Misconceptions

## Misconception 1

### Agents are just chatbots.

Reality:

Agents perform reasoning, planning, and actions beyond simple response generation.

---

## Misconception 2

### Agents are autonomous humans.

Reality:

Agents are software systems operating within defined constraints.

---

## Misconception 3

### Agents require special models.

Reality:

Many agents use the same LLMs used in chat systems.

---

## Misconception 4

### The model is the agent.

Reality:

The model is usually only one component within a larger agent architecture.

---

# The Bigger Architectural Realization

Agents represent a shift from:

```plaintext
Generating Information
```

to:

```plaintext
Executing Objectives
```

This introduces entirely new architectural concerns:

- tools,
- memory,
- orchestration,
- governance,
- observability,
- security.

The challenge is no longer:

```plaintext
Can The Model Answer?
```

The challenge becomes:

```plaintext
Can The System Accomplish The Goal?
```

---

# Foundational Takeaway

An agent fundamentally provides:

> A system that uses reasoning, tools, memory, and execution logic to pursue goals and perform actions beyond simple response generation.

The LLM supplies intelligence.

The surrounding architecture supplies capability.

Together they transform AI from:

> A conversational assistant

into:

> A goal-oriented system capable of participating in work.

---

[⬅ Series Home](index.md) | [⬅From Chatbots to Agents](01-from-chatbots-to-agents.md) | [Planning and Reasoning➡](03-planning-and-reasoning.md)