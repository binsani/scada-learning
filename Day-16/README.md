# 📘 Day 16 – The Purdue Enterprise Reference Architecture (PERA)

## 🎯 Learning Objective

Understand the **Purdue Enterprise Reference Architecture (PERA)**, its different levels, and how it helps organize and secure industrial control systems.

---

# 📖 What is the Purdue Model?

The Purdue Model is a reference architecture used to organize industrial automation and control systems into different levels.

Each level has a specific purpose and defines how information flows between business systems and industrial equipment.

The model helps engineers:

- Design secure industrial networks
- Separate IT and OT environments
- Reduce cybersecurity risks
- Improve system reliability

It remains one of the most widely used architectures in industrial automation.

---

# 🏗️ Purdue Model Levels

## Level 0 – Physical Process

This is where the actual industrial process takes place.

Examples:

- Motors
- Pumps
- Valves
- Conveyor Belts
- Tanks
- Temperature Sensors
- Pressure Sensors
- Flow Meters

These devices interact directly with the physical world.

---

## Level 1 – Basic Control

Devices at this level monitor and control the physical process.

Examples:

- PLCs
- RTUs
- Remote I/O
- Motor Controllers

These devices receive information from Level 0 and control equipment accordingly.

---

## Level 2 – Supervisory Control

This level allows operators to monitor and supervise industrial operations.

Examples:

- HMIs
- SCADA Servers
- Operator Workstations
- Alarm Systems
- Historians

Operators can view system status and issue control commands from this level.

---

## Level 3 – Site Operations

This level manages plant operations.

Examples:

- Manufacturing Execution Systems (MES)
- Engineering Workstations
- Patch Management Servers
- Asset Management Systems
- Backup Servers

Level 3 bridges operational control and business operations.

---

## Level 3.5 – Industrial DMZ

The Industrial Demilitarized Zone (DMZ) separates operational technology (OT) from enterprise IT.

Typical systems include:

- Jump Servers
- Patch Management
- Update Servers
- Remote Access Gateways
- Data Historians
- Security Monitoring Systems

The DMZ helps reduce the risk of cyber threats moving between IT and OT environments.

---

## Level 4 – Enterprise IT

This level contains business systems.

Examples:

- Email Servers
- ERP Systems
- HR Systems
- Financial Applications
- Corporate Databases
- Office Computers

These systems support business operations rather than industrial control.

---

## Level 5 – External Networks

This includes connections outside the organization.

Examples:

- Internet
- Cloud Services
- Remote Vendors
- Business Partners
- Customer Portals

These networks require strong security controls before connecting to enterprise systems.

---

# 🏭 Purdue Model Overview

```text
+---------------------------------------+
| Level 5 | Internet / Cloud            |
+---------------------------------------+
| Level 4 | Enterprise IT               |
+---------------------------------------+
| Level 3.5 | Industrial DMZ            |
+---------------------------------------+
| Level 3 | Site Operations (MES)       |
+---------------------------------------+
| Level 2 | SCADA / HMI                 |
+---------------------------------------+
| Level 1 | PLCs / RTUs / Controllers   |
+---------------------------------------+
| Level 0 | Sensors & Physical Process  |
+---------------------------------------+
```

---

# 🌍 Real-World Example

Imagine a bottling factory.

- Level 0: Sensors measure bottle position and liquid level.
- Level 1: PLCs control conveyors and filling machines.
- Level 2: SCADA displays production status to operators.
- Level 3: MES tracks production orders and equipment performance.
- Level 3.5: The DMZ securely transfers approved data between OT and IT.
- Level 4: ERP manages inventory and customer orders.
- Level 5: Cloud dashboards provide business analytics.

Each level has a different responsibility, helping keep industrial operations organized and secure.

---

# 🔐 Why the Purdue Model Matters

The Purdue Model helps organizations:

- Separate critical control systems from business networks
- Reduce cyber risk
- Simplify network design
- Support compliance with security standards
- Improve operational resilience

Although modern architectures continue to evolve, the Purdue Model remains a valuable framework for understanding industrial environments.

---

# 💡 Key Takeaways

- The Purdue Model organizes industrial systems into functional levels.
- Lower levels interact directly with physical equipment.
- Higher levels focus on business operations.
- The Industrial DMZ helps separate IT and OT networks.
- Proper network segmentation improves cybersecurity.

---

# 🛠️ Practical Exercise

Imagine you are designing the network for a manufacturing plant.

Answer the following:

1. Which Purdue level contains PLCs?
2. Where would you place the SCADA server?
3. Why is the Industrial DMZ important?
4. Which systems belong in the Enterprise IT level?

Write your answers before moving to Day 17.

---

# 📝 Knowledge Check

1. What is the Purdue Enterprise Reference Architecture?

2. Which level contains the physical process?

3. Which level contains PLCs and RTUs?

4. What is the purpose of the Industrial DMZ?

5. Which level contains ERP and email systems?

---

# 📚 References

- ISA/IEC 62443 Series – Industrial Automation and Control Systems Security
- NIST SP 800-82 – Guide to Industrial Control Systems (ICS) Security
- Purdue University – Purdue Enterprise Reference Architecture (PERA)
- CISA – Industrial Control Systems Security Resources
- SANS Institute – ICS Security

---

# ⏭️ Next Lesson

**Day 17 – SCADA Alarms and Event Management**

We'll explore:

- What alarms are
- Alarm priorities
- Alarm lifecycle
- Alarm flooding
- Alarm rationalization
- ISA-18.2 overview

---

> **"A well-designed industrial network doesn't happen by accident—it follows a structured architecture that separates, secures, and simplifies operations."**
