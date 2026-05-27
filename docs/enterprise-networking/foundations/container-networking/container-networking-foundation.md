---
layout: default
title: Lab-1|Container Networking Foundation
---

## Understanding Container Networking from First Principles

---

In the previous chapter, we explored what actually powers containers — how isolation is created using namespaces and how resource control is enforced using cgroups.

This lab builds on that foundation by focusing on one specific aspect **Network isolation and connectivity**

Container networking is not a new networking model. It is Linux networking applied within isolated environments and then connected using virtual constructs.

The goal of this lab is to understand how that connectivity is created from first principles.

---

# Lab 1 - Container Networking Foundation

**Understanding Container Networking from First Principles with Linux Network Namespaces**

When people first hear terms like _container networking_, _Kubernetes networking_, or _pod-to-pod communication_, it often sounds like a new and specialized domain. In reality, the foundation is much simpler *Container networking is largely Linux networking with isolation and virtual connectivity.*

This lab is designed to build that understanding from first principles. The goal is not to become a Linux networking specialist. The goal is to clearly understand what is happening underneath containers and Kubernetes so that later concepts feel logical instead of magical.

**What This Lab Teaches**

By the end of this lab, you should understand:

- how network namespaces isolate networking
- why isolated environments cannot communicate by default
- how veth pairs create connectivity
- how IP addressing works inside a namespace
- why ARP and routing still apply even in isolated environments
    

---

## Core Concept 1: Network Namespace in Context

---

A network namespace is one of the isolation mechanisms discussed in the foundation chapter.

It specifically isolates the networking stack of a process.

Each network namespace has its own:

- network interfaces
- IP addresses
- routing table
- ARP (neighbor) table

This means that even though multiple namespaces exist on the same Linux system, they behave like independent network environments.

At this point, it is important to connect this back to containers:

A container uses multiple namespaces together, but in this lab, we are isolating and exploring only the network namespace to understand its behavior in detail.

---

## Core Concept 2: Why Communication Does Not Exist by Default

---

When two namespaces are created, they are isolated from each other. The important point is not just that they have separate IP space. The more fundamental reason is *There is no interface, no link, and no path between them.*

So even though both namespaces exist on the same Linux machine, Linux treats them as separate network stacks. This is one of the most important ideas in container networking *Connectivity is not assumed. It must be explicitly created.*

---

## Core Concept 3: What is a veth Pair?

---

A **veth pair** means **virtual Ethernet pair**. It is a Linux construct that behaves like a virtual cable with two ends. If a packet enters one end of the pair, it appears on the other end. That makes it a perfect way to connect two isolated namespaces. You can think of it as:
>
> [namespace 1] <=======> [namespace 2]
>

In Linux terminology, that virtual cable is the **veth pair**. Within Linux-based container environments, this is standard terminology and a standard mechanism.

---

## Lab Topology

**Figure**: Connectivity between two network namespaces using a veth pair.

![Lab 1 Topology]({{ "/assets/images/lab1-topology.png" | relative_url }})    

Here:

- *ns1* and *ns2* are network namespaces    
- veth-ns1 and veth-ns2 are the two ends of the virtual link    
- both ends are placed in the same subnet so they can communicate directly

---

### **Step 1: Create Two Network Namespaces**

```text
sudo ip netns add ns1
sudo ip netns add ns2
ip netns list   `
```
**What this does**

This creates two isolated network environments:
- ns1    
- ns2
    

At this point, they exist, but they are not connected to each other.

**What to understand**

This is the first important lesson *Isolation comes first. Connectivity comes later.* If you stop here, the namespaces cannot communicate, because no interfaces or routes exist between them.


### **Step 2: Create a veth Pair**

```text
sudo ip link add veth-ns1 type veth peer name veth-ns2
```

**What this does**

This creates a pair of virtual interfaces:

- veth-ns1    
- veth-ns2

These two interfaces are linked together internally by the Linux kernel.

**What to understand**

This is not just an interface. It is a connected pair. If traffic enters veth-ns1, it can exit through veth-ns2, and vice versa.

At this stage, both interfaces still exist in the host namespace, not yet inside ns1 or ns2.


### **Step 3: Move Each End into a Namespace**

```text
sudo ip link set veth-ns1 netns ns1
sudo ip link set veth-ns2 netns ns2   `
```
**What this does**

Now each namespace gets one side of the virtual cable:

- ns1 gets veth-ns1    
- ns2 gets veth-ns2
    

**What to understand**

The topology now becomes:

```text
ns1                      ns2
-----                    -----
veth-ns1  <=======>  veth-ns2
```

This is the point where the namespaces now have a physical path between them, but they still do not have IP addresses yet.


### **Step 4: Assign IP Addresses**

```text
 sudo ip netns exec ns1 ip addr add 10.0.0.1/24 dev veth-ns1
 sudo ip netns exec ns2 ip addr add 10.0.0.2/24 dev veth-ns2
```
**What this does**

This assigns IP addresses to the interfaces inside the namespaces:

- ns1 gets 10.0.0.1/24
- ns2 gets 10.0.0.2/24
    

**What to understand**

An important clarification here *IP addresses belong to interfaces, not directly to containers or processes.* So when people say "a container has an IP," what they usually mean is *the network interface inside that container's namespace has an IP*. That distinction is important because it explains why multiple processes inside the same namespace can share the same network identity.


### **Step 5: Bring the Interfaces Up**

```text
sudo ip netns exec ns1 ip link set veth-ns1 up
sudo ip netns exec ns2 ip link set veth-ns2 up
sudo ip netns exec ns1 ip link set lo up
sudo ip netns exec ns2 ip link set lo up
```

**What this does**

This enables the interfaces. By default, newly created interfaces are typically down. A down interface cannot send or receive traffic. The *lo interface* is the loopback interface, used for local communication inside the namespace.

**What to understand**

Without this step, even correctly addressed interfaces still will not communicate. This is similar to a cable being present but the interface itself being administratively down.

### **Step 6: Test Connectivity**

```text
sudo ip netns exec ns1 ping 10.0.0.2
```
**What this does**

This sends ICMP packets from ns1 to ns2.

**What to understand**

If this works, Linux has successfully done all of the following:

- checked the routing decision    
- resolved the destination MAC address using ARP    
- sent the packet through veth-ns1    
- delivered the packet to veth-ns2    
- received the reply back
    
This proves that the two isolated network namespaces are now able to communicate.

**Important Concept: What Does exec Mean Here?**

In commands like this:
```text
sudo ip netns exec ns1 ping 10.0.0.2
```
the word exec means *run this command inside the given namespace*. So this does not permanently move your shell into ns1. It simply runs one command using the network context of ns1. This is why the command behaves as though it is originating from inside that namespace.

### **Step 7: Inspect the Interfaces**

 sudo ip netns exec ns1 ip link
 sudo ip netns exec ns2 ip link

**What to look for**

You may see output like this:
```text
2: veth-ns1@if3: <BROADCAST,MULTICAST,UP,...>
```

**What this means**

This shows that the interface is paired with another interface. That pairing is what makes the veth link work.

**What to understand**

This confirms the core idea *a veth pair acts like a two-ended virtual Ethernet cable*

### **Step 8: Check the Routing Table**

```text
sudo ip netns exec ns1 ip route
sudo ip netns exec ns2 ip route   `
```

**Example output**

10.0.0.0/24 dev veth-ns1 proto kernel scope link src 10.0.0.1

**How to read it**

- 10.0.0.0/24 is the destination subnet    
- dev veth-ns1 means use this interface    
- scope link means the destination is directly reachable on that link    
- src 10.0.0.1 is the preferred source IP for this route

**What to understand**

This is a critical point. Even though the two namespaces are in the same subnet, Linux still makes a routing decision. In a Linux system, the kernel checks the routing table to determine which interface should be used. So although this feels similar to same-subnet switching in traditional networks, the Linux kernel is still using routing logic to decide packet delivery.

A precise way to say it is *The Linux kernel makes a routing decision and then uses neighbor resolution to deliver the packet directly on the connected link.*

### **Step 9: Check the ARP or Neighbor Table**

```text
sudo ip netns exec ns1 ip neigh
sudo ip netns exec ns2 ip neigh
```

**What this shows**

This displays the **neighbor table**, which is the Linux equivalent of the ARP cache for IPv4.

Example:

```text
10.0.0.2 dev veth-ns1 lladdr aa:bb:cc:dd:ee:ff REACHABLE
```

**What to understand**

ARP is still relevant here. When ns1 wants to send traffic to 10.0.0.2, it first needs the destination MAC address. If it does not already know it, it sends an ARP request. Once the MAC is learned, Linux stores it in the neighbor table.

This means:

- the first communication may require ARP resolution
    
- repeated communication does not need repeated broadcast, because the result is cached. That is why ARP is still important, even in a virtual network built on one machine.

### **Step 10: Observe Live Traffic**

In one terminal: *sudo ip netns exec ns2 tcpdump -i veth-ns2*

In another terminal: *sudo ip netns exec ns1 ping 10.0.0.2*

**What this does**

This lets you watch packets arrive live on the interface inside ns2.

**What to understand**

This is one of the most useful observations in the lab. It proves that this is not an abstract or logical-only model. Actual packets are being sent and received through Linux networking constructs.

**What Happens Internally When ns1 Pings ns2**

A simplified sequence looks like this:

1.  ns1 wants to reach 10.0.0.2
    
2.  the Linux kernel in ns1 checks the routing table
    
3.  it determines that the destination is directly reachable using veth-ns1
    
4.  if needed, ARP resolves the destination MAC
    
5.  the packet is sent through veth-ns1
    
6.  the Linux kernel passes it across the paired veth interface
    
7.  veth-ns2 receives the packet inside ns2
    
8.  ns2 responds back through the same path
    
>
> This is the foundation of local container communication.
>

---

## **Why This Lab Matters for Containers and Kubernetes**

---


This lab is small, but the ideas are foundational. In Linux-based container platforms:

- isolation is created using namespaces
    
- connectivity is created using virtual interfaces
    
- IP addresses live on interfaces
    
- Linux kernel handles routing and neighbor resolution
    
- packet flow is real, even when the environment is virtual
    

This is why a useful mental model is *Containers are not magical network entities. They are processes running inside isolated Linux networking constructs.*

And at a broader level *Kubernetes networking is largely Linux networking automated at scale.*

**Key Takeaways**

1\. A network namespace is an isolated network environment - It has its own interfaces, IP addresses, routes, and ARP state.

2\. Isolation is the default - Two namespaces cannot communicate unless explicitly connected.

3\. A veth pair is a virtual cable - It provides direct connectivity between isolated namespaces.

4\. IP addresses belong to interfaces -A process or container uses the namespace's interface and its IP.
5\. Routing and ARP still matter - Even in a virtual container-like setup, Linux still uses routing and neighbor resolution.

6\. The Linux kernel is doing the real work - The kernel is responsible for packet delivery, ARP cache management, interface state, and routing decisions.


**A Clean Final Mental Model**

If you want one clear sentence to carry forward from this lab, let it be this *A container or pod network is not a special kind of network. It is an isolated Linux network stack connected through virtual interfaces and managed by the kernel.*

**Commands Used in This Lab**

```text
sudo ip netns add ns1
sudo ip netns add ns2
ip netns list

sudo ip link add veth-ns1 type veth peer name veth-ns2

sudo ip link set veth-ns1 netns ns1
sudo ip link set veth-ns2 netns ns2

sudo ip netns exec ns1 ip addr add 10.0.0.1/24 dev veth-ns1
sudo ip netns exec ns2 ip addr add 10.0.0.2/24 dev veth-ns2

sudo ip netns exec ns1 ip link set veth-ns1 up
sudo ip netns exec ns2 ip link set veth-ns2 up
sudo ip netns exec ns1 ip link set lo up
sudo ip netns exec ns2 ip link set lo up

sudo ip netns exec ns1 ping 10.0.0.2

sudo ip netns exec ns1 ip link
sudo ip netns exec ns2 ip link

sudo ip netns exec ns1 ip route
sudo ip netns exec ns2 ip route

sudo ip netns exec ns1 ip neigh
sudo ip netns exec ns2 ip neigh

sudo ip netns exec ns2 tcpdump -i veth-ns2
```
---

[⬅ Back to Series Home](index.md) | [⬅ Back to What Powers Containers](what-powers-containers.md) | 