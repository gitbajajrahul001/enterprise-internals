---
layout: default
title: Network Architecture | Case Study
---

# Network Architecture – Case Study (ACME Corp)

This section extends the ACME Corp transformation journey, focusing on how network architecture decisions evolved across Strategy, Plan, Ready, and Adopt phases.

During earlier phases, ACME Corp had defined:

- Compliance-driven segmentation (PCI, SOX, GDPR workloads)  
- Hub-and-spoke as the initial network model  
- Hybrid connectivity to support legacy systems  

However, these decisions were still theoretical and had not been tested under real workload conditions.

---

## 🔷 1. Initial Understanding

---

At the start of the Ready phase, the network vision was *Implement a centralized hub-and-spoke architecture with strict segmentation and full traffic inspection*

### **Observations**

- Strong focus on security and control  
- Assumption that all traffic would flow through central hub  
- Limited consideration for application-specific communication patterns  

>
> The initial design optimized for control, not for application behavior.
>
---

## 🔷 2. What We Discovered

---

As workloads began onboarding, several realities emerged:

### **Application Communication Mismatch**

- Some applications required low-latency communication  
- Others depended on direct service-to-service connectivity  

#### **Example:**

- Customer-facing application routed through central firewall  
- Result: increased latency and degraded user experience  

### **Hybrid Dependency Challenges**

- Core systems still hosted on-prem  
- Cloud workloads dependent on on-prem authentication and data  

#### **Example:**

- Login flows delayed due to repeated network round trips  

### **Segmentation Complexity**

- PCI workloads required strict isolation  
- But shared services needed access across environments  

#### **Example:**

- Logging and monitoring services needing access to both PCI and non-PCI environments  

### **IP Address Conflicts**

- Overlapping IP ranges between regions and legacy systems  

#### **Example:**

- Two business units using same CIDR range  
- Blocking VNet peering and hybrid connectivity  

>
> The network design did not fail — it exposed gaps between planned segmentation and actual communication needs.
>

---

## 🔷 3. Decisions Made

---

### **Decision 1: Evolve Hub-and-Spoke Model**

Instead of strict centralization:

- Retained hub for:
  - security controls  
  - shared services  
- Allowed selective direct communication between spokes  

#### **Example:**

- Service-to-service communication allowed within trusted boundaries  
- Not all traffic forced through central firewall  

### **Decision 2: Introduce Tiered Segmentation**

Instead of uniform segmentation:

- High-security zones  *(e.g., PCI workloads with strict isolation)*  

- Medium-security zones  *(e.g., internal business applications)*  

- Flexible zones   *(e.g., development and testing environments)*  

### **Decision 3: Optimize Hybrid Connectivity**

- Reduced dependency on on-prem systems  
- Replicated critical services in cloud  

#### **Example:**

- Identity services partially moved to cloud  
- Reduced authentication latency  

### **Decision 4: Establish Structured IP Addressing**

- Defined global IP allocation strategy  
- Assigned ranges per region and environment  

#### **Example:**

- Region-based CIDR allocation  
- Reserved space for future growth  

### **Decision 5: Introduce Controlled Network Exceptions**

Instead of rigid enforcement:

- Defined exception process  
- Allowed temporary connectivity with review  

#### **Example:**

- Temporary access for testing environments  
- Reviewed and removed post-validation  

### **Decision 6: Enhance Network Observability**

- Enabled flow logs and diagnostics  
- Integrated network metrics with application monitoring  

#### **Example:**

- Identified latency issues through flow logs  
- Correlated with application performance metrics  

---

## 🔷 4. What Changed During Execution

---

| Initial Assumption | Reality |
|------------------|--------|
| Hub-and-spoke works for all workloads | Requires selective flexibility |
| Segmentation can be strictly enforced | Needs contextual adaptation |
| Hybrid connectivity is temporary | Becomes long-term dependency |
| IP planning is straightforward | Requires structured governance |
| Network issues are easy to diagnose | Requires strong observability |

>
> Network architecture evolved from a centralized control model to a **balanced, context-aware design**
>

---

## 🔷 5. Final Network Architecture State

---

At the end of initial transformation phases, ACME Corp had:

- Hybrid network with cloud and on-prem integration  
- Hub-and-spoke model with selective flexibility  
- Tiered segmentation aligned with compliance levels  
- Structured IP addressing across regions  
- Enhanced observability for network flows  

**Resulting Network Model:**

```text
                On-Prem Data Center
                         |
                Hybrid Connectivity
                         |
                -------------------
                |      Hub        |
                | (Firewall, DNS, |
                |  Shared Svcs)   |
                -------------------
                 /        |        \
                /         |         \
         --------     --------     --------
        | PCI   |   | SOX   |   | Non-PCI |
        | Zone  |   | Zone  |   | Zone    |
         --------     --------     --------

   (Selective communication allowed between zones where required)
```
---

## 🔍 Closing Thoughts

---

ACME Corp’s journey highlights that:

- Centralized control must be balanced with flexibility  
- Segmentation must align with real application flows  
- Hybrid complexity cannot be ignored  
- Observability is essential for managing distributed systems  

>
> The most effective network architectures are not rigid — they are adaptable to changing workloads and constraints.
>

---

[⬅ Back to Series Home](index.md) | [⬅ Back to Network Architecture-Consulting](network-arch-consulting.md) 