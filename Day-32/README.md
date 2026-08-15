# 📘 Day 32 – PLC Fault Handling & Diagnostics

## 🎯 Learning Objective

Today I am learning how PLC-based control systems detect, handle, and respond to abnormal conditions.

The focus is on:

- Fault detection
- Fault states
- Equipment faults
- Diagnostic signals
- Fault handling
- Fault reset
- Troubleshooting PLC sequences
- Understanding the difference between a fault and an alarm

---

# 📖 What is a PLC Fault?

A fault is an abnormal condition that can affect the operation of a machine, process, or control system.

Examples include:

- Motor overload
- Communication failure
- Sensor failure
- Valve failure
- Pump failure
- Loss of required feedback
- PLC hardware problems
- Unexpected process conditions

The PLC or associated control system can detect defined fault conditions and take the appropriate programmed response.

---

# 🔍 Fault Detection

A PLC can monitor signals and determine whether something has gone wrong.

For example:

```text
Pump Command = ON
        ↓
Expected Pump Feedback = ON
        ↓
Feedback NOT Received
        ↓
FAULT CONDITION
