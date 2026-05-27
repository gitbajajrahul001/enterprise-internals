---

layout: default
title: Identity & Access Design

---


# 🔐 Part 6 — Identity & Access Design

### _Where Real Security Actually Begins_

Most teams think security = network.

It’s not.

> In cloud, identity is the primary security boundary

🔥 First Principle

> Assume network is already compromised — control access through identity

This is the foundation of:

*   Zero Trust
*   Modern cloud security

* * *

## ❌ The Most Common Mistake

Teams do:

*   open access internally
*   broad permissions
*   shared credentials

Because:

> “It’s inside the VNet, so it’s safe”

👉 This thinking is dangerous in cloud

* * *

## 🧠 Start With These 4 Questions

### **1\. Who needs access?**

*   users
*   apps
*   services
*   automation

### **2\. What level of access?**

*   read
*   write
*   admin

### **3\. For how long?**


*   permanent
*   temporary
*   just-in-time

### **4\. Under what conditions?**

*   MFA required?
*   trusted device?
*   location-based?

* * *

## 🔷 Core Identity Components

### **1\. Microsoft Entra ID (Tenant Level)**

This is your *identity backbone*

*   users
*   groups
*   applications
*   service principals

* * *

### **2\. RBAC (Role-Based Access Control)**

> Defines *who can do what*

**Example Roles**

*   Reader
*   Contributor
*   Owner
*   Custom roles

**Where applied/Scope?**

*   Management Group
*   Subscription
*   Resource Group
*   Resource

🔥 Golden Rule


> Assign roles to groups — never directly to users


* * *

### **3\. PIM (Privileged Identity Management)**

> Controls **privileged access**

Instead of:

*   permanent admin access ❌

Use:

*   Just-in-time access ✔
*   approval workflow ✔
*   time-bound roles ✔

For Example:

Cloud Admin:

*   No permanent Owner role
*   Requests access via PIM
*   Gets 2-hour window
*   MFA enforced

* * *

### **4\. Conditional Access**

> Defines when and how access is allowed

**Example Policies**

*   Require MFA for all admins
*   Block access from unknown countries
*   Allow access only from compliant devices

* * *

## 5\. Managed Identities

> Identity for applications (no credentials)

**Example**

*   App accesses Key Vault
*   VM accesses storage

👉 No passwords needed

* * *

## 6\. Service Principals

> Identity for automation/tools

**Example**

*   Terraform
*   CI/CD pipelines

* * *

## 🔐 Zero Trust Model

### **Principles**

*   Verify explicitly
*   Use least privilege
*   Assume breach

### **What this means**

*   No implicit trust
*   No “internal = safe”
*   Identity is always verified


### **Real-World Design**

#### **Admin Access**

*   PIM enforced
*   MFA mandatory
*   audited access

#### **Developer Access**

*   scoped to their app
*   no production by default

#### **Application Access**


*   via managed identities
*   no hardcoded secrets


#### **External Access**


*   tightly controlled
*   conditional access enforced

* * *

### ⚠️ Common Mistakes

❌ Direct user role assignments

> 👉 leads to chaos

### ❌ Over-permission

> *   Owner everywhere
> *   Contributor everywhere

### ❌ No PIM

> 👉 permanent admin risk

* * *

#### ❌ Hardcoded secrets

> 👉 major security risk

#### ❌ Ignoring identity logs

> 👉 no visibility

* * *

## 🧠 Architect Thinking

You don’t ask:

“Who needs access?”

You ask:

“What is the minimum access required, under what conditions, for how long?"

> Identity is the new perimeter — design it like your primary security control

* * *

## 🔁 How It Connects

| Layer | Role |
| --- | --- |
| Network | Controls traffic |
| Identity | Controls access |
| Policy | Enforces compliance |

* * *

## What Comes Next

Now we move into:

🛡️ Security & Governance (Policy, Defender, Compliance)

Because:

> - Identity controls access  
> - Governance controls behavior

---

[⬅ Back to Series Home](index.md) |  [⬅ Back to: Network Design ➡](part5-network.md) | [Next: Security & Governance ➡](part7-governance.md)


