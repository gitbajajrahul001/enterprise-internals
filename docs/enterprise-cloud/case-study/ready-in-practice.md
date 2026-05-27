---
layout: default
title: Ready in Practice
---

# Phase 3 – Ready in Practice

## Engagement Context

With detailed planning completed, ACME Corp moved into the Ready phase.

The organization now had:
- workload classifications
- migration sequencing
- compliance tagging
- dependency-aware planning
- operating model direction

The next challenge was implementing a cloud foundation capable of supporting:
- governance enforcement
- workload isolation
- operational scalability
- compliance-aware deployment patterns

This phase focused on building the Landing Zone that would support enterprise-scale cloud adoption.

---

# Initial Assumptions

At the beginning of the Ready phase, several assumptions existed:

- Governance controls could be enforced centrally
- Workloads could be segmented cleanly
- Subscription design would align naturally with workload structure
- IAM ownership boundaries were already understood
- Landing zone implementation would follow the planned architecture closely

As implementation progressed, these assumptions proved only partially accurate.

---

# What We Discovered

## 1. Governance vs Agility Conflict

The largest operational tension emerged between:
- governance enforcement
- delivery speed expectations

### Platform Team Perspective

The platform team prioritized:
- policy enforcement
- access control
- compliance alignment
- deployment governance

### Application Team Perspective

Application teams prioritized:
- rapid provisioning
- deployment flexibility
- reduced approval dependency
- operational autonomy

### Example

Development teams expected:
- on-demand environment provisioning

while governance teams enforced:
- approval workflows
- region restrictions
- resource controls
- deployment standards

### Impact

This created:
- onboarding delays
- operational friction
- governance bypass attempts
- escalation cycles between teams

---

## 2. Network Architecture Complexity

The original network design assumed a relatively standardized architecture model.

### Initial Direction

- Centralized hub-spoke topology
- Shared firewall model
- Unified connectivity standards

### Reality

Different workload categories required significantly different networking approaches.

### Examples

| Workload Type | Requirement |
|---|---|
| PCI-DSS Systems | Strict isolation and private connectivity |
| Customer Portals | Internet-facing access |
| Legacy Integrations | Flat connectivity assumptions |
| Development Environments | Simplified and flexible networking |

### Key Observation

A single networking pattern could not efficiently support all workload categories.

### Impact

The network architecture evolved into:
- tiered segmentation models
- workload-specific connectivity patterns
- differentiated isolation strategies

---

## 3. IAM Ownership Gaps

The Planning phase assumed operational ownership boundaries were already understood.

Implementation revealed otherwise.

### Common Issues

- Multiple teams requesting elevated permissions
- Temporary access becoming permanent
- Undefined ownership for shared services
- Broad Contributor and Owner role assignments

### Key Observation

Identity governance was operationally immature despite existing security policies.

### Impact

IAM quickly became one of the most sensitive governance areas because it directly affected:
- operational speed
- deployment autonomy
- auditability
- compliance enforcement

---

## 4. Policy Enforcement Challenges

Governance policies defined during planning created operational resistance during implementation.

### Examples

Policies included:
- denying public IP creation
- enforcing tagging
- restricting deployment regions
- requiring approved resource configurations

### Reality

Application teams experienced:
- blocked deployments
- failed provisioning requests
- unclear policy error handling

### Result

Teams began:
- requesting policy exceptions
- bypassing standards
- escalating governance conflicts

### Key Observation

Strict governance without operational maturity created friction rather than consistency.

---

## 5. Landing Zone Scope Expansion

The original landing zone scope was relatively limited.

### Initial Scope

- Core subscriptions
- Networking
- IAM integration
- Basic governance controls

### Expanded Scope

As implementation progressed, additional requirements emerged:
- centralized logging
- shared monitoring platforms
- DNS and identity services
- security integrations
- compliance-specific controls
- observability standards

### Impact

The landing zone evolved from:
- infrastructure setup

into:
- operational platform engineering

---

# Key Ready Phase Realization

The Ready phase revealed that cloud foundations are not built only through architecture diagrams.

They are shaped by:
- organizational behavior
- operational maturity
- governance adoption
- workload realities
- implementation trade-offs

This was the stage where:
- theoretical design encountered operational resistance

and:
- architecture became operationally constrained

---

# Decisions Made During the Ready Phase

## Decision 1 – Refine Subscription & Environment Structure

The original subscription design evolved into a layered operational structure.

### Revised Structure

| Layer | Purpose |
|---|---|
| Platform Subscriptions | Shared services, governance, networking |
| Landing Zone Subscriptions | Workload hosting environments |
| Sandbox Environments | Controlled experimentation and development |

### Impact

This improved:
- operational separation
- governance boundaries
- cost visibility
- access control management

---

## Decision 2 – Introduce Tiered Network Models

Instead of enforcing a single network architecture pattern, the organization adopted workload-aware segmentation.

### Examples

| Workload Type | Network Approach |
|---|---|
| PCI-DSS Systems | Strict hub-spoke isolation |
| Non-Critical Development Workloads | Simplified VNet structure |
| Shared Services | Centralized platform connectivity |

### Impact

This balanced:
- security requirements
- operational simplicity
- workload flexibility

---

## Decision 3 – Implement Role-Based IAM Governance

IAM responsibilities were formally segmented.

### Revised Model

| Team | Access Scope |
|---|---|
| Platform Team | Owner access at platform layer |
| Application Teams | Contributor at workload scope |
| Audit Teams | Read-only access |

### Additional Controls

- Privileged access review processes
- Reduced standing administrative access
- Controlled elevation workflows

### Impact

IAM became:
- more governable
- more auditable
- operationally scalable

---

## Decision 4 – Introduce Phased Governance Enforcement

The organization moved away from immediate hard enforcement.

### Revised Approach

| Phase | Governance Mode |
|---|---|
| Phase 1 | Audit and visibility |
| Phase 2 | Partial enforcement |
| Phase 3 | Full deny-based controls |

### Key Observation

Organizations require operational adaptation time before strict governance becomes sustainable.

### Impact

This reduced:
- deployment friction
- governance resistance
- operational disruption

while still improving compliance visibility.

---

## Decision 5 – Implement Compliance-Aware Isolation

Workload segmentation became directly aligned to compliance categories.

### Examples

| Compliance Category | Architectural Enforcement |
|---|---|
| PCI-DSS | Isolated subscriptions and segmented networks |
| SOX | Centralized audit logging and restricted access |
| GDPR | Region-bound deployment policies |

### Impact

Compliance transitioned from:
- governance documentation

into:
- enforceable platform architecture

---

## Decision 6 – Expand Operational Foundations

The landing zone evolved into a broader operational platform.

### Additional Capabilities Introduced

- Centralized observability
- Unified logging
- Shared monitoring standards
- Identity integration
- Security tooling integration

### Key Observation

Cloud foundations require operational services, not just infrastructure provisioning.

---

# What Changed During the Ready Phase

| Planning Assumption | Ready Phase Reality |
|---|---|
| Governance can be enforced immediately | Enforcement must mature gradually |
| Networking is mostly standardized | Workloads require differentiated patterns |
| IAM ownership is clear | Ownership requires operational refinement |
| Landing zone scope is fixed | Scope expands during implementation |
| Compliance tagging alone is sufficient | Compliance requires architectural enforcement |

---

# Key Insight

The Ready phase transformed cloud architecture into:
- operationally governed systems

This phase exposed the reality that:
- cloud foundations are organizational systems as much as technical systems

The most important outcome was not simply building infrastructure.

It was establishing:
- scalable operational governance
- workload-aware architecture controls
- sustainable platform management patterns

---

# Outputs of the Ready Phase

At the end of the Ready phase, ACME Corp had:

- Implemented landing zone architecture
- Defined subscription hierarchy
- Established workload segmentation patterns
- Implemented IAM governance controls
- Introduced phased governance enforcement
- Enabled centralized monitoring and logging
- Established compliance-aware isolation models
- Created foundational operational platform services

---

# Transition to Adoption in Practice

With foundational controls implemented, workload onboarding and migration execution could begin.

The next phase would test:
- migration assumptions
- operational readiness
- workload stability
- deployment maturity
- observability effectiveness

This led into the Adopt phase, where cloud transformation would move from architecture into operational execution.

---

[⬅ Series Home](index.md) |[⬅ Back](plan-in-practice.md) | [Next➡](adopt-in-practice.md)