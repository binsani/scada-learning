# 📘 Day 37 – PLC Analog Control & Deadband

> 365 Days to SCADA Engineer — Day 37/365

Today I learned how PLCs can use analog process values in control logic.

So far, I learned how to:

- Read analog signals
- Scale raw values
- Convert signals into engineering units
- Detect abnormal analog signals

Today, the focus is on what happens **after the PLC has a valid analog value**.

One important concept is **deadband**.

---

## 🎯 Learning Objectives

By the end of this lesson, I should understand:

- How analog values can influence PLC control
- What deadband means
- Why hysteresis is useful
- How unnecessary output switching can happen
- The difference between an analog value and a control decision
- How deadband can be applied to simple process control

---

# 1. From Measurement to Control

Consider a water tank.

A level transmitter measures the tank:

```text
Tank
 ↓
Level Transmitter
 ↓
Analog Input
 ↓
PLC
 ↓
Control Decision
 ↓
Pump
