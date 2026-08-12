# 📘 Day 30 – PLC Interlocks & Permissive Logic

## 🎯 Learning Objective

Understand how PLCs use **interlocks** and **permissives** to prevent equipment from operating when required conditions are not satisfied.

Today I am learning:

- Interlocks
- Permissives
- Start conditions
- Stop conditions
- Equipment protection
- Fault conditions
- Pump and motor control logic
- The difference between permissives and interlocks

---

# 📖 What is an Interlock?

An interlock is a control condition that prevents or stops equipment from operating when a defined condition exists.

The purpose is to help protect:

- Equipment
- Processes
- Operators
- The plant

For example:

```text
Pump Start Command
        +
Low-Low Tank Level
        ↓
     INTERLOCK
        ↓
     Pump OFF
```

The PLC can prevent the pump from running when the tank level is dangerously low.

---

# 🔐 What is a Permissive?

A permissive is a condition that must be satisfied before equipment is allowed to start or operate.

Think of it as:

> "Is everything ready for this equipment to start?"

For example, a pump might require:

```text
Auto Mode = TRUE
AND
Suction Valve Open = TRUE
AND
No Pump Fault = TRUE
AND
Tank Level > Minimum
```

Only when the required conditions are satisfied should the PLC allow the pump to start.

---

# 🔄 Permissive Logic

A simplified pump permissive could look like:

```text
Auto Mode
     │
     AND
     │
Valve Open
     │
     AND
     │
No Fault
     │
     AND
     │
Level OK
     │
     ▼
Pump Start Permitted
```

In Boolean logic:

```text
AUTO
AND
VALVE_OK
AND
NO_FAULT
AND
LEVEL_OK
=
START PERMITTED
```

---

# 🛑 Interlock Logic

An interlock works differently.

An interlock identifies a condition under which equipment should **not** operate.

Example:

```text
Low-Low Level
      ↓
   Interlock
      ↓
   Pump OFF
```

Another example:

```text
High Pressure
      ↓
   Interlock
      ↓
Compressor Stop
```

The exact implementation depends on the process and safety requirements.

---

# ⚖️ Permissive vs Interlock

| Feature | Permissive | Interlock |
|---------|-------------|-----------|
| Main purpose | Allows operation | Prevents/restricts operation |
| Typical question | "Can I start?" | "Should I stop/block?" |
| Evaluated before start | Commonly | Can be |
| Can stop running equipment | Depends on design | Commonly |
| Example | Valve open | Low-low level |

These concepts can overlap in real control systems, so the exact terminology depends on the plant, control philosophy, and implementation.

---

# 🏭 Example: Pump Control

Imagine a water transfer pump.

The pump should only start when:

```text
Auto Mode
+
Suction Valve Open
+
Discharge Path Available
+
No Pump Fault
+
Tank Level > 20%
```

The PLC evaluates these conditions.

```text
                    ┌── Auto Mode
                    │
                    ├── Suction Valve Open
                    │
                    ├── Discharge Available
                    │
                    ├── No Pump Fault
                    │
                    └── Level > 20%
                             │
                            AND
                             │
                             ▼
                       START PERMITTED
                             │
                             ▼
                          PUMP ON
```

---

# 🚨 Pump Interlocks

Now imagine the pump is already running.

A dangerous condition occurs:

```text
Tank Level < 10%
```

The PLC can detect the condition and initiate the configured pump shutdown logic.

```text
Tank Level < 10%
        ↓
Pump Interlock
        ↓
Pump Stop
```

This prevents the pump from continuing to operate under an undesirable process condition.

---

# 🔗 Combining Permissives and Interlocks

A real control strategy may contain both.

```text
              START CONDITIONS
                    │
                    ▼
              PERMISSIVES
                    │
                    ▼
              PUMP STARTS
                    │
                    ▼
             PUMP RUNNING
                    │
                    ▼
          CONTINUOUS MONITORING
                    │
             ┌──────┴──────┐
             │             │
        Normal State    Fault Condition
             │             │
             │             ▼
             │         INTERLOCK
             │             │
             │             ▼
             │         PUMP STOP
             │
             ▼
        Continue Running
```

This is a fundamental pattern in industrial control logic.

---

# 🧠 Example: Motor Control

Consider an industrial motor.

Possible start permissives:

```text
Remote Mode = TRUE
AND
Motor Ready = TRUE
AND
No Fault = TRUE
AND
Cooling Available = TRUE
```

Possible interlocks:

```text
Motor Overload
OR
High Temperature
OR
Emergency Stop Condition
```

The PLC control logic must be designed according to the actual equipment and safety requirements.

---

# ⚠️ Important Safety Concept

A PLC interlock is not automatically the same thing as a **safety function**.

Safety-related functions may require dedicated safety systems, safety PLCs, safety relays, appropriate sensors, validated architectures, and compliance with applicable standards.

For example:

```text
Emergency Stop
```

should not simply be assumed to be adequately handled by ordinary PLC logic.

The safety design must be based on the applicable machinery/process safety requirements.

---

# 🔄 PLC Control Sequence

A simplified sequence could be:

```text
Operator Start Command
          │
          ▼
   Check Permissives
          │
      ┌───┴───┐
      │       │
     YES      NO
      │       │
      ▼       ▼
   Start    Remain OFF
   Pump
      │
      ▼
Monitor Process
      │
      ▼
Check Interlocks
      │
   ┌──┴──┐
   │     │
 Normal Fault
   │     │
   ▼     ▼
Continue Stop
Running
```

---

# 🛠️ Practical Exercise

Design the control logic for a water transfer pump.

### Start Permissives

The pump may start only when:

1. Auto mode is enabled.
2. Suction valve is open.
3. Discharge valve is open.
4. No pump fault exists.
5. Tank level is above 20%.

### Interlocks

The pump must stop when:

1. Pump fault occurs.
2. Tank level falls below 10%.
3. A required valve closes.

Create a logic diagram showing:

```text
START COMMAND
      ↓
PERMISSIVES
      ↓
PUMP START
      ↓
PROCESS MONITORING
      ↓
INTERLOCKS
      ↓
PUMP STOP
```

---

# 📊 Example Logic Table

| Condition | Result |
|-----------|--------|
| Auto OFF | Pump cannot start |
| Suction Valve CLOSED | Pump cannot start |
| Discharge Valve CLOSED | Pump cannot start |
| Pump Fault | Pump cannot start |
| Level ≤ 20% | Pump cannot start |
| All permissives satisfied | Pump can start |
| Level < 10% while running | Pump stop condition |
| Pump Fault while running | Pump stop condition |

---

# 📝 Knowledge Check

1. What is a PLC interlock?

2. What is a permissive?

3. What is the main difference between a permissive and an interlock?

4. Give three examples of pump start permissives.

5. Give two examples of pump interlocks.

6. Why are interlocks important in industrial automation?

7. Is an ordinary PLC interlock automatically a safety function? Explain.

8. Why should control logic be based on the actual process and equipment design?

---

# 💡 Key Takeaways

- Permissives determine whether equipment is allowed to start or operate.
- Interlocks prevent or stop operation when defined conditions require it.
- Multiple permissives can be combined using AND logic.
- Multiple fault conditions can be monitored continuously.
- Pump and motor control commonly use permissive and interlock concepts.
- Interlocks improve process and equipment protection.
- Safety functions require appropriate safety engineering and should not automatically be treated as ordinary PLC logic.

---

# 📚 References

- IEC 61131-3 – Programmable Controllers
- IEC 61508 – Functional Safety of Electrical/Electronic/Programmable Electronic Safety-Related Systems
- IEC 62061 – Functional Safety of Machinery Control Systems
- Siemens Automation Documentation
- Rockwell Automation Documentation
- Schneider Electric Automation Documentation

---

# ⏭️ Next Lesson

**Day 31 – PLC Sequences & State-Based Control**

We'll explore:

- Sequential control
- Process states
- Start/Stop sequences
- State transitions
- Step-by-step machine operation
- Practical pump and tank sequences

---

> **"Good control logic doesn't only tell equipment what to do—it also defines when it must not operate."**
