# 📘 Day 41 – PLC Data Structures & UDTs

> 365 Days to SCADA Engineer — Day 41/365

Today I learned how PLC programmers organize related information into structured data.

Yesterday, I learned about:

- BOOL
- INT
- DINT
- REAL
- PLC tags
- Inputs
- Outputs
- Commands
- Feedback
- Internal variables

But imagine a plant with 50 pumps.

Creating and managing hundreds of unrelated tags can quickly become difficult.

This is where **data structures** and **User-Defined Data Types (UDTs)** become useful.

---

## 🎯 Learning Objectives

By the end of this lesson, I should understand:

- What a PLC data structure is
- What a UDT is
- Why related tags can be grouped together
- How structures improve program organization
- How structures can represent equipment
- How UDTs can support reusable PLC programming
- Why structured data is useful for SCADA integration

---

# 1. The Problem With Too Many Individual Tags

Imagine a plant has one pump.

We might have:

```text
Pump01_StartCommand
Pump01_StopCommand
Pump01_RunFeedback
Pump01_Fault
Pump01_AutoMode
Pump01_Runtime
Pump01_Speed
