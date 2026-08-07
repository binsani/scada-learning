# 📘 Day 21 – Introduction to PLC Programming (Ladder Logic)

## 🎯 Learning Objective

Understand what **Ladder Logic** is, why it is the most common PLC programming language, and learn the basic building blocks used to create industrial control programs.

---

# 📖 What is Ladder Logic?

Ladder Logic (LAD) is a graphical programming language used to program Programmable Logic Controllers (PLCs).

It was designed to resemble traditional electrical relay circuits, making it easier for electricians and control engineers to transition from relay-based systems to PLCs.

Today, Ladder Logic remains one of the most widely used PLC programming languages in industrial automation.

---

# 🏭 Why is Ladder Logic Used?

Ladder Logic is popular because it is:

- Easy to read
- Easy to troubleshoot
- Familiar to electricians
- Supported by most PLC manufacturers
- Reliable for industrial control applications

It is commonly used in:

- Manufacturing plants
- Water treatment facilities
- Oil & Gas
- Food processing
- Building automation
- Packaging lines

---

# 🪜 Understanding the Ladder

A Ladder Logic program resembles a ladder.

```text
 Left Rail                    Right Rail
     |                              |
     |----[ ]-----------( )---------|
     |                              |
```

- **Left Rail** → Represents the power source.
- **Right Rail** → Represents the return path.
- **Horizontal lines** are called **rungs**.
- Each rung contains logic that controls an output.

The PLC evaluates each rung from **left to right** and **top to bottom** during every scan cycle.

---

# 🔌 Basic Ladder Logic Elements

## Normally Open (NO) Contact

Symbol:

```text
----[ ]----
```

Represents an input that becomes TRUE when activated.

Example:

- Push Button
- Limit Switch
- Sensor

---

## Normally Closed (NC) Contact

Symbol:

```text
----[/]----
```

Represents an input that is TRUE until activated.

Commonly used for:

- Emergency Stop buttons
- Safety circuits
- Fault conditions

---

## Output Coil

Symbol:

```text
----( )----
```

Represents an output device controlled by the PLC.

Examples:

- Motor
- Pump
- Solenoid Valve
- Indicator Lamp

---

# 🧠 Simple Start Button Example

Imagine a push button controlling a motor.

```text
Start Button          Motor

----[ ]----------------( )----
```

How it works:

- Button NOT pressed → Motor OFF
- Button pressed → Motor ON

The PLC continuously checks the button during each scan cycle.

---

# 🏭 Real-World Example

Imagine a water pumping station.

A level sensor detects that the water level has dropped below 30%.

The PLC receives the signal and energizes the pump.

Simplified logic:

```text
Low Level Sensor      Water Pump

----[ ]----------------( )----
```

When the tank refills above the required level, the PLC turns the pump OFF.

---

# ⚙️ PLC Scan Cycle Reminder

Every PLC continuously repeats these steps:

```text
Read Inputs
      │
      ▼
Execute Ladder Logic
      │
      ▼
Update Outputs
      │
      ▼
Repeat
```

This happens many times every second.

---

# 💡 Key Takeaways

- Ladder Logic is the most widely used PLC programming language.
- It is based on traditional relay control diagrams.
- Programs are built using contacts, coils, and rungs.
- PLCs execute Ladder Logic continuously during each scan cycle.
- Ladder Logic is designed to make industrial control easy to understand and maintain.

---

# 🛠️ Practical Exercise

Design a simple Ladder Logic program that controls a cooling fan.

Requirements:

- A temperature sensor acts as the input.
- The cooling fan acts as the output.
- The fan starts when the temperature becomes too high.

Draw the ladder diagram and explain how it works.

---

# 📝 Knowledge Check

1. What is Ladder Logic?

2. Why was Ladder Logic designed to resemble electrical relay circuits?

3. What is the purpose of a Normally Open contact?

4. What does an Output Coil represent?

5. In what order does the PLC execute Ladder Logic?

---

# 📚 References

- IEC 61131-3 – PLC Programming Languages
- Siemens TIA Portal Documentation
- Rockwell Automation Studio 5000 Documentation
- Schneider Electric EcoStruxure Machine Expert
- AutomationDirect PLC Programming Guide

---

# ⏭️ Next Lesson

**Day 22 – PLC Contacts, Coils, and Basic Logic Operations**

We'll explore:

- Series Logic (AND)
- Parallel Logic (OR)
- NOT Logic
- Internal Memory Bits
- Practical Ladder Logic examples

---

> **"Every automated machine begins with logic. Master the logic, and you can control the process."**
