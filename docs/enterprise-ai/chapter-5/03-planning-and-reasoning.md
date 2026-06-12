---
layout: default
title: Planning and Reasoning
parent: Chapter 05 — Agents and Tool Use
nav_order: 3
---

# Planning and Reasoning

> Understanding how agents break down goals into executable steps and why reasoning is the foundation that transforms an LLM from a responder into a decision-making system.

---

# Why This Topic Matters

In the previous chapter we learned:

```plaintext
Agent
=
LLM
+
Tools
+
Memory
+
Orchestration
```

However, a critical question remains:

> How does an agent decide what to do?

Having access to tools is not enough.

Imagine giving someone:

- Azure access
- AWS access
- ServiceNow access
- Jira access
- GitHub access

Without a plan, those tools are useless.

The same is true for AI agents.

Before an agent can act, it must determine:

```plaintext
What Should Happen Next?
```

This capability is called:

# Planning and Reasoning

---

# The Fundamental Difference

Traditional automation follows:

```plaintext
Predefined Workflow
```

Example:

```plaintext
Step 1
        ↓
Step 2
        ↓
Step 3
```

Developers define every action.

---

Agents often operate differently.

Example:

```plaintext
Goal
        ↓
Determine Steps
        ↓
Execute
```

The path is not fully predetermined.

---

# Human Analogy

Imagine asking:

```plaintext
Organize a team offsite.
```

You do not specify:

```plaintext
Book Venue

Book Travel

Arrange Catering

Send Invites
```

The employee determines those tasks.

Agents attempt something similar.

---

# What Is Reasoning?

Reasoning is:

> The process of analyzing information and determining what actions should occur next.

Examples:

```plaintext
What Is The Goal?

What Information Is Missing?

What Tool Should Be Used?

What Step Should Come First?
```

Reasoning helps convert:

```plaintext
Objective
```

into:

```plaintext
Action
```

---

# What Is Planning?

Planning is:

> The process of decomposing a goal into smaller executable steps.

Example:

Goal:

```plaintext
Generate Weekly Operations Report
```

Potential plan:

```plaintext
Retrieve Incident Data
        ↓
Retrieve Change Data
        ↓
Analyze Metrics
        ↓
Generate Summary
        ↓
Distribute Report
```

The goal becomes a workflow.

---

# Important Mental Model

Reasoning answers:

```plaintext
What Should Happen?
```

Planning answers:

```plaintext
In What Order?
```

Together they create:

```plaintext
Execution Strategy
```

---

# Why Chatbots Rarely Need Planning

Consider:

```plaintext
What is Kubernetes?
```

The model simply:

```plaintext
Generate Answer
```

No planning required.

---

Now consider:

```plaintext
Investigate why application latency increased yesterday.
```

This requires:

```plaintext
Multiple Steps
```

The complexity changes dramatically.

---

# The Agent Planning Loop

Many agents operate like:

```plaintext
Goal
        ↓
Reason
        ↓
Create Plan
        ↓
Execute Step
        ↓
Review Result
        ↓
Update Plan
        ↓
Execute Next Step
```

This loop continues until completion.

---

# Example — Cloud Operations Agent

Goal:

```plaintext
Identify Failed VM Backups
```

Possible reasoning process:

```plaintext
Need Backup Data
        ↓
Need Monitoring Tool
        ↓
Query Monitoring System
        ↓
Review Results
        ↓
Identify Failures
        ↓
Generate Report
```

Notice:

The workflow was not hardcoded.

It was derived from the objective.

---

# Why Planning Matters

Without planning:

An agent may:

```plaintext
Call Wrong Tool

Skip Critical Steps

Repeat Work

Terminate Early
```

Planning creates structure.

---

# Infrastructure Analogy

Imagine building a datacenter.

Without planning:

```plaintext
Buy Servers
```

might happen before:

```plaintext
Power Design
```

which would be disastrous.

Planning ensures actions occur in a meaningful sequence.

Agents face similar challenges.

---

# Reactive vs Planned Agents

Not all agents plan equally.

---

# Reactive Agents

Operate as:

```plaintext
Observe
        ↓
Act
```

Minimal planning.

Example:

```plaintext
User Question
        ↓
Search
        ↓
Response
```

Simple.

Fast.

Limited.

---

# Planned Agents

Operate as:

```plaintext
Goal
        ↓
Plan
        ↓
Execute
        ↓
Revise Plan
```

More capable.

More expensive.

More complex.

---

# Why Multi-Step Reasoning Emerged

Many real-world tasks require:

```plaintext
Intermediate Decisions
```

Examples:

```plaintext
Troubleshooting

Research

Architecture Reviews

Root Cause Analysis

Financial Analysis
```

These tasks cannot always be solved in one inference step.

---

# Example — Architecture Review Agent

Goal:

```plaintext
Review Landing Zone Design
```

Potential reasoning:

```plaintext
Review Networking
        ↓
Review Security
        ↓
Review Governance
        ↓
Review Cost Controls
        ↓
Generate Findings
```

This resembles how a human architect would approach the task.

---

# Planning Is Often Imperfect

A common misconception:

```plaintext
Agent Creates Perfect Plan
```

Reality:

Agents often:

```plaintext
Miss Steps

Choose Poor Actions

Need Replanning
```

This is why agent systems frequently include:

```plaintext
Feedback Loops
```

---

# Replanning

Modern agents often revise plans as new information appears.

Example:

Initial plan:

```plaintext
Retrieve Server Logs
```

Result:

```plaintext
Logs Missing
```

New plan:

```plaintext
Use Monitoring Data Instead
```

The workflow adapts.

---

# Why This Feels Familiar

Infrastructure professionals already understand this pattern.

Consider:

```plaintext
Incident Response
```

Rarely follows:

```plaintext
Fixed Workflow
```

Instead:

```plaintext
Investigate
        ↓
Learn
        ↓
Adapt
        ↓
Proceed
```

Agent planning behaves similarly.

---

# The Cost Of Reasoning

Recall Chapter 3:

```plaintext
Inference Costs Money
```

Reasoning often requires:

```plaintext
Multiple Inference Cycles
```

Example:

```plaintext
Reason
        ↓
Plan
        ↓
Execute
        ↓
Reason Again
```

Every step consumes resources.

This is why agents can become expensive.

---

# Why Reasoning Models Emerged

The industry increasingly realized:

Some workloads require:

```plaintext
Deeper Thinking
```

than standard response generation.

This contributed to the rise of:

```plaintext
Reasoning Models
```

which we will revisit in later chapters.

---

# Planning And Tool Use

Planning becomes far more important when tools exist.

Without tools:

```plaintext
Wrong Plan
```

usually means:

```plaintext
Poor Answer
```

With tools:

```plaintext
Wrong Plan
```

may mean:

```plaintext
Wrong Action
```

The consequences become more significant.

---

# Why Governance Matters

As agents become capable of:

- provisioning resources,
- modifying systems,
- sending communications,
- executing workflows,

organizations increasingly require:

```plaintext
Approval Controls

Guardrails

Human Oversight
```

Planning without governance creates risk.

---

# Common Misconceptions

## Misconception 1

### Planning and reasoning are the same thing.

Reality:

Reasoning determines what should happen.

Planning determines how it should happen.

---

## Misconception 2

### Every agent plans.

Reality:

Many agents are reactive and perform minimal planning.

---

## Misconception 3

### Better tools eliminate planning needs.

Reality:

Tools increase the importance of planning.

---

## Misconception 4

### Agents always create optimal plans.

Reality:

Planning remains probabilistic and imperfect.

---

# The Bigger Architectural Realization

The transition from:

```plaintext
Answer Generation
```

to:

```plaintext
Goal Execution
```

requires a new capability layer.

That layer is:

```plaintext
Reasoning
        +
Planning
```

Without it:

Agents remain sophisticated chatbots.

With it:

Agents begin behaving like systems that can pursue objectives.

---

# Foundational Takeaway

Planning and reasoning fundamentally provide:

> The ability for an agent to analyze a goal, determine a sequence of actions, adapt to changing information, and decide what should happen next.

This capability transforms AI from:

```plaintext
Response Generation
```

into:

```plaintext
Goal-Oriented Execution
```

which is one of the defining characteristics of modern agentic systems.

---

[⬅ Series Home](index.md) | [⬅What Is an Agent?](02-what-is-an-agent.md) | [Tools and Function Calling➡](04-tools-and-function-calling.md)