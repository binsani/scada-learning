# 📘 Day 26 – PLC Comparators and Conditional Logic

## 🎯 Learning Objective

Understand how PLCs compare values and use the results to make decisions in industrial control systems.

Today I am learning:

- Equal To
- Not Equal To
- Greater Than
- Less Than
- Greater Than or Equal To
- Less Than or Equal To
- Conditional control using process values

---

# 📖 What is a PLC Comparator?

A PLC comparator evaluates two values and determines whether a specific condition is TRUE or FALSE.

For example:

```text
Tank Level > 80%
```

If the tank level is 85%, the condition is TRUE.

If the tank level is 70%, the condition is FALSE.

The PLC can then use that result to control another part of the process.

---

# 🔢 Why Comparators Matter

Industrial processes constantly deal with numerical values.

Examples include:

- Tank level
- Temperature
- Pressure
- Flow
- Speed
- Production count
- Motor current
- Energy consumption

Comparators allow the PLC to make decisions based on these values.

---

# 1️⃣ Equal To

The **Equal To** comparison checks whether two values are equal.

```text
Value A = Value B
```

Example:

```text
Production Count = 100
```

When the count reaches 100, the PLC can trigger a batch-complete condition.

---

# 2️⃣ Not Equal To

The **Not Equal To** comparison checks whether two values are different.

```text
Value A ≠ Value B
```

Example:

```text
Machine Speed ≠ Target Speed
```

This could be used to detect that a machine is not operating at its requested speed.

---

# 3️⃣ Greater Than

The **Greater Than** comparison checks whether one value is greater than another.

```text
Value A > Value B
```

Example:

```text
Temperature > 80°C
```

If the temperature rises above 80°C, the PLC could activate an alarm or cooling system.

---

# 4️⃣ Less Than

The **Less Than** comparison checks whether one value is below another.

```text
Value A < Value B
```

Example:

```text
Tank Level < 20%
```

The PLC could use this condition to start a pump.

---

# 5️⃣ Greater Than or Equal To

```text
Value A ≥ Value B
```

Example:

```text
Tank Level ≥ 90%
```

When the tank reaches 90% or higher, the PLC could stop an inlet valve.

---

# 6️⃣ Less Than or Equal To

```text
Value A ≤ Value B
```

Example:

```text
Pressure ≤ 2 bar
```

This could trigger a warning or another control action depending on the process design.

---

# 🏭 Real-World Example: Tank Level Control

Imagine a water storage tank.

The PLC receives the tank level from a level transmitter.

Control requirements:

```text
Level < 30%
      ↓
Start Pump

Level ≥ 80%
      ↓
Stop Pump
```

Simplified logic:

```text
       Tank Level
           │
           ▼
     ┌─────────────┐
     │   Compare   │
     └──────┬──────┘
            │
      ┌─────┴─────┐
      │           │
   < 30%        ≥ 80%
      │           │
      ▼           ▼
 Pump ON       Pump OFF
```

This is an example of **conditional control**.

---

# 🌡️ Real-World Example: Temperature Control

Consider an industrial heating system.

```text
Temperature < 60°C
        ↓
Heater ON

Temperature ≥ 60°C
        ↓
Heater OFF
```

The PLC continuously evaluates the temperature and changes the output according to the control conditions.

---

# 🔄 Comparators + Ladder Logic

Comparators can be combined with normal Ladder Logic conditions.

Example:

```text
Low Level       Pump Fault        Pump

----[ ]-----------[/]------------( )----
```

The logic can become more advanced:

```text
Level < 30%
      AND
No Pump Fault
      AND
Auto Mode
      ↓
   Pump ON
```

This is how simple PLC instructions combine into practical control strategies.

---

# 📊 Comparison Operators

| Operator | Meaning | Example |
|----------|---------|---------|
| = | Equal | Count = 100 |
| ≠ | Not Equal | Speed ≠ 1500 RPM |
| > | Greater Than | Temperature > 80°C |
| < | Less Than | Level < 30% |
| ≥ | Greater Than or Equal | Level ≥ 90% |
| ≤ | Less Than or Equal | Pressure ≤ 2 bar |

---

# ⚠️ Engineering Consideration: Analog Values

Many industrial measurements are analog values.

Examples:

- 4–20 mA
- 0–10 V
- Temperature transmitters
- Pressure transmitters
- Level transmitters

The PLC normally converts the incoming signal into a numerical value that can then be compared against process limits.

For example:

```text
4–20 mA Level Transmitter
           ↓
          PLC
           ↓
      Level = 72%
           ↓
       Comparator
           ↓
    Is Level > 80%?
```

The exact scaling and representation depend on the PLC and instrumentation system.

---

# ⚠️ Hysteresis

A simple comparison can sometimes cause an output to rapidly switch ON and OFF when a process value is close to a threshold.

For example:

```text
Pump ON  < 30%
Pump OFF ≥ 30%
```

If the measured value fluctuates around 30%, the pump could repeatedly change state.

A common solution is to use **hysteresis**.

Example:

```text
Level < 30%
     ↓
Pump ON

Level > 80%
     ↓
Pump OFF
```

The gap between the ON and OFF thresholds reduces unnecessary switching.

---

# 🛠️ Practical Exercise

Design a tank control system using comparators.

### Requirements

The tank level is measured from 0–100%.

1. If level falls below 25%, start Pump 1.
2. If level reaches 80%, stop Pump 1.
3. If level reaches 90%, activate a High Level Alarm.
4. If level falls below 10%, activate a Low Level Alarm.

Create a table showing:

| Condition | PLC Action |
|-----------|------------|
| Level < 10% | Low Level Alarm |
| Level < 25% | Pump ON |
| Level ≥ 80% | Pump OFF |
| Level ≥ 90% | High Level Alarm |

Then explain how you would implement the logic in Ladder Logic.

---

# 📝 Knowledge Check

1. What is a PLC comparator?

2. What does `>` mean?

3. What does `<` mean?

4. Give an example of using `≥` in an industrial process.

5. Why can simple threshold logic cause rapid switching?

6. What is hysteresis?

7. Why are analog process values commonly used with comparators?

---

# 💡 Key Takeaways

- Comparators allow PLCs to make decisions using numerical values.
- PLCs can compare process measurements against defined limits.
- Comparators are useful for temperature, pressure, level, flow, speed, and production counts.
- Multiple conditions can be combined to create more sophisticated control logic.
- Hysteresis can help prevent unnecessary switching around process thresholds.

---

# 📚 References

- IEC 61131-3 – Programmable Controllers Programming Languages
- Siemens TIA Portal Documentation
- Rockwell Automation Studio 5000 Documentation
- Schneider Electric PLC Documentation
- AutomationDirect PLC Programming Resources

---

# ⏭️ Next Lesson

**Day 27 – PLC Analog Signals and Scaling**

We'll explore:

- Digital vs Analog signals
- 4–20 mA
- 0–10 V
- Analog Input Modules
- Signal Scaling
- Engineering Units
- Real-world instrumentation examples

---

> **"A PLC becomes more powerful when it can make decisions based on what the process is actually doing."**
