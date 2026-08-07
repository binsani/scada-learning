# 📘 Day 22 – PLC Contacts, Coils, and Basic Logic Operations

## 🎯 Learning Objective

Understand how PLCs use contacts and coils to create control logic and learn the three fundamental logic operations:

- AND Logic
- OR Logic
- NOT Logic

These concepts form the foundation of most industrial automation programs.

---

# 📖 Review: Contacts and Coils

Before learning logic operations, let's review the basic Ladder Logic elements.

## Normally Open (NO) Contact

```text
----[ ]----
```

Becomes TRUE when the input is active.

Examples:

- Push buttons
- Sensors
- Limit switches

---

## Normally Closed (NC) Contact

```text
----[/]----
```

Is TRUE until the input becomes active.

Examples:

- Emergency stop buttons
- Safety interlocks
- Fault conditions

---

## Output Coil

```text
----( )----
```

Represents the output controlled by the PLC.

Examples:

- Motor
- Pump
- Valve
- Alarm Light

---

# ⚙️ AND Logic

AND Logic means:

**All conditions must be TRUE before the output turns ON.**

Example:

A conveyor motor should start only when:

- Start button is pressed
- Safety gate is closed

Ladder Diagram:

```text
Start Button     Safety Gate       Motor

----[ ]------------[ ]------------( )----
```

Truth Table:

| Start | Safety Gate | Motor |
|---------|------------|--------|
| OFF | OFF | OFF |
| ON | OFF | OFF |
| OFF | ON | OFF |
| ON | ON | ON |

---

# ⚙️ OR Logic

OR Logic means:

**Any one condition can turn the output ON.**

Example:

A pump can be started by:

- Operator Push Button
OR
- Automatic Control Signal

Ladder Diagram:

```text
----[ ]----------------------------( )----
     |
     |
----[ ]----------------------------|
```

Truth Table:

| Push Button | Auto Signal | Pump |
|-------------|-------------|------|
| OFF | OFF | OFF |
| ON | OFF | ON |
| OFF | ON | ON |
| ON | ON | ON |

---

# ⚙️ NOT Logic

NOT Logic uses a Normally Closed contact.

Example:

The motor should run only if the Emergency Stop button is NOT pressed.

```text
Emergency Stop        Motor

----[/]----------------( )----
```

If the E-Stop is pressed, the motor turns OFF.

---

# 🧠 Combining Logic

Industrial systems often combine logic types.

Example:

```text
Start Button   Safety Gate   E-Stop

----[ ]----------[ ]----------[/]--------(Motor)
```

The motor runs only if:

- Start button is pressed
- Safety gate is closed
- Emergency stop is NOT pressed

---

# 🏭 Real-World Example

Imagine a water pumping station.

The pump starts only when:

- Tank level is low
AND
- Auto mode is enabled
AND
- No fault exists

Ladder Logic:

```text
Low Level   Auto Mode   No Fault

----[ ]--------[ ]--------[/]--------(Pump)
```

This simple logic is used in many industrial applications.

---

# 🔄 Internal Memory Bits

PLCs also use internal memory bits.

Examples:

```text
M0.0
B3:0/1
Memory_1
```

These bits:

- Store temporary information
- Create interlocks
- Remember system states
- Simplify complex logic

---

# 💡 Key Takeaways

- Contacts represent conditions.
- Coils represent outputs.
- AND Logic requires all conditions to be TRUE.
- OR Logic requires any one condition to be TRUE.
- NOT Logic uses Normally Closed contacts.
- Most PLC programs combine these logic types.

---

# 🛠️ Practical Exercise

Design Ladder Logic for a fan.

The fan starts when:

- Temperature is high
AND
- Auto mode is enabled
AND
- Emergency stop is not pressed

Draw the logic and explain how it works.

---

# 📝 Knowledge Check

1. What does a Normally Open contact represent?

2. What is the difference between AND and OR logic?

3. How is NOT logic implemented?

4. Why are internal memory bits useful?

5. When would you use a Normally Closed contact?

---

# 📚 References

- IEC 61131-3 – PLC Programming Languages
- Siemens TIA Portal Documentation
- Rockwell Automation Studio 5000
- Schneider Electric PLC Programming Guide

---

# ⏭️ Next Lesson

**Day 23 – PLC Latching Circuits and Seal-In Logic**

We'll explore:

- Start/Stop circuits
- Motor control logic
- Latching outputs
- Seal-in contacts
- Industrial control examples

---

> **"Complex industrial systems are built from simple logic operations combined intelligently."**
