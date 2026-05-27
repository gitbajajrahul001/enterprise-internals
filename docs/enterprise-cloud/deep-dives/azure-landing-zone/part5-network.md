---

layout: default
title: Designing Network Architecture

---

# 🌐 Part 5 — Designing Network Architecture

### _Where Most “Good Designs” Break in Production_


Networking is where:

*   performance issues show up
*   security gaps get exposed
*   costs spiral
*   re-architecture becomes painful

🔥 First Principle

Before choosing Hub-Spoke, vWAN, or anything:

> Network design is NOT about topology — it’s about traffic behavior

* * *

## ❌ The Most Common Mistake

Teams start with:

*   “Let’s do Hub-Spoke”
*   “Let’s deploy firewall”
*   “Let’s create VNets”

Without asking:

*   Who talks to whom?
*   How often?
*   From where?
*   Through what controls?

👉 Result:

> Technically correct architecture… operationally broken system

* * *

## 🧠 Start With These 4 Questions

### **1\. Traffic Patterns**

*   App → DB?
*   App → App?
*   On-prem → Cloud?
*   Internet → App?

## **2\. Trust Boundaries**


*   Regulated vs non-regulated
*   Internal vs external
*   Production vs non-production

## **3\. Inspection Requirements**

*   Do you need:
    *   firewall inspection?
    *   WAF?
    *   IDS/IPS?


## **4\. Connectivity Model**

*   Branch → Cloud?
*   DC → Cloud?
*   Cloud → Cloud (future AWS)?

## 🔷 Core Design Models

Now we talk topology.

### **1\. Hub-Spoke (Most Common)**

```text
        Branches
           │
        vWAN Hub
       /    |    \
   VNet1  VNet2  VNet3
```

#### **Why it works**

*   centralized control
*   easier governance
*   scalable
*   security inspection

#### **Real-world use**


*   enterprise workloads
*   regulated environments
*   hybrid cloud

* * *

### **2\. Virtual WAN (vWAN)**

```text
        Branches  
           │  
        vWAN Hub  
       /    |    \\  
   VNet1  VNet2  VNet3
```

#### **Why it works**

*   global scale
*   simplified branch connectivity
*   built-in routing

#### **Real-world use**

*   multi-region banks
*   many branches
*   global footprint


### **3\. Mesh (Avoid in Enterprise)**

```text
VNet1 ↔ VNet2 ↔ VNet3
```

#### **Problem**

*   no central control
*   security gaps
*   unmanageable at scale

* * *

## 🔥 Key Design Components

### **1\. Hub VNet (Critical)**

This is your **control plane**

Contains:

*   Azure Firewall / NVA
*   DNS (Private DNS)
*   Bastion
*   VPN / ExpressRoute Gateway

* * *

### **2\. Spoke VNets**

Each workload lives here:

*   App VNets
*   AKS VNets
*   DB VNets

* * *

### **3\. Private Connectivity (Important)**

*   Private Endpoints
*   Private DNS Zones

👉 Avoid public exposure

* * *

### **4\. Egress Control**

All outbound traffic:

> Must go through firewall

* * *

### **5\. Ingress Control**

*   Application Gateway (WAF)
*   Front Door (for global apps)

* * *

## 🔐 Security Design (Non-Negotiable)

*   No direct internet exposure
*   No public IPs by default
*   Forced tunneling via firewall
*   Network segmentation

* * *

## 🔁 Real Example

### **Payment Application (PCI)**

```text
Internet → WAF → App Gateway → Spoke VNet → DB (Private Endpoint)  
                        │  
                    Firewall (Hub)
```

### **Internal App**

```text
On-Prem → ExpressRoute → Hub → Spoke → App
```

* * *

## ⚠️ Common Mistakes

### ❌ Over-segmentation

*   too many VNets
*   too many rules

👉 operational nightmare

## ❌ No DNS strategy

*   private endpoints fail
*   name resolution breaks

## ❌ Bypassing firewall


*   direct internet access
*   shadow IT risk

## ❌ Ignoring latency

*   cross-region traffic
*   app performance issues

* * *

## 🧠 Architect Thinking

You don’t ask:

> “Should I use Hub-Spoke?”

You ask:

> “Where should traffic flow, and where should it be controlled?”

One-Line Rule:

> Design network around traffic and control — not diagrams

* * *

### **What Comes Next**

Now that network is clear, we move into:

🔐 Identity & Access Design (RBAC, PIM, Zero Trust)

Because:

> Network controls traffic  
> Identity controls access

---

[⬅ Back to Series Home](index.md) |  [⬅ Back to: Subscription Design ➡](part4-subscriptions.md) | [Next: Identity Design ➡](part6-identity.md)


