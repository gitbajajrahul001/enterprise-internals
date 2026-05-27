---
layout: default
title: Plan Phase
---

# Plan Phase – Structuring Cloud Adoption Execution

The Plan phase is where cloud adoption transitions from strategic intent into structured execution.

If the Strategy phase defines:
- why cloud adoption is needed
- what business outcomes are expected

then the Plan phase defines:
- how adoption will be executed
- how workloads will be prioritized
- how risks and dependencies will be managed
- how teams will operate during and after migration

This phase establishes the execution structure required to enable controlled, scalable, and predictable cloud adoption.

---

# What the Plan Phase Really Means

Cloud planning is not simply about creating migration schedules.

It is the process of converting strategic direction into:
- actionable execution
- workload-level decisions
- operational alignment
- migration sequencing
- governance-aware implementation planning

In practice, the Plan phase is iterative.

Many assumptions established during strategy discussions are refined, challenged, or corrected once deeper technical and organizational realities become visible.

---

# Core Planning Pillars

Cloud planning is built on a set of interconnected pillars that collectively define the cloud adoption roadmap.

---

## 1. Digital Estate Understanding

Before migration planning can begin, the current environment must be clearly understood.

### Key Focus Areas

- Application inventory
- Infrastructure footprint
- Data flows and integrations
- Existing operational dependencies
- Platform ownership visibility

### Why It Matters

A well-defined digital estate becomes the foundation for:
- application classification
- migration sequencing
- dependency analysis
- operational risk assessment

### Common Challenges

- Incomplete application inventories
- Outdated CMDB or documentation
- Unknown ownership boundaries
- Hidden integrations discovered late

### Consulting Insight

Digital estate understanding is rarely complete during initial discovery.

A practical approach treats discovery as:
- iterative
- continuously refined
- validated during migration execution

The goal is not perfect visibility on day one, but sufficient visibility to make informed decisions.

---

## 2. Application Rationalization (6Rs)

Each application must be evaluated and aligned to an appropriate migration strategy.

### Common Rationalization Strategies

| Strategy | Description |
|---|---|
| Rehost | Lift-and-shift with minimal changes |
| Replatform | Minor optimization while leveraging managed services |
| Refactor | Modify applications for cloud-native capabilities |
| Rearchitect | Redesign application architecture |
| Rebuild | Rewrite the application entirely |
| Retain / Replace | Keep existing solution or replace with SaaS |

### Key Considerations

- Business criticality
- Migration complexity
- Technical debt
- Long-term modernization goals
- Timeline constraints
- Cost implications

### Common Challenges

- Preference for rehosting due to aggressive timelines
- Resistance to refactoring because of perceived risk
- Misalignment between business and technical priorities
- Everything being classified as "critical"

### Consulting Insight

Migration strategy decisions are rarely ideal technical decisions.

Most organizations operate within constraints involving:
- budget
- timelines
- skill availability
- operational pressure

The role of planning is not to force perfection, but to:
- expose trade-offs clearly
- align decisions with business priorities
- avoid short-term choices that create long-term operational inefficiencies

---

## 3. Dependency Mapping

Understanding application and infrastructure dependencies is essential for controlled migration execution.

### Key Questions

- Which systems interact with each other?
- Which integrations are latency-sensitive?
- Which dependencies cannot be decoupled easily?
- Are there external or on-premises integration requirements?

### Why It Matters

Dependency mapping helps ensure:
- workloads migrate in the correct sequence
- integrations remain functional
- outages and operational disruption are minimized

### Common Challenges

- Hidden dependencies discovered during migration
- Over-reliance on outdated documentation
- Informal integrations unknown to architecture teams

### Consulting Insight

Dependency mapping should not be treated as a one-time exercise.

A mature planning approach continuously validates and refines dependencies through:
- discovery tooling
- migration pilots
- early migration waves
- operational feedback

---

## 4. Migration Waves & Sequencing

Cloud adoption is typically executed in controlled phases called migration waves.

### Typical Wave Structure

| Wave | Type |
|---|---|
| Wave 1 | Low-risk, non-critical workloads |
| Wave 2 | Medium complexity applications |
| Wave 3 | Business-critical systems |

### Why It Matters

Wave-based execution helps:
- reduce migration risk
- validate assumptions progressively
- improve operational confidence
- prevent large-scale disruption

### Common Challenges

- Pressure to migrate critical applications early
- Unrealistic expectations around migration speed
- Resistance to phased execution approaches

### Consulting Insight

Migration waves are not simply workload groupings.

They are mechanisms used to:
- validate architecture assumptions
- refine operational processes
- improve migration repeatability
- build organizational confidence over time

Well-structured migration waves reduce both technical and organizational risk.

---

## 5. Cloud Operating Model Alignment

Cloud adoption changes how technology teams operate.

The operating model defines:
- ownership boundaries
- governance responsibilities
- operational accountability
- platform management structure

### Common Operating Models

| Model | Description |
|---|---|
| Centralized | Central team manages cloud operations |
| Shared | Platform team provides common services |
| Decentralized | Application teams manage workloads independently |

### Key Considerations

- Platform vs application ownership
- Governance enforcement responsibilities
- Operational support boundaries
- DevOps and automation alignment

### Common Challenges

- Undefined ownership after migration
- Conflicts between central platform and application teams
- Governance responsibilities distributed inconsistently

### Consulting Insight

Operating model gaps often become visible during planning rather than during strategy discussions.

This is typically where organizations realize:
- governance responsibilities are unclear
- cloud ownership is fragmented
- existing operational structures do not scale effectively in cloud environments

Planning must clarify these boundaries before large-scale migration begins.

---

## 6. Organizational Alignment

Cloud adoption is not only a technical transformation.

It also changes:
- team responsibilities
- delivery models
- operational processes
- collaboration patterns

### Key Focus Areas

- Role definitions
- Cross-team collaboration
- DevOps adoption
- Platform engineering alignment
- Operational readiness

### Why It Matters

Without organizational alignment:
- execution slows down
- ownership confusion increases
- operational friction grows after migration

### Common Challenges

- Resistance to operational change
- Legacy ownership structures
- Lack of cloud skill readiness
- Siloed infrastructure and application teams

### Consulting Insight

Technical migration often progresses faster than organizational transformation.

Long-term cloud success depends heavily on:
- operational maturity
- accountability clarity
- team enablement
- platform operating discipline

---

## 7. Cost & Financial Planning (FinOps)

Cloud introduces consumption-based financial models that require proactive planning.

### Key Areas

- Budget forecasting
- Cost allocation and tagging
- Chargeback or showback models
- Optimization planning
- Consumption visibility

### Why It Matters

Financial planning provides visibility into:
- expected cloud spend
- workload-level cost distribution
- operational optimization opportunities

### Common Challenges

- Underestimation of cloud operating costs
- Lack of cost ownership
- Inconsistent tagging strategies
- Reactive rather than proactive optimization

### Consulting Insight

Cost discussions evolve significantly during planning.

Organizations typically move from:
- estimating cloud costs

to:
- establishing operational accountability for cloud consumption

FinOps maturity becomes increasingly important as adoption scales.

---

## 8. Environment & Landing Zone Planning

The Plan phase defines the structural requirements for the target cloud environment.

This phase does not fully design the landing zone, but it establishes:
- environment strategy
- isolation requirements
- governance expectations
- connectivity requirements

### Key Focus Areas

- Subscription or account structure
- Environment separation (Dev / Test / Prod)
- Network segmentation
- Identity integration
- Governance and policy requirements

### Connection to the Ready Phase

The outputs from planning directly feed into:
- Landing Zone Design
- Governance Implementation
- Platform Architecture
- Security Baseline Definition

---

# Handling Real-World Planning Challenges

Cloud planning rarely occurs under ideal conditions.

Organizations commonly face:
- incomplete data
- conflicting priorities
- unrealistic timelines
- political ownership conflicts
- evolving business requirements

### Common Scenarios

| Situation | Practical Approach |
|---|---|
| Incomplete application data | Use iterative discovery and refine during migration waves |
| Everything marked as critical | Introduce objective classification criteria |
| Conflicting priorities | Align decisions to business impact and operational risk |
| Unrealistic timelines | Break execution into phased milestones |
| Hidden dependencies | Validate continuously during early migrations |

---

# Key Outputs of the Plan Phase

A mature Plan phase should produce:

- Application inventory and classification
- Migration strategy mapping (6Rs)
- Dependency-aware migration sequencing
- Migration wave planning
- Operating model alignment
- Governance considerations
- Financial planning inputs
- Landing zone requirements
- Execution roadmap

---

# Key Insight

Planning is not about creating a perfect roadmap.

It is about enabling informed decision-making under uncertainty while reducing operational, architectural, and organizational risk.

---

# Closing Thoughts

The Plan phase is where cloud adoption becomes operationally actionable.

It is also the stage where:
- assumptions are challenged
- trade-offs become visible
- governance expectations are clarified
- execution realities emerge

A well-structured planning approach enables organizations to:
- migrate with greater predictability
- reduce operational disruption
- align technology decisions with business objectives
- establish scalable cloud operating foundations

---

[⬅ Series Home](index.md) |[⬅ Back](strategy-phase.md) | [Next➡](plan-phase.md)