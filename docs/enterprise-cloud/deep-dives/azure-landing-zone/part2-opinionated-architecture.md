---

layout: default
title: Opinionated Architecture

---

# 🧭 What is an Opinionated Target Architecture?

### _And Why You Actually Need It_

In Part 1, we saw why Landing Zones fail.

Not because Azure is complex.  
Not because tools are missing.

But because:

> Too many decisions are left undefined.

* * *

## The Problem Nobody Talks About

When teams start designing a Landing Zone, they face hundreds of decisions:

*   How many management groups?
*   Hub-spoke or vWAN?
*   Public access allowed or not?
*   One subscription per app or per environment?
*   Central firewall or distributed?
*   How to handle identity?
*   How to enforce policies?

And what usually happens?

> Every team answers these differently.


### **The Result**

*   inconsistent architectures
*   security gaps
*   cost inefficiencies
*   constant rework
*   endless exceptions

* * *

## So What Do You Do?


You remove ambiguity.

You don’t let every team decide everything.

You define:

> An Opinionated Target Architecture that is a predefined, strongly guided design that enforces how cloud must be built — not just how it can be built.


* * *

### 🔥 Key Idea

It does NOT say:

> “Here are some options”

It says:

> “This is how we will build — unless there is a justified exception”

* * *

## 🧠 Why This Matters (Real World)

In a bank like yours, if you allow flexibility everywhere:

*   One team exposes services publicly
*   Another uses private endpoints
*   One uses central logging
*   Another skips it
*   One tags resources
*   Another doesn’t

👉 Within months:

> You don’t have a cloud platform — you have chaos at scale

* * *

## 🔒 What an Opinionated Architecture Enforces

### **1\. Structure**

*   Fixed Management Group hierarchy
*   Defined subscription model
*   Clear separation of platform vs workloads

* * *

### **2\. Networking Pattern**


*   Hub-spoke (or chosen model)
*   Centralized ingress/egress
*   Private-first connectivity

* * *

### **3\. Security Baseline**

*   No public IP by default
*   Encryption enforced
*   Defender enabled
*   Logging mandatory

* * *

### **4\. Identity Model**

*   Centralized identity
*   RBAC patterns
*   PIM enforced

* * *

### **5\. Governance**

*   Mandatory tagging
*   Policy-driven control
*   Budget and cost visibility

* * *

### **6\. Deployment Model**

*   Infrastructure as Code only
*   Standard pipelines
*   No manual provisioning

* * *

### **⚖️ Important: It’s Not About Control — It’s About Consistency**

This is where many people misunderstand. Opinionated architecture is NOT:

*   blocking teams
*   slowing innovation
*   enforcing rigidity

It is:

> Creating a safe, predictable, and scalable foundation

* * *

## 🔁 Real-world Example

### **Without Opinionated Architecture**

Team A:

*   builds VNet with open access
*   deploys without tags

Team B:

*   uses private endpoints
*   enforces policies

Team C:

*   uses different naming
*   no logging

👉 Result: No standard. No control. No audit readiness.

* * *

### **With Opinionated Architecture**

All teams:

*   use same network pattern
*   inherit same policies
*   follow same naming
*   send logs to same system

👉 Result:

*   faster deployments
*   easier operations
*   consistent security
*   predictable cost

* * *

## 🔥 The Architect’s Role

As an architect, your job is NOT to:

*   design one system

Your job is to:

> Define how ALL systems will be designed

That is what an opinionated architecture does.

* * *

## ⚠️ The Balance You Must Maintain

Too opinionated:

*   teams get blocked
*   innovation slows

Too flexible:

*   governance fails
*   cost explodes

👉 The goal is:

> Controlled flexibility

* * *

## What Comes Next

Now that you understand _why_ and _what_…

We move into the most critical part:

> Designing the Azure Landing Zone — step by step

---

[⬅ Back to Series Home](index.md) |  [⬅ Back to: Opinionated Architecture](part2-opinionated-architecture.md)| [Next: Management Group Design ➡](part3-management-groups.md)
