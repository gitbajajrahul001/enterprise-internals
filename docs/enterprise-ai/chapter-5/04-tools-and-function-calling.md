---
layout: default
title: Tools and Function Calling
parent: Chapter 05 — Agents and Tool Use
nav_order: 4
---

# Tools and Function Calling

> Understanding how AI systems interact with external applications, APIs, databases, and services, transforming language models from information providers into action-capable systems.

---

# Why This Topic Matters

In previous chapters we learned:

```plaintext
LLMs Generate Text
```

This is important.

But also limiting.

Consider these requests:

```plaintext
Create a ServiceNow ticket.

Provision an Azure VM.

Restart a Kubernetes pod.

Send an email.

Query a database.
```

A standard LLM cannot perform any of these actions.

It can only explain:

```plaintext
How To Do Them
```

This creates a major limitation.

For AI to become operationally useful, it must interact with systems outside itself.

This is where:

# Tools

and

# Function Calling

enter the picture.

---

# The Fundamental Limitation Of LLMs

Recall:

A Large Language Model fundamentally performs:

```plaintext
Input Tokens
        ↓
Prediction
        ↓
Output Tokens
```

Everything it does ultimately becomes:

```plaintext
Text Generation
```

Even when the output appears intelligent.

---

# Important Realization

An LLM cannot:

```plaintext
Create A VM

Query ServiceNow

Access GitHub

Read Databases

Send Emails
```

unless additional capabilities are provided.

The model itself has no direct access to external systems.

---

# Human Analogy

Imagine hiring a consultant.

The consultant possesses:

```plaintext
Knowledge
```

but no:

```plaintext
Laptop

Phone

System Access
```

They can advise.

They cannot act.

Tools provide the equivalent of:

```plaintext
Hands
```

for AI systems.

---

# What Is A Tool?

A tool is:

> Any external capability that an AI system can invoke to perform an action or retrieve information.

Examples:

```plaintext
API

Database Query

Search Engine

Cloud Platform

Monitoring System

Email System

Ticketing Platform
```

All are tools from an agent's perspective.

---

# Examples Of Common Tools

---

## Search Tool

```plaintext
Search Documentation
```

---

## Database Tool

```plaintext
Query Records
```

---

## Email Tool

```plaintext
Send Email
```

---

## Azure Tool

```plaintext
Create Resources
```

---

## ServiceNow Tool

```plaintext
Create Tickets
```

---

## GitHub Tool

```plaintext
Create Pull Requests
```

---

The specific technology is less important than the pattern.

---

# The Traditional Chatbot Flow

Without tools:

```plaintext
User
        ↓
LLM
        ↓
Text Response
```

The interaction ends.

---

# The Tool-Enabled Flow

With tools:

```plaintext
User
        ↓
LLM
        ↓
Tool Decision
        ↓
Tool Execution
        ↓
Result
        ↓
LLM
        ↓
Final Response
```

This architecture is fundamentally different.

---

# Example — Weather Request

User:

```plaintext
What is the weather in London?
```

---

Without tools:

The model relies on:

```plaintext
Training Knowledge
```

which may be outdated.

---

With tools:

```plaintext
User
        ↓
Weather Tool
        ↓
Current Data
        ↓
Response
```

The answer becomes current.

---

# Example — Azure Operations

User:

```plaintext
Create a VM called app-server-01.
```

---

Without tools:

```plaintext
Instructions Only
```

---

With tools:

```plaintext
Determine Intent
        ↓
Call Azure API
        ↓
Create VM
        ↓
Return Result
```

Now an action occurs.

---

# The Key Question

How does the model know:

```plaintext
Which Tool To Use?
```

This is where:

# Function Calling

becomes important.

---

# What Is Function Calling?

Function calling is:

> A structured mechanism that allows a model to request the execution of a specific tool.

Instead of generating:

```plaintext
Natural Language
```

the model may generate:

```plaintext
Structured Action Request
```

Conceptually:

```plaintext
Call Function:
CreateVM

Parameters:
Name=app-server-01
Region=EastUS
```

The platform then executes the function.

---

# Important Mental Model

The model does NOT directly execute tools.

The model typically:

```plaintext
Requests Tool Usage
```

The surrounding platform performs:

```plaintext
Actual Execution
```

This distinction is critical.

---

# The Hidden Architecture

What appears to users as:

```plaintext
One AI Response
```

may internally look like:

```plaintext
User Request
        ↓
LLM
        ↓
Function Call Request
        ↓
Tool Execution
        ↓
Result
        ↓
LLM
        ↓
Final Response
```

Multiple steps occur behind the scenes.

---

# Why Structured Function Calls Matter

Imagine a model generating:

```plaintext
Please create a VM named app-server-01.
```

A platform cannot reliably execute this.

Natural language is ambiguous.

---

Instead:

```plaintext
{
  action: create_vm,
  name: app-server-01,
  region: eastus
}
```

provides structured intent.

Systems can execute this safely.

---

# Why Function Calling Changed Everything

Before function calling:

```plaintext
Models Generated Text
```

After function calling:

```plaintext
Models Could Trigger Actions
```

This was a major breakthrough.

It enabled:

- agents,
- copilots,
- automation assistants,
- operational AI systems.

---

# Tool Selection

Modern agents may have access to:

```plaintext
Azure

AWS

ServiceNow

Jira

GitHub

Databases

Monitoring Systems
```

The model must determine:

```plaintext
Which Tool Is Appropriate?
```

This becomes a reasoning problem.

---

# Example

User:

```plaintext
Create an incident ticket.
```

Agent may reason:

```plaintext
Need Ticket System
        ↓
Use ServiceNow Tool
```

---

User:

```plaintext
Create a repository.
```

Agent may reason:

```plaintext
Need Source Control
        ↓
Use GitHub Tool
```

Tool selection becomes part of agent intelligence.

---

# Why Multiple Tools Matter

Many tasks require:

```plaintext
More Than One Tool
```

Example:

```plaintext
Investigate Production Incident
```

Potential workflow:

```plaintext
Query Monitoring Tool
        ↓
Review Logs
        ↓
Create Ticket
        ↓
Notify Team
```

The agent orchestrates several tools.

---

# Tool Chaining

This pattern is called:

# Tool Chaining

Conceptually:

```plaintext
Tool A
        ↓
Tool B
        ↓
Tool C
```

where outputs from one tool become inputs for another.

This is common in enterprise workflows.

---

# Why Security Becomes Critical

Tools introduce risk.

A chatbot generating text is relatively safe.

A tool-enabled agent may:

```plaintext
Create Resources

Delete Resources

Send Emails

Modify Records
```

The consequences become much larger.

---

# Enterprise Concerns

Organizations immediately ask:

```plaintext
Who Approved This Action?

What Permissions Exist?

What Can The Agent Access?

What Happens If It Makes A Mistake?
```

These questions are valid.

Tool-enabled agents require strong governance.

---

# Read-Only vs Action Tools

Not all tools are equal.

---

## Read-Only Tools

Examples:

```plaintext
Search

Monitoring

Database Queries
```

Low risk.

---

## Action Tools

Examples:

```plaintext
Create VM

Delete Resource

Send Email

Modify Records
```

Higher risk.

Most organizations treat these differently.

---

# Why Human Approval Exists

Many enterprise agents operate like:

```plaintext
Plan
        ↓
Request Approval
        ↓
Execute
```

This pattern is known as:

```plaintext
Human-In-The-Loop
```

which we will cover later.

---

# Why This Feels Familiar

For automation professionals:

Function calling resembles:

```plaintext
API Invocation
```

combined with:

```plaintext
Decision Logic
```

The difference is that the decision logic is increasingly powered by LLMs.

---

# The Emerging Architecture

Modern agents increasingly resemble:

```plaintext
LLM
        ↓
Reasoning Layer
        ↓
Tool Selection
        ↓
Function Calls
        ↓
Execution Layer
        ↓
External Systems
```

This architecture is becoming standard.

---

# Common Misconceptions

## Misconception 1

### The model executes tools directly.

Reality:

The platform executes tools after receiving a function call request.

---

## Misconception 2

### Tools are only APIs.

Reality:

Any external capability can function as a tool.

---

## Misconception 3

### Function calling is an agent.

Reality:

Function calling is one capability used by agents.

---

## Misconception 4

### Tool access guarantees useful actions.

Reality:

Reasoning and planning remain critical.

---

# The Bigger Architectural Realization

Function calling introduced something transformative:

```plaintext
Language
        ↓
Action
```

The model no longer simply describes work.

It can participate in work.

This capability forms the foundation of:

- agents,
- copilots,
- AI automation,
- operational AI platforms.

---

# Foundational Takeaway

Tools provide external capabilities that allow AI systems to interact with applications, services, and infrastructure.

Function calling provides the structured mechanism through which models request those capabilities.

Together they transform AI from:

> A system that explains actions

into:

> A system that can initiate and orchestrate actions across the enterprise.

---

[⬅ Series Home](index.md) | [⬅Planning and Reasoning](03-planning-and-reasoning.md) | [Model Context Protocol (MCP)➡](05-model-context-protocol-mcp.md)