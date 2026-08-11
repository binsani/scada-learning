# 📘 Day 27 – Analog Signals & Signal Scaling

## 🎯 Learning Objective

Understand how PLCs receive continuous measurements from industrial instruments and convert raw analog signals into meaningful engineering values.

Today I am learning:

- Digital vs Analog signals
- 4–20 mA
- 0–10 V
- Analog Input Modules
- Raw PLC values
- Signal Scaling
- Engineering Units
- Real-world instrumentation

---

# 📖 What is an Analog Signal?

An analog signal represents a continuously varying physical measurement.

Unlike a digital signal, which normally has discrete states such as:

```text
ON / OFF
1 / 0
```

an analog signal can represent a range of values.

Examples include:

- Temperature
- Pressure
- Tank level
- Flow
- Speed
- pH
- Position

---

# 🔌 Digital vs Analog

## Digital Signal

A digital input might represent:

```text
0 = OFF

1 = ON
```

Example:

A pump running-status contact.

---

## Analog Signal

An analog input represents a range.

For example:

```text
4–20 mA
```

could represent:

```text
0% → 100% tank level
```

This allows the PLC to know the actual process value rather than simply knowing whether something is ON or OFF.

---

# 📡 The 4–20 mA Signal

The **4–20 mA current loop** is widely used for industrial instrumentation.

A simplified example:

```text
4 mA  →  0%
12 mA →  50%
20 mA →  100%
```

For a tank level transmitter:

```text
Tank Level
    │
    ▼
Level Transmitter
    │
    │ 4–20 mA
    ▼
PLC Analog Input
    │
    ▼
Raw Value
    │
    ▼
Scaling
    │
    ▼
Engineering Value
    │
    ▼
75% Level
```

The exact raw values depend on the PLC hardware and configuration.

---

# ⚡ 0–10 V

Another common analog signal is:

```text
0–10 V
```

For example:

```text
0 V  →  0%
5 V  →  50%
10 V →  100%
```

It can be used for applications such as:

- Speed references
- Position
- Temperature
- Pressure
- Level

The choice between current and voltage signaling depends on the instrumentation, distance, environment, and system design.

---

# 🧠 Why Does the PLC Need Scaling?

The PLC's analog input module normally converts the electrical signal into a numerical value.

The PLC may therefore receive something like:

```text
Raw Input = 27648
```

instead of:

```text
Tank Level = 75%
```

The program then scales the raw input into an engineering value that operators and control logic can use.

---

# 🔄 Signal Scaling

Signal scaling converts a raw PLC value into a meaningful engineering value.

For example:

```text
Raw PLC Value
      ↓
   Scaling
      ↓
Tank Level (%)
```

Suppose a system is configured so that:

```text
Raw Minimum = 0
Raw Maximum = 27648

Engineering Minimum = 0%
Engineering Maximum = 100%
```

Then the PLC can convert the raw value into a percentage.

---

# 🧮 Basic Scaling Concept

A general linear scaling relationship can be represented as:

```text
Engineering Value =
( Raw Value - Raw Min )
----------------------- ×
( Engineering Max - Engineering Min )
+ Engineering Min
        Raw Max - Raw Min
```

The actual implementation depends on the PLC platform and configuration.

---

# 🏭 Example: Tank Level

Imagine a tank level transmitter measuring:

```text
0–100%
```

and transmitting:

```text
4–20 mA
```

The PLC receives the signal through an analog input module.

The control system can then interpret the measurement as:

```text
4 mA  →  0%
8 mA  →  25%
12 mA →  50%
16 mA →  75%
20 mA →  100%
```

The PLC can now use the level value in control logic.

For example:

```text
Level < 25%
      ↓
Start Pump

Level > 80%
      ↓
Stop Pump
```

This connects today's topic directly to the comparator logic learned on Day 26.

---

# 🔗 Connecting Multiple PLC Concepts

We can now combine several concepts learned during this journey.

```text
Level Transmitter
       │
       │ 4–20 mA
       ▼
Analog Input
       │
       ▼
Signal Scaling
       │
       ▼
Tank Level = 22%
       │
       ▼
Comparator
       │
       ▼
Level < 25%
       │
       ▼
PLC Logic
       │
       ▼
Pump ON
```

This is much closer to how an actual industrial control process can be structured.

---

# ⚠️ Important Engineering Concept: 4 mA Is Not Zero

One important characteristic of the 4–20 mA standard is that the live-zero value is normally **4 mA**, not 0 mA.

This provides useful diagnostic information.

For example:

```text
Normal minimum process value
        ↓
      4 mA
```

A significantly lower current can indicate a problem with the signal loop or instrumentation, depending on the system and configured fault handling.

The exact fault thresholds and diagnostic behaviour depend on the transmitter, input module, and control system.

---

# 🛠️ Practical Exercise

Design a tank level measurement system.

### Requirements

A level transmitter measures:

```text
0–100% tank level
```

The transmitter outputs:

```text
4–20 mA
```

The PLC receives the signal through an analog input.

Your task:

1. Draw the signal path.
2. Identify the analog input module.
3. Explain why scaling is required.
4. Convert the following signals conceptually:

```text
4 mA
8 mA
12 mA
16 mA
20 mA
```

into percentage values.

5. Explain how the resulting level value could be used by the PLC to control a pump.

---

# 📊 Exercise Table

Complete this table:

| Current | Tank Level |
|---------|------------|
| 4 mA | ? |
| 8 mA | ? |
| 12 mA | ? |
| 16 mA | ? |
| 20 mA | ? |

---

# 📝 Knowledge Check

1. What is the difference between a digital and analog signal?

2. What does 4–20 mA represent?

3. Why is signal scaling necessary?

4. What does an analog input module do?

5. What is the purpose of engineering units?

6. Why is 4 mA commonly used as the lower end of a 4–20 mA signal?

7. Give three industrial measurements that can be transmitted using analog signals.

8. How could a scaled tank-level value be used with a PLC comparator?

---

# 💡 Key Takeaways

- Digital signals normally represent discrete states.
- Analog signals represent continuously varying measurements.
- 4–20 mA is widely used for industrial instrumentation.
- 0–10 V is another common analog signaling method.
- PLC analog input modules convert electrical signals into values the PLC can process.
- Scaling converts raw PLC values into meaningful engineering units.
- Analog values can be combined with comparators and control logic.

---

# 📚 References

- IEC 61131-3 – Programmable Controllers Programming Languages
- IEC 60381 – Analog Signals for Process Control Systems
- Siemens TIA Portal Documentation
- Rockwell Automation Documentation
- Schneider Electric PLC Documentation

---

# ⏭️ Next Lesson

**Day 28 – Analog Inputs, Raw Values & Engineering Units**

We'll go deeper into:

- Analog input modules
- Raw values
- Engineering units
- Input ranges
- Scaling examples
- Sensor-to-PLC signal paths
- Practical instrumentation scenarios

---

> **"A sensor measures the process. The PLC turns that measurement into a decision."**
