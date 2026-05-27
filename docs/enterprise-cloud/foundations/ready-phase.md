---
layout: default
title: Ready Phase
---

# Ready Phase – Establishing the Cloud Foundation

The Ready phase establishes the foundational cloud environment required to support secure, scalable, and governed cloud adoption.

If the Plan phase defines:
- how cloud adoption will be executed
- how workloads will be prioritized
- how governance and operations will function

then the Ready phase defines:
- where workloads will be deployed
- how foundational controls will be implemented
- how governance and operational standards will be enforced

This phase focuses on building the Landing Zone that enables consistent and repeatable workload deployment.

---

# What the Ready Phase Really Means

The Ready phase is not simply about provisioning cloud resources.

It is the stage where foundational architectural decisions are implemented to establish:
- governance boundaries
- operational controls
- security baselines
- connectivity models
- scalability foundations

This phase creates the environment that all future workloads will inherit.

A poorly designed Ready phase commonly results in:
- inconsistent deployments
- governance drift
- operational instability
- security gaps
- uncontrolled cloud growth
- long-term rework

---

# Core Readiness Pillars

Cloud readiness is built on a set of interconnected pillars that collectively establish a secure and scalable cloud foundation.

---

## 1. Resource Organization & Hierarchy

Cloud resources must be organized in a structured and scalable hierarchy.

This hierarchy establishes:
- governance boundaries
- ownership separation
- operational structure
- scalability alignment

### Key Focus Areas

- Management group hierarchy
- Subscription strategy
- Resource group organization
- Shared services placement
- Environment separation

### Common Design Patterns

| Layer | Purpose |
|---|---|
| Management Groups | Governance and policy inheritance |
| Subscriptions | Isolation, billing, and operational boundaries |
| Resource Groups | Lifecycle and workload organization |

### Common Challenges

- Multiple teams sharing a single subscription
- No separation between production and non-production
- Unclear ownership boundaries
- Shared services distributed inconsistently

### Consulting Insight

Hierarchy decisions made early have long-term impact on:
- governance enforcement
- operational scalability
- access management
- cost accountability

Overly simplistic hierarchy models often become difficult to scale, while overly complex structures create operational friction.

The objective is to establish clear separation without unnecessary complexity.

---

## 2. Identity & Access Management (IAM)

Identity becomes the primary control plane for cloud operations.

IAM decisions influence:
- security posture
- operational accountability
- governance enforcement
- privileged access control

### Key Focus Areas

- Centralized identity provider integration
- Role-Based Access Control (RBAC)
- Least privilege access
- Privileged access management
- Access lifecycle governance

### Common Challenges

- Excessive Owner or Contributor permissions
- Access granted permanently without review
- Weak separation between operational and administrative roles
- IAM configured for convenience rather than control

### Consulting Insight

IAM misconfigurations are among the most common long-term operational risks in cloud environments.

Strong IAM practices should focus on:
- minimizing privilege
- separating responsibilities
- controlling elevation paths
- regularly validating access ownership

Identity governance becomes increasingly important as cloud adoption scales.

---

## 3. Network Architecture

Network architecture defines how workloads communicate internally and externally.

The network model must balance:
- security
- scalability
- operational simplicity
- connectivity requirements

### Key Focus Areas

- Virtual network design
- Hub-spoke or alternative topologies
- Hybrid connectivity
- Private vs public access models
- Segmentation boundaries

### Common Design Considerations

| Design Area | Example Direction |
|---|---|
| Hybrid Connectivity | VPN or dedicated private connectivity |
| Workload Isolation | Segmented virtual networks |
| Shared Services | Centralized hub architecture |
| PaaS Security | Private Endpoints instead of public exposure |

### Common Challenges

- Over-engineered network architectures
- Public exposure of services due to poor planning
- Lack of workload segmentation
- Excessive operational complexity

### Consulting Insight

Complex network architectures are frequently introduced in anticipation of future scale that may never materialize.

A mature network design should:
- satisfy current operational needs
- enforce appropriate security boundaries
- remain operationally manageable
- evolve incrementally as adoption matures

Simplicity is often more valuable than theoretical architectural perfection.

---

## 4. Security Baseline

Security controls must be embedded into the cloud foundation before workloads are deployed.

Security implemented reactively after deployment typically leads to:
- inconsistent enforcement
- configuration drift
- operational gaps

### Key Focus Areas

- Encryption standards
- Threat protection
- Secure configuration baselines
- Identity-driven security controls
- Security policy enforcement

### Common Challenges

- Security standards defined but not enforced
- Inconsistent configurations across environments
- Security introduced too late in the adoption lifecycle
- Over-reliance on manual enforcement

### Consulting Insight

Security gaps are rarely caused by lack of tooling.

They are more commonly caused by:
- inconsistent governance
- weak enforcement
- unclear ownership
- operational shortcuts taken during rapid deployment

Security becomes sustainable only when embedded directly into:
- platform architecture
- automation
- governance policies
- operational workflows

---

## 5. Governance & Policy Enforcement

Governance establishes the operational guardrails required for controlled cloud adoption.

Effective governance enables:
- consistency
- compliance
- operational scalability
- cost accountability

without unnecessarily restricting innovation.

### Key Focus Areas

- Policy definition and enforcement
- Tagging standards
- Region restrictions
- Resource compliance controls
- Environment-specific governance

### Common Challenges

- No governance standards established early
- Overly restrictive policies blocking deployment
- Inconsistent tagging and cost allocation
- Governance applied differently across environments

### Consulting Insight

Governance maturity requires balance.

Overly restrictive governance slows adoption and encourages workarounds.

Insufficient governance creates:
- inconsistent environments
- operational instability
- uncontrolled cost growth

A practical approach often begins with:
- visibility and audit controls

before progressively enforcing:
- deny policies
- mandatory compliance standards
- automated governance enforcement

---

## 6. Cost Management Foundations

Cost management must be integrated into the cloud foundation from the beginning.

Cloud consumption models require operational accountability rather than reactive budgeting alone.

### Key Focus Areas

- Budget controls
- Cost allocation standards
- Resource tagging
- Cost visibility dashboards
- Consumption accountability

### Common Challenges

- No ownership of cloud spend
- Missing or inconsistent tagging
- Reactive cost optimization
- Lack of workload-level visibility

### Consulting Insight

Most cloud cost issues are not caused by excessive consumption alone.

They are caused by:
- unclear accountability
- lack of visibility
- absence of operational ownership

Cost governance becomes more effective when integrated into:
- platform standards
- deployment automation
- operational reporting
- organizational accountability models

---

## 7. Monitoring & Observability

Operational visibility must be established as part of the platform foundation.

Monitoring and observability provide the operational insight required for:
- troubleshooting
- incident response
- performance analysis
- operational stability

### Key Focus Areas

- Centralized logging
- Metrics collection
- Alerting standards
- Operational dashboards
- Cross-environment visibility

### Common Challenges

- Logs collected but never operationally reviewed
- Excessive alerts causing alert fatigue
- Fragmented monitoring across teams
- Inconsistent observability standards

### Consulting Insight

Observability only creates value when it enables:
- actionable operational response
- rapid troubleshooting
- operational learning
- measurable reliability improvement

Monitoring should be designed around operational outcomes rather than simply collecting telemetry.

---

## 8. Resilience & Backup Foundations

Resilience capabilities must be validated before workloads rely on them.

### Key Focus Areas

- Backup strategy
- Retention policies
- Availability architecture
- Recovery validation
- Regional resilience planning

### Common Challenges

- Backups configured but never tested
- Recovery assumptions not operationally validated
- Over-reliance on default configurations
- Misalignment between expected and actual recovery capabilities

### Consulting Insight

Resilience is not proven through configuration alone.

It is proven through:
- recovery testing
- operational validation
- failure simulation
- repeatable recovery execution

Organizations frequently discover recovery gaps only during real incidents because recovery capabilities were never fully validated beforehand.

---

## 9. Landing Zone Implementation

The Landing Zone combines all foundational decisions into a deployable and operational cloud environment.

It establishes:
- governance boundaries
- network connectivity
- security controls
- operational standards
- workload onboarding capabilities

### Key Focus Areas

- Environment structure
- Connectivity architecture
- IAM integration
- Governance enforcement
- Deployment readiness

### Common Challenges

- Partial landing zone implementation
- Governance bypassed for speed
- Inconsistent environment configuration
- Manual deployment dependencies

### Consulting Insight

A landing zone is only considered mature when it supports:
- repeatable deployment patterns
- governed workload onboarding
- operational consistency
- scalable platform operations

A landing zone should reduce operational effort, not increase it.

---

# Handling Real-World Ready Phase Challenges

Cloud readiness activities frequently expose:
- planning gaps
- conflicting priorities
- operational disagreements
- governance immaturity

### Common Scenarios

| Situation | Practical Approach |
|---|---|
| Over-engineered architecture | Start with simpler scalable foundations |
| Conflicting design preferences | Align decisions to business and operational priorities |
| Missing governance | Introduce baseline guardrails early |
| Security vs agility conflicts | Define controlled flexibility models |
| Operational ownership ambiguity | Clarify responsibilities before onboarding workloads |

### Consulting Insight

Many operational problems observed later in cloud adoption originate from foundational decisions made during the Ready phase.

Strong foundations reduce:
- operational drift
- governance inconsistency
- security exposure
- future rework effort

---

# Key Outputs of the Ready Phase

A mature Ready phase should produce:

- Implemented landing zone
- Defined resource hierarchy
- Identity and access governance model
- Network architecture implementation
- Security baseline enforcement
- Governance and policy controls
- Cost management standards
- Monitoring and observability setup
- Backup and resilience configuration
- Workload onboarding readiness

---

# Key Insight

The Ready phase is not only about building cloud foundations.

It is about building foundations that:
- scale predictably
- enforce governance consistently
- reduce operational risk
- support repeatable cloud adoption

Foundational decisions made here influence every downstream workload and operational process.

---

# Closing Thoughts

The Ready phase establishes the operational and governance foundation for cloud adoption.

A well-executed foundation enables:
- secure deployment patterns
- controlled scalability
- operational consistency
- governance alignment
- smoother workload onboarding

The quality of the Ready phase directly impacts:
- migration success
- operational maturity
- governance effectiveness
- long-term cloud sustainability

Cloud adoption scales successfully only when the foundational platform is designed with both technical and operational realities in mind.

---

[⬅ Series Home](index.md) |[⬅ Back](plan-phase.md) | [Next➡](adopt-phase.md)