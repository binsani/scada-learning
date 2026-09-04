# 📘 Day 36 – PLC Analog Signal Faults & Diagnostics

> 365 Days to SCADA Engineer — Day 36/365

Today I moved from **analog signal scaling** to something every real industrial system needs:

**Analog signal fault detection and diagnostics.**

In a real plant, receiving an analog value is not enough.

The PLC also needs to help determine:

- Is the signal valid?
- Is the sensor disconnected?
- Is the signal outside the expected range?
- Is the value physically possible?
- Should the control logic trust this value?

---

## 🎯 Learning Objectives

By the end of this lesson, I should understand:

- Common analog signal faults
- How PLCs detect abnormal analog values
- 4–20 mA fault conditions
- Out-of-range signals
- Sensor wire-break detection
- Signal validation
- Engineering limits
- Why diagnostics are important in SCADA

---

# 1. Why Analog Diagnostics Matter

Consider a water tank with a level transmitter.

The transmitter sends the tank level to the PLC.

```text
Level Transmitter
       ↓
Analog Input
       ↓
PLC
       ↓
SCADA
