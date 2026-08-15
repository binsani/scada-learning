# 📘 Day 33 – PLC Troubleshooting & Diagnostic Thinking

## 🎯 Learning Objective

Today I am learning how to approach PLC troubleshooting systematically instead of guessing.

The focus is on:

- Troubleshooting methodology
- Following the control path
- Checking inputs and outputs
- Verifying PLC logic
- Checking field devices
- Using feedback signals
- Diagnosing communication problems
- Separating symptoms from root causes

---

# 🧠 What is PLC Troubleshooting?

PLC troubleshooting is the process of identifying why a control system is not behaving as expected.

A good troubleshooting process should answer:

> What was supposed to happen?

Then:

> What actually happened?

And finally:

> Where did the expected sequence break?

---

# 🔄 Follow the Control Path

A useful approach is to trace the complete signal path:

```text
Operator Command
       ↓
PLC Input
       ↓
PLC Logic
       ↓
PLC Output
       ↓
Field Device
       ↓
Process
       ↓
Feedback
       ↓
PLC Input
       ↓
SCADA / HMI
