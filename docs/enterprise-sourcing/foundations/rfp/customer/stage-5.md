---
layout: default
title: Sourcing Strategy 
---

# 🏢 Stage 5 — Sourcing Strategy

Now we define: How will Acme go to market to find the right partner(s)?

---

## 👥 Who Is Involved

| Role | Description |
|------|------------|
| Procurement Team | Sourcing specialists who manage vendor selection process |
| CIO / CTO | Chief Information Officer / Chief Technology Officer |
| Enterprise Architects | Provide architectural direction and constraints |
| Finance Team | Validate financial approach and constraints |
| Legal Team | Ensure contractual and compliance considerations |

---

## 🛠 What Happens in This Stage

### 1. Decide Engagement Model

Acme decides the **engagement model** for the sourcing initiative.

| Option | Benefits | Trade-offs |
|--------|----------|------------|
| Single vendor | Simpler governance, single accountability, easier coordination, unified reporting | Higher dependency on one partner, limited best-of-breed specialization, potential lock-in |
| Multi-vendor | Access to specialized expertise, better fit for different workstreams, competitive tension between vendors | More complex governance, higher coordination effort, unclear accountability if roles are not well-defined |

---

### 2. Decide Scope Packaging

Acme decides **how the work will be packaged** for the market.

| Package | Benefits | Trade-offs |
|---------|----------|------------|
| End-to-end transformation | Single integrated scope covering strategy, migration, and operations; easier accountability across the full journey | Larger commitment, longer evaluation cycle, higher dependency on selected partner |
| Migration project | Clear project boundary, easier to estimate, suitable for workload movement or data center exit | May not address operating model, governance, or post-migration optimization |
| Managed services | Suitable for steady-state operations, SLA-driven delivery, predictable run cost | Less focus on transformation; quality depends on clear SLAs, scope boundaries, and governance |
| Platform build | Strong fit for cloud foundation, landing zone, automation, security, and service catalog setup | Requires clear ownership after build; benefits may be limited if adoption and operating model are not defined |

---

### 3. Decide Commercial Model

Acme decides **how vendors will be paid** and how commercial risk will be shared.

| Model | Benefits | Trade-offs |
|------|----------|------------|
| Fixed price | Predictable cost, easier budget approval, clear commercial baseline | Works best only when scope is well-defined; change requests can increase cost and delay execution |
| Time & Material | Flexible for evolving scope, useful when requirements are unclear, faster to start | Cost can increase if effort is not controlled; requires strong governance and tracking |
| Managed services | Predictable recurring cost, suitable for steady-state operations, supports SLA-based delivery | Less flexible for major scope changes; service quality depends heavily on SLA design and governance |
| Outcome-based | Aligns vendor payment with business results, encourages ownership and innovation | Harder to define measurable KPIs; disputes can arise if outcomes are influenced by factors outside vendor control |

---

### 4. Define Vendor Qualification Criteria

Acme defines **which vendors are eligible** to participate in the sourcing process.

| Criteria | Why It Matters | Trade-offs / Watchouts |
|----------|----------------|------------------------|
| Large-scale cloud transformation experience | Ensures the vendor has handled complex migration, modernization, and operating model changes | Past experience must be relevant to Acme’s scale, industry, and technology landscape |
| SAP migration capability | Critical if SAP workloads are in scope, especially for business-critical systems | Generic cloud migration experience is not enough; SAP sizing, downtime planning, and dependency mapping matter |
| Multi-cloud expertise | Supports environments involving Azure, AWS, private cloud, or hybrid platforms | Broad capability should not hide shallow expertise; validate depth in the platforms actually in scope |
| Global delivery capability | Enables support across regions, time zones, and delivery centers | Global scale can add coordination complexity if ownership, escalation, and governance are unclear |

---

## 📦 Output

- Sourcing Strategy Document
- Vendor selection approach defined

--- 


## ⚡ Key Insight

These decisions are not independent.

They are linked:

| Decision | Impact |
|----------|--------|
| Single vendor | Easier fixed pricing |
| Multi-vendor | Requires strong governance |
| T&M | Needs trust and oversight |
| Fixed price | Requires clarity |

---

##  🧠 How You Should Think

Whenever you face such decisions, ask:

- What is the current maturity?
- What is the risk tolerance?
- What is the speed vs control trade-off?
- What is the internal capability?

---

[⬅ Series Home](index.md) | [⬅ Future-State Vision](stage-4.md) | [RFI➡](stage-6.md)
