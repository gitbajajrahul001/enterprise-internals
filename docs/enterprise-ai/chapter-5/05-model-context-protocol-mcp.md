---
layout: default
title: Model Context Protocol (MCP)
parent: Chapter 05 — Agents and Tool Use
nav_order: 5
---

# Model Context Protocol (MCP)

> Understanding the emerging standard that allows AI systems to connect to tools, data sources, and services through a common interface instead of requiring custom integrations for every application.

---

# Why This Topic Matters

In the previous chapter we learned:

```plaintext
LLM
        ↓
Function Call
        ↓
Tool
        ↓
Result
```

This allows agents to:

- query databases,
- create tickets,
- provision infrastructure,
- retrieve documents,
- interact with APIs.

However, a major problem quickly emerges.

Imagine an enterprise wants AI to interact with:

```plaintext
Azure

AWS

GitHub

ServiceNow

Jira

Confluence

SharePoint

Databases

Monitoring Platforms
```

Without a standard approach:

Every integration becomes:

```plaintext
Custom Development
```

This creates a scalability problem.

---

# The Historical Problem

Before MCP, most AI integrations looked like:

```plaintext
Tool A
        ↓
Custom Connector

Tool B
        ↓
Custom Connector

Tool C
        ↓
Custom Connector
```

Every tool required:

- custom APIs,
- custom authentication,
- custom schemas,
- custom maintenance.

The number of integrations grows rapidly.

---

# Infrastructure Analogy

Think about networking.

Before standard protocols:

```plaintext
Every Vendor
=
Different Communication Method
```

Interoperability becomes difficult.

Standards such as:

```plaintext
TCP/IP
HTTP
DNS
```

solved this problem.

MCP attempts something similar for AI systems.

---

# The Core Question

How can an agent interact with:

```plaintext
Thousands Of Different Tools
```

without needing:

```plaintext
Thousands Of Different Integrations?
```

This is the problem MCP attempts to solve.

---

# What Is MCP?

MCP stands for:

# Model Context Protocol

At a high level:

> MCP is a standardized way for AI systems to discover, understand, and interact with external tools and resources.

Think of MCP as:

```plaintext
A Universal Connector Framework
```

for AI.

---

# The Simplified Vision

Without MCP:

```plaintext
Agent
        ↓
Custom Integration A

Agent
        ↓
Custom Integration B

Agent
        ↓
Custom Integration C
```

---

With MCP:

```plaintext
Agent
        ↓
MCP

        ↓

Tool A

Tool B

Tool C
```

The integration model becomes significantly simpler.

---

# Important Mental Model

Function calling answers:

```plaintext
How Does The Model Request An Action?
```

MCP answers:

```plaintext
How Does The Agent Discover
And Understand Available Actions?
```

These are related but different concerns.

---

# Human Analogy

Imagine hiring a new employee.

Without documentation:

```plaintext
Every System Must Be Explained Manually
```

The employee constantly asks:

```plaintext
What Can This System Do?

How Do I Use It?

What Inputs Are Required?
```

---

Now imagine every system provides:

```plaintext
Self-Describing Documentation
```

The employee can immediately understand:

- capabilities,
- inputs,
- outputs,
- constraints.

MCP aims to provide this experience for AI systems.

---

# Why Agents Need Discovery

Consider an agent connected to:

```plaintext
ServiceNow
```

Questions emerge:

```plaintext
Can I Create Tickets?

Can I Update Tickets?

Can I Close Tickets?

What Fields Are Required?
```

Without discovery mechanisms:

Every capability must be hardcoded.

This becomes difficult to scale.

---

# MCP's Core Idea

Instead of:

```plaintext
Agent Knows Everything
```

the model can discover:

```plaintext
Available Tools

Available Resources

Available Actions
```

through a common protocol.

---

# Think About USB

A useful analogy:

Before USB:

```plaintext
Different Device
=
Different Connector
```

After USB:

```plaintext
Common Interface
```

Devices remain different.

The connection model becomes standardized.

MCP attempts something similar.

---

# The Three Major Concepts

Most MCP discussions revolve around three concepts.

---

# Resources

Resources provide:

```plaintext
Information
```

Examples:

```plaintext
Documents

Files

Knowledge Bases

Configuration Data

Records
```

Resources are generally:

```plaintext
Read-Oriented
```

---

# Tools

Tools provide:

```plaintext
Actions
```

Examples:

```plaintext
Create Ticket

Deploy Application

Restart Service

Send Email
```

Tools perform work.

---

# Prompts

Some MCP implementations also expose:

```plaintext
Reusable Prompt Templates
```

that agents can leverage.

These help standardize interactions.

---

# A Simplified Architecture

Conceptually:

```plaintext
Agent
        ↓
MCP Client
        ↓
MCP Server
        ↓
Resources

Tools

Prompts
```

The agent no longer needs to understand every implementation detail.

---

# Why This Matters For Enterprises

Large organizations may have:

```plaintext
Hundreds

Thousands

Tens Of Thousands
```

of systems.

Examples:

```plaintext
HR Systems

ITSM Platforms

Cloud Platforms

Databases

Knowledge Repositories

Monitoring Tools
```

Building bespoke integrations for all of them becomes expensive.

---

# MCP And Tool Discovery

Without MCP:

Developers often manually define:

```plaintext
Available Tools
```

inside applications.

---

With MCP:

Tools can describe themselves.

Example:

```plaintext
Tool:
Create ServiceNow Ticket

Required Inputs:
Title
Description
Priority
```

The agent can discover this dynamically.

---

# Why This Is Powerful

Notice what happens.

The AI system becomes less dependent on:

```plaintext
Hardcoded Knowledge
```

about integrations.

Instead:

```plaintext
Capabilities Become Discoverable
```

This improves flexibility.

---

# MCP Does Not Replace APIs

This is important.

MCP is not replacing:

```plaintext
REST APIs

GraphQL APIs

SDKs
```

These still exist.

MCP sits above them.

Think of it as:

```plaintext
AI-Friendly Abstraction
```

rather than an infrastructure replacement.

---

# Infrastructure Analogy

Consider:

```plaintext
Kubernetes
```

Kubernetes did not eliminate:

```plaintext
Linux

Networking

Storage
```

It introduced:

```plaintext
A Standard Control Layer
```

MCP attempts something similar for AI integrations.

---

# Why MCP Is Receiving Attention

The industry increasingly believes:

```plaintext
Agents Will Need Many Tools
```

and

```plaintext
Many Agents Will Need The Same Tools
```

A common integration model therefore becomes attractive.

---

# Enterprise Example

Imagine:

```plaintext
Azure MCP Server

ServiceNow MCP Server

GitHub MCP Server

Confluence MCP Server
```

An agent can interact with each through a consistent protocol.

The underlying systems remain different.

The interaction model becomes standardized.

---

# Why Architects Should Care

For architects, MCP is not primarily about AI.

It is about:

```plaintext
Standardization
```

The industry has repeatedly benefited from:

```plaintext
Common Protocols
```

Examples:

```plaintext
HTTP

DNS

SMTP

TCP/IP
```

MCP represents an attempt to create a similar standardization layer for AI systems.

---

# Current Reality

It is important to understand:

```plaintext
MCP Is Emerging
```

not:

```plaintext
Mature And Universal
```

The ecosystem is evolving rapidly.

Standards, implementations, and adoption patterns continue to develop.

---

# Common Misconceptions

## Misconception 1

### MCP is an AI model.

Reality:

MCP is a protocol for connecting AI systems to external capabilities.

---

## Misconception 2

### MCP replaces APIs.

Reality:

MCP typically sits on top of existing APIs.

---

## Misconception 3

### MCP is required for agents.

Reality:

Agents can exist without MCP.

MCP simply standardizes integration.

---

## Misconception 4

### MCP makes integrations automatic.

Reality:

Systems still need MCP-compatible implementations.

---

# The Bigger Architectural Realization

The AI industry is gradually moving from:

```plaintext
Model-Centric Architectures
```

toward:

```plaintext
Ecosystem Architectures
```

where agents interact with:

- tools,
- knowledge sources,
- services,
- enterprise platforms.

As this ecosystem grows:

```plaintext
Standardization
```

becomes increasingly valuable.

This is the environment in which MCP emerged.

---

# Foundational Takeaway

Model Context Protocol (MCP) fundamentally provides:

> A standardized way for AI systems to discover and interact with tools, resources, and services through a common interface.

Its goal is not to make models smarter.

Its goal is to make integrations simpler, more reusable, and more scalable.

In the long term:

> MCP has the potential to become for AI integrations what HTTP became for web applications—a common language that enables interoperability across an increasingly complex ecosystem.

---

[⬅ Series Home](index.md) | [⬅Tools and Function Calling](04-tools-and-function-calling.md) | [Agent Memory➡](06-agent-memory.md)