# 📘 Day 28 – Analog Inputs, Raw Values & Engineering Units

## 🎯 Learning Objective

Understand how PLC analog input modules receive signals from industrial instruments, convert them into raw values, and scale them into engineering units used for monitoring and control.

Today I am learning:

- Analog Input Modules
- Raw PLC Values
- Engineering Units
- Signal Scaling
- Sensor-to-PLC signal paths
- Real-world instrumentation examples

---

# 📖 What is an Analog Input Module?

An Analog Input (AI) module is a PLC hardware module that receives continuously varying electrical signals from industrial instruments.

Unlike digital inputs, which only detect ON or OFF states, analog inputs measure values that change continuously.

Common connected instruments include:

- Level transmitters
- Temperature transmitters
- Pressure transmitters
- Flow transmitters
- pH sensors
- Speed sensors

The analog input module acts as the bridge between the physical world and the PLC program.

---

# 🔄 How Analog Data Flows

A typical measurement follows this path:

```text
Tank Level
     │
     ▼
Level Transmitter
     │
 4–20 mA Signal
     │
     ▼
Analog Input Module
     │
     ▼
Raw PLC Value
     │
     ▼
Scaling
     │
     ▼
Engineering Value (75%)
     │
     ▼
SCADA Display
```

The PLC never sees "75%" directly—it first receives a raw value.

---

# 🔢 What is a Raw Value?

When the analog module receives an electrical signal, it converts it into a numerical value that the PLC can process.

For example, some PLC platforms use values similar to:

| Signal | Raw Value (Example) |
|---------|----------------------|
| Minimum | 0 |
| Half Scale | 13824 |
| Maximum | 27648 |

Different PLC manufacturers use different raw ranges, but the principle is the same.

---

# 📏 What are Engineering Units?

Engineering units are the real-world values operators and engineers actually want to see.

Examples:

| Measurement | Engineering Unit |
|-------------|------------------|
| Temperature | °C |
| Pressure | bar |
| Flow | L/min |
| Tank Level | % |
| Speed | RPM |

Instead of displaying:

```text
Raw Value = 20736
```

SCADA displays:

```text
Tank Level = 75%
```

This is much more useful during plant operations.

---

# 📊 Example: Level Scaling

Imagine a tank level transmitter.

- Measurement Range: **0–100%**
- Signal: **4–20 mA**

After conversion, the PLC scales the signal.

| Current | Level |
|---------|-------|
| 4 mA | 0% |
| 8 mA | 25% |
| 12 mA | 50% |
| 16 mA | 75% |
| 20 mA | 100% |

The PLC can now use these values in control logic.

---

# 🌡️ Example: Temperature Transmitter

Suppose a temperature transmitter measures:

```text
0–200°C
```

using:

```text
4–20 mA
```

The PLC scales the incoming signal.

Examples:

| Current | Temperature |
|---------|-------------|
| 4 mA | 0°C |
| 12 mA | 100°C |
| 20 mA | 200°C |

The PLC can now make decisions such as:

```text
Temperature > 180°C
      ↓
High Temperature Alarm
```

---

# ⚙️ Scaling Inside the PLC

The PLC generally performs three steps:

1. Read the analog signal.
2. Convert it into a raw value.
3. Scale it into engineering units.

Conceptually:

```text
Raw Value
     │
     ▼
Scaling Function
     │
     ▼
Engineering Value
```

The exact scaling instruction depends on the PLC platform being used.

---

# 🏭 Real-World Example: Water Treatment Plant

A storage tank uses a level transmitter.

The PLC reads:

```text
Raw Value
```

After scaling:

```text
Tank Level = 22%
```

The control logic becomes:

```text
Level < 25%
      ↓
Start Pump

Level > 80%
      ↓
Stop Pump
```

This combines:

- Analog inputs
- Scaling
- Comparators
- Ladder Logic

into one complete control sequence.

---

# ⚠️ Why Accurate Scaling Matters

Incorrect scaling can lead to serious problems.

For example:

- Incorrect tank level readings
- Wrong pressure values
- False alarms
- Equipment damage
- Poor process control

Engineers must verify both the transmitter range and the PLC scaling configuration.

---

# 💡 Key Takeaways

- Analog input modules receive continuous signals.
- PLCs first store analog signals as raw values.
- Raw values are converted into engineering units.
- Engineering units make process data meaningful.
- Proper scaling is essential for safe and accurate control.

---

# 🛠️ Practical Exercise

Design a temperature monitoring system.

Requirements:

- Temperature transmitter: **0–150°C**
- Signal: **4–20 mA**
- PLC analog input
- SCADA display
- High Temperature Alarm at **120°C**

Draw the complete signal path and explain how the PLC uses scaling before generating the alarm.

---

# 📋 Knowledge Check

1. What is an analog input module?

2. What is a raw PLC value?

3. Why are engineering units important?

4. What happens before a PLC displays "75%" on a SCADA screen?

5. Why is accurate scaling important?

6. Name three industrial instruments that use analog signals.

---

# 📚 References

- IEC 61131-3 – Programmable Controllers Programming Languages
- IEC 60381 – Analog Signals for Process Control Systems
- Siemens TIA Portal Documentation
- Rockwell Automation Studio 5000 Documentation
- Schneider Electric PLC Documentation

---

# ⏭️ Next Lesson

**Day 29 – Analog Output Modules and Controlling Real Equipment**

We'll explore:

- Analog output modules
- 4–20 mA outputs
- 0–10 V outputs
- Controlling valves
- Variable Frequency Drives (VFDs)
- Speed control
- Real industrial examples

---

> **"A sensor measures reality. Scaling helps the PLC understand it."**
