---
layout: default
title: Strategy in Practice
---

# Phase 1 – Strategy in Practice

## Engagement Context

The cloud transformation engagement began with ACME Corp defining a broad objective:

> “Migrate all workloads to cloud to improve agility and reduce cost.”

At a high level, the objective appeared reasonable.

However, early discovery activities revealed that:
- workload priorities were unclear
- migration assumptions were overly broad
- compliance implications were not fully understood
- operational readiness was immature

The Strategy phase therefore focused on transforming broad intent into structured direction.

---

# Initial Understanding

At the start of the engagement, leadership expectations centered around:
- accelerating digital delivery
- reducing infrastructure management overhead
- improving scalability
- modernizing operational processes

There was also a strong perception that cloud adoption would:
- automatically reduce cost
- simplify operations
- accelerate application delivery

However, these expectations were not yet aligned to:
- workload realities
- compliance obligations
- operational maturity
- organizational readiness

---

# Discovery Activities

The Strategy phase was executed through:
- stakeholder workshops
- architecture discovery sessions
- operational reviews
- business alignment discussions
- compliance and risk assessments

The objective was not simply to gather information.

The objective was to:
- uncover assumptions
- identify constraints
- expose gaps
- align business and technology direction

---

# What We Discovered

## 1. Business Misalignment

Different regions and business units had different transformation priorities.

### Examples

| Region / Team | Primary Priority |
|---|---|
| Europe | Regulatory compliance |
| North America | Faster digital delivery |
| Operations Teams | Stability and risk reduction |
| Digital Teams | Agility and modernization |

### Key Observation

There was no shared definition of:
- transformation success
- modernization scope
- migration priorities

### Impact

Without alignment, cloud adoption risked becoming:
- fragmented
- inconsistent
- politically driven

rather than strategically coordinated.

---

## 2. Incomplete Application Visibility

The organization lacked a reliable understanding of its application landscape.

### Key Challenges

- No centralized application inventory
- Duplicate workloads across regions
- Unknown application dependencies
- Legacy middleware not fully documented
- Operational ownership inconsistencies

### Example

Several downstream reporting systems were tightly coupled to core banking platforms without formal documentation.

This significantly increased:
- migration risk
- sequencing complexity
- operational uncertainty

### Key Observation

Applications were assumed to be well understood internally.

In reality, operational knowledge was fragmented across teams and regions.

---

## 3. Compliance Complexity

Regulatory requirements existed across multiple dimensions:
- region
- workload type
- operational process
- data sensitivity

### Examples

| Workload Type | Regulatory Drivers |
|---|---|
| Payment Platforms | PCI-DSS |
| Financial Reporting | SOX |
| Customer Applications | GDPR |
| Core Banking Systems | FFIEC and operational resilience requirements |

### Key Challenge

Compliance existed as isolated organizational knowledge rather than integrated architectural guidance.

There was:
- no workload-to-compliance mapping
- no standardized control alignment
- no clarity on enforcement models in cloud environments

### Impact

This created uncertainty around:
- workload placement
- network isolation
- identity controls
- audit requirements
- operational governance

---

## 4. Operational Readiness Gaps

The organization had limited operational maturity for cloud environments.

### Key Challenges

- Heavy reliance on manual processes
- Limited automation adoption
- Minimal Infrastructure as Code usage
- Undefined cloud operating model
- Limited cloud operations experience

### Key Observation

Cloud adoption was initially viewed primarily as:
- infrastructure migration

rather than:
- operational transformation

### Impact

Without operational readiness improvements, migration alone would not deliver the expected agility benefits.

---

# Key Strategic Realization

The engagement revealed that the primary challenge was not simply moving workloads to cloud.

The deeper challenge involved:
- understanding workload dependencies
- aligning architecture to compliance
- establishing operational ownership
- balancing modernization with stability
- defining realistic migration priorities

---

# Strategic Decisions Made

## Decision 1 – Not All Workloads Would Move

Initial assumptions favored broad migration.

However, detailed analysis showed that some workloads should:
- remain on-premises temporarily
- be modernized incrementally
- be retained due to regulatory or operational constraints

### Example

Certain core banking systems remained retained because:
- operational stability requirements were extremely high
- dependencies were poorly understood
- recovery expectations exceeded current modernization readiness

### Impact

The transformation focus shifted from:
- migration volume

to:
- business-aligned workload prioritization

---

## Decision 2 – Introduce Workload Segmentation

Applications were grouped into operational categories.

### Example Segments

| Segment | Characteristics |
|---|---|
| Digital Workloads | Higher agility, customer-facing |
| Regulated Workloads | Compliance-driven controls |
| Core Banking Systems | Stability and resilience focused |

### Impact

This segmentation influenced:
- migration strategy
- governance controls
- network architecture
- operational ownership
- modernization priorities

---

## Decision 3 – Map Workloads to Compliance Requirements

Compliance controls were aligned directly to workload categories.

### Example

| Workload Type | Architectural Impact |
|---|---|
| PCI-DSS Workloads | Network isolation and restricted access |
| GDPR Applications | Regional deployment controls |
| SOX Systems | Centralized logging and auditability |

### Impact

Compliance transitioned from:
- generalized governance discussions

to:
- architecture-driving operational requirements

---

## Decision 4 – Define Realistic Business Outcomes

Transformation goals were refined into measurable operational objectives.

### Examples

- Reduce environment provisioning from weeks to hours
- Accelerate release cycles for digital applications
- Improve compliance visibility
- Increase deployment consistency
- Establish scalable operational governance

### Impact

This created clearer alignment between:
- business expectations
- architecture decisions
- operational priorities

---

## Decision 5 – Establish Operating Model Direction

The organization moved toward a shared platform operating model.

### Model Direction

| Responsibility | Ownership |
|---|---|
| Platform Governance | Central platform team |
| Workload Ownership | Application teams |
| Compliance Enforcement | Shared governance model |

### Impact

This established the foundation for:
- landing zone governance
- operational accountability
- scalable cloud operations

---

# What Changed During Strategy

| Initial Assumption | Strategic Reality |
|---|---|
| All workloads will move to cloud | Workload prioritization is required |
| Compliance is a separate activity | Compliance shapes architecture directly |
| Cloud automatically reduces cost | Optimization requires operational maturity |
| Applications are fully understood | Significant visibility gaps exist |
| Strategy is a one-time exercise | Strategy evolves continuously |

---

# Key Insight

The Strategy phase transformed cloud adoption from:
- broad migration ambition

into:
- workload-aware
- compliance-aware
- operationally aligned
- risk-conscious transformation planning

The most important outcome was not technical architecture.

It was establishing organizational clarity around:
- priorities
- constraints
- responsibilities
- transformation direction

---

# Outputs of the Strategy Phase

At the end of the Strategy phase, ACME Corp had:

- Defined business objectives
- Identified workload categories
- Established workload prioritization direction
- Mapped compliance requirements to workloads
- Identified operational readiness gaps
- Established initial operating model direction
- Identified major architectural and governance constraints

---

# Transition to Planning in Practice

With strategic direction established, the engagement moved into the Planning phase.

The next challenge was transforming strategic intent into:
- application-level decisions
- migration sequencing
- dependency-aware planning
- governance-aligned execution models

This is where high-level direction would encounter the complexity of the actual enterprise estate.

---

[⬅ Series Home](index.md) | [Next➡](plan-in-practice.md)