# 📘 Day 13 – Network Redundancy in SCADA Systems

## 🎯 Learning Objective

Understand what **network redundancy** is, why it is important in industrial automation, and how it helps maintain reliable communication in SCADA systems.

---

# 📖 What is Network Redundancy?

Network redundancy is the practice of creating **backup communication paths** so that industrial devices can continue communicating even if part of the network fails.

Instead of relying on a single communication path, redundant networks provide alternative routes for data.

This helps prevent downtime and improves the reliability of industrial operations.

---

# 🤔 Why is Network Redundancy Important?

Many industrial facilities operate **24 hours a day, 7 days a week**.

If communication between a PLC and the SCADA server is lost, operators may lose visibility of the process, alarms may not be reported, and production could stop.

Network redundancy helps reduce these risks.

Benefits include:

- Increased reliability
- Reduced downtime
- Improved system availability
- Better fault tolerance
- Safer industrial operations

---

# ⚠️ What Happens Without Redundancy?

Imagine a factory where every PLC communicates through a single Ethernet cable.

If that cable is accidentally cut:

- PLCs become isolated
- Operators lose visibility
- Alarms stop updating
- Production may halt

A single point of failure can affect the entire system.

---

# 🔄 Common Redundancy Topologies

## 1. Ring Topology

Each network device connects to two neighbouring devices, forming a loop.

```text
PLC ─── Switch ─── HMI
│                 │
│                 │
SCADA ─── Switch ── RTU
```

If one communication link fails, traffic can travel in the opposite direction.

---

## 2. Dual Network

Critical devices connect to two independent networks.

```text
        Network A
PLC ─────────────── SCADA

        Network B
PLC ─────────────── SCADA
```

If one network fails, the other continues operating.

---

## 3. Redundant Switches

Large industrial systems often deploy two core switches.

If one switch fails, communication automatically continues through the backup switch.

---

# 🛠️ Redundancy Protocols

Several protocols support network redundancy.

### Rapid Spanning Tree Protocol (RSTP)

- Prevents switching loops
- Quickly restores communication after a failure

---

### Media Redundancy Protocol (MRP)

- Common in PROFINET networks
- Detects failures and restores communication rapidly

---

### Device Level Ring (DLR)

- Common in EtherNet/IP networks
- Creates a resilient ring network
- Minimises communication interruptions

---

# 🏭 Real-World Example

Imagine a water treatment plant.

Two industrial Ethernet switches are connected in a ring.

During maintenance, one fibre optic cable is accidentally disconnected.

Because the network is redundant:

- PLCs remain online
- SCADA continues receiving data
- Operators maintain visibility
- Water production continues safely

Without redundancy, communication could be interrupted until the fault is repaired.

---

# 📊 Redundant Network Example

```text
                SCADA Server
                     │
              Managed Switch A
              /               \
           PLC                 HMI
              \               /
              Managed Switch B
                     │
                    RTU
```

If one communication path fails, data can travel through the alternative path.

---

# 💡 Key Takeaways

- Redundancy provides backup communication paths.
- It improves system reliability and availability.
- Ring networks are commonly used in industrial automation.
- Redundancy protocols help networks recover quickly after failures.
- Eliminating single points of failure is a key design principle.

---

# 🛠️ Practical Exercise

Imagine you are designing the network for a power substation.

Answer the following:

1. Which redundancy topology would you choose?
2. Why is redundancy important in this environment?
3. What could happen if there were no backup communication path?
4. Which devices would benefit most from redundant connections?

Write your answers before moving to Day 14.

---

# 📝 Knowledge Check

1. What is network redundancy?

2. Why is redundancy important in SCADA systems?

3. Name two redundancy protocols used in industrial networks.

4. What is a single point of failure?

5. How does a ring topology improve network reliability?

---

# 📚 References

- Cisco – Industrial Network Design Guide
- Siemens – PROFINET System Description
- ODVA – EtherNet/IP and Device Level Ring (DLR)
- Schneider Electric – EcoStruxure Network Architecture
- NIST SP 800-82 – Guide to Industrial Control Systems (ICS) Security

---

# ⏭️ Next Lesson

**Day 14 – Introduction to Industrial Cybersecurity**

We'll explore:

- What Industrial Cybersecurity is
- Why Operational Technology (OT) security matters
- Common cyber threats to SCADA systems
- Basic security principles
- The CIA Triad in industrial environments

---

> **"In industrial automation, reliability isn't optional. Redundancy ensures the process continues even when failures occur."**
