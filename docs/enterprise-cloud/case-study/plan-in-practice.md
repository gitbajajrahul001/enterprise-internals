---
layout: default
title: Planning in Practice
---

# Phase 2 – Planning in Practice

## Engagement Context

With strategic direction established, ACME Corp moved into the Planning phase.

The organization now had:
- high-level workload segmentation
- initial compliance mapping
- defined business objectives
- operating model direction

However, these decisions still existed primarily at a conceptual level.

The Planning phase focused on converting strategic intent into:
- executable migration planning
- application-level decisions
- dependency-aware sequencing
- compliance-aware architecture direction

This was the stage where enterprise complexity became fully visible.

---

# Initial Planning Assumptions

At the beginning of the phase, the organization believed:
- the application landscape was broadly understood
- workloads could be grouped relatively easily
- migration sequencing would follow predictable waves
- compliance requirements could be enforced later during implementation

These assumptions changed significantly as detailed discovery progressed.

---

# What We Discovered

## 1. Application Inventory Expansion

The initial understanding of the application landscape proved incomplete.

### Initial Estimate

- Approximately 250 applications

### Actual Discovery

- More than 420 applications and supporting services

### Newly Identified Components

- Batch processing systems
- Reporting scripts
- Middleware services
- Shared authentication components
- Regional utility applications

### Key Observation

Many critical operational dependencies existed outside formally documented systems.

### Impact

The expanded inventory significantly increased:
- migration complexity
- sequencing requirements
- operational risk exposure
- governance scope

---

## 2. Hidden Dependency Complexity

Dependency analysis revealed tighter coupling between systems than initially expected.

### Examples

- Reporting systems depended directly on core banking services
- Payment platforms relied on legacy authentication infrastructure
- Shared middleware components supported multiple unrelated applications
- Regional systems depended on undocumented integrations

### Key Observation

Many dependencies were known operationally by teams but not documented architecturally.

### Impact

This complicated:
- migration sequencing
- outage risk management
- modernization planning
- rollback strategies

Dependency management became one of the central planning challenges.

---

## 3. Compliance Gaps at Application Level

The Strategy phase had identified regulatory requirements conceptually.

However, Planning revealed that compliance was not operationally mapped to workloads.

### Key Gaps

- No compliance tagging at application level
- No environment classification standards
- Shared infrastructure between regulated and non-regulated workloads
- No workload-specific governance alignment

### Examples

| Workload | Issue Identified |
|---|---|
| Payment Systems | Shared network paths with non-regulated systems |
| Financial Reporting Platforms | Shared infrastructure with low-risk applications |
| Customer Applications | Regional data placement inconsistencies |

### Impact

Compliance could no longer be treated as:
- high-level governance guidance

It now required:
- workload-aware architecture decisions
- segmentation planning
- environment isolation strategies

---

# Key Planning Realization

The Planning phase revealed that the challenge was no longer defining transformation goals.

The challenge became:
- structuring execution safely
- sequencing workloads correctly
- translating compliance into architecture
- balancing modernization with operational stability

This phase transformed cloud adoption into:
- constraint-aware execution planning

---

# Planning Decisions Made

## Decision 1 – Introduce Multi-Dimensional Application Classification

Applications were classified across multiple operational dimensions.

### Classification Model

| Dimension | Example Values |
|---|---|
| Business Criticality | High / Medium / Low |
| Technical Complexity | High / Medium / Low |
| Compliance Category | PCI-DSS / SOX / GDPR / None |
| Deployment Pattern | VM / Container / PaaS |
| Recovery Requirement | High Availability / Standard Recovery |

### Impact

This enabled:
- more accurate migration sequencing
- compliance-aware planning
- operational prioritization
- workload segmentation

---

## Decision 2 – Implement Compliance Tagging

Compliance requirements were mapped directly to workloads.

### Example

| Application | Compliance Tags |
|---|---|
| Payment Gateway | PCI-DSS, High Criticality |
| Financial Reporting | SOX |
| Customer Portal | GDPR |

### Architectural Impact

Compliance tagging directly influenced:
- network segmentation
- access control models
- workload placement
- landing zone design
- logging and monitoring requirements

### Key Observation

Compliance became:
- architecture-driving metadata

rather than:
- external governance documentation

---

## Decision 3 – Refine Migration Strategy Dynamically

Initial migration assumptions changed significantly after application-level analysis.

### Examples

| Application | Initial Strategy | Revised Strategy |
|---|---|
| Customer Portal | Replatform | Rehost due to timeline constraints |
| Payment Platform | Rehost | Temporarily retained |
| Reporting Systems | Rehost | Replatform for database optimization |

### Key Observation

Migration strategy decisions evolved continuously based on:
- operational constraints
- technical feasibility
- business timelines
- dependency complexity

### Impact

The Planning phase reinforced that:
- 6Rs decisions are rarely final during early planning

---

## Decision 4 – Create Compliance-Aware Migration Waves

Migration sequencing was redesigned using:
- business risk
- workload complexity
- compliance sensitivity
- operational readiness

### Migration Wave Model

| Wave | Characteristics |
|---|---|
| Wave 1 | Low-risk internal systems |
| Wave 2 | Customer-facing workloads |
| Wave 3 | Regulated reporting platforms |
| Wave 4 | Highly sensitive payment systems |

### Key Observation

Migration sequencing was no longer driven only by:
- technical complexity

It was also shaped by:
- compliance exposure
- operational dependency risk
- organizational readiness

---

## Decision 5 – Sequence Migration Around Dependencies

Dependency mapping directly altered migration sequencing.

### Examples

- Authentication platforms migrated before dependent applications
- Shared middleware components prioritized early
- Reporting systems delayed until core interfaces were stabilized

### Impact

Migration planning shifted from:
- application-by-application execution

to:
- dependency-aware orchestration

---

## Decision 6 – Define Landing Zone Requirements Early

The Planning phase generated explicit architectural requirements for the upcoming Ready phase.

### Examples

| Requirement Type | Impact on Landing Zone |
|---|---|
| PCI-DSS Workloads | Isolated network segmentation |
| SOX Systems | Centralized logging and audit controls |
| GDPR Applications | Region-aware deployment boundaries |
| Shared Services | Dedicated platform environments |

### Key Observation

Planning and foundational architecture became tightly interconnected.

The Ready phase would now need to enforce:
- workload-aware governance
- compliance-aware segmentation
- operational isolation boundaries

---

# What Changed During Planning

| Initial Assumption | Planning Reality |
|---|---|
| Applications are mostly understood | Significant inventory expansion occurred |
| Dependencies are manageable | Hidden coupling increased complexity |
| Compliance is conceptual | Compliance requires workload-level enforcement |
| Migration strategies are stable | Strategies evolve continuously |
| Waves can be planned statically | Sequencing must remain adaptive |

---

# Key Insight

The Planning phase transformed cloud adoption from:
- strategic direction

into:
- executable and constraint-aware transformation planning

The most important outcome was not the migration roadmap itself.

It was establishing realistic execution alignment between:
- workloads
- dependencies
- compliance obligations
- operational readiness
- architectural constraints

---

# Outputs of the Planning Phase

At the end of the Planning phase, ACME Corp had:

- A refined application inventory
- Multi-dimensional workload classification
- Compliance-tagged applications
- Dependency-aware migration sequencing
- Defined migration waves
- Refined migration strategies
- Early landing zone requirements
- Governance-aligned architecture inputs

---

# Transition to Ready in Practice

The Planning phase made one thing clear:

Cloud adoption could not scale without strong foundational controls.

The organization now needed to establish:
- governed cloud environments
- segmented architecture boundaries
- centralized operational controls
- scalable platform governance

This led directly into the Ready phase, where architectural plans would become operational cloud foundations.

---

[⬅ Series Home](index.md) |[⬅ Back](strategy-in-practice.md) | [Next➡](ready-in-practice.md)