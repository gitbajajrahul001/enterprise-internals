---

layout: default
title: Designing Management Group

---


# 🏗️ Designing Management Group Hierarchy

### _Where Governance Actually Starts_

Most people think Management Groups are just:

> “folders to organize subscriptions”

That thinking is wrong.

* * *

## 🔥 What Management Groups Really Are

> Management Groups define governance boundaries — not structure for convenience

They control:

*   Policy inheritance
*   Access control (RBAC)
*   Compliance enforcement
*   Operational separation

* * *

## ❌ The Wrong Way to Design MGs

### 1\. Designing based on teams

1) Finance  
2) HR  
3) Retail Banking
4) etc..

👉 Problem:

*   teams change
*   org structures evolve
*   governance breaks

* * *

### 2\. Designing based on applications

App1  
App2  
App3

👉 Problem:

*   not scalable
*   no policy grouping
*   no governance value

***

✅ The Right Way

Design based on:

> Control boundaries that will remain stable over time

* * *

# 🧠 The 3 Core Dimensions You Must Think In

Before drawing anything, answer:

* * *

## 1\. Governance & Policy Boundaries

*   Where do policies differ?
*   Where do controls change?

Example:

*   PCI vs Non-PCI
*   Regulated vs Non-regulated

* * *

## 2\. Platform vs Workloads

Separate:

*   Platform (shared services)
*   Landing Zones (applications)

👉 This is non-negotiable in enterprise design

* * *

## 3\. Lifecycle & Risk Segmentation

*   Production vs Non-production
*   Sandbox vs Controlled environments
*   Quarantine / Decommission

* * *

# 🏦 Realistic Enterprise Structure

Here’s a practical starting point:

```text
Tenant Root  
│  
├── Platform  
│   ├── Identity  
│   ├── Connectivity  
│   └── Management-Security  
│  
├── Landing Zones  
│   ├── Regulated  
│   │   ├── PCI  
│   │   ├── GDPR  
│   │   └── Core-Banking  
│   │  
│   ├── Non-Regulated  
│   │   ├── Production  
│   │   └── Non-Production  
│   │  
│   └── Sandbox  
│  
├── Transitional  
│   ├── Quarantine  
│   └── Decommissioning
```

* * *

# 🔍 Why This Structure Works

## Platform is isolated

*   Central ownership
*   High control
*   No workload noise

* * *

## Landing Zones are structured by risk

*   Regulated workloads inherit stricter policies
*   Non-regulated get more flexibility

* * *

## Sandbox is isolated

*   innovation allowed
*   risk contained

* * *

## Transitional zones exist

*   handle real-world mess
*   not everything is clean

* * *

# ⚠️ Key Design Decisions You Must Make

**Decision 1: Where do policies differ?**

👉 This defines your MG split

**Decision 2: What is centrally controlled?**

👉 Platform vs workload separation

**Decision 3: Where do you expect exceptions?**

👉 Plan for:

*   sandbox
*   quarantine
*   temporary states

* * *

# 🔥 Real-World Mistake

Most teams do this:

> “Let’s copy Microsoft’s reference architecture exactly”

Problem:

*   It’s generic
*   Your bank is not generic
*   Your constraints are different

* * *

# 🧠 Architect Thinking

You don’t ask:

> “What is the correct MG structure?”

You ask:

> “Where do I need different control behavior?”

* * *

## 🔁 Example (Important)

### If PCI needs:

*   no public IP
*   restricted regions
*   strict logging

👉 It must be a separate MG

* * *

### If Dev vs Prod:

*   same policies
*   different access

👉 Don’t create MG — use subscription/RBAC

* * *

### 💡 One-Line Rule

> Create a new Management Group only when policy or governance needs to change significantly

* * *

## Where Most People Go Wrong

*   Too many MGs → complexity
*   Too few MGs → no control

#### Now that MG structure is clear, the next logical step is:

👉 Subscription Design Strategy

Because:

> MG defines governance  
> Subscription defines ownership, cost, and deployment boundary

* * *


[⬅ Back to Series Home](index.md) |  [⬅ Back to: Why Landing Zones Fail](part1-why-landing-zones-fail.md) | [Next: Subscription Design ➡](part4-subscriptions.md)
