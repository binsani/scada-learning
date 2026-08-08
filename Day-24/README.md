# 📘 Day 24 – PLC Timers: TON, TOF & Retentive Timers

## 🎯 Learning Objective

Understand how PLC timers control industrial processes based on time.

Today I am learning three important timer concepts:

- TON — Timer ON Delay
- TOF — Timer OFF Delay
- RTO — Retentive Timer

Timers are essential for sequencing machines, delaying operations, controlling equipment, and monitoring process conditions.

---

# ⏱️ What is a PLC Timer?

A PLC timer is an instruction that allows a control program to measure or delay an operation for a specified amount of time.

For example:

> Start a motor → wait 5 seconds → start another motor.

Instead of starting both motors at the same time, a timer can introduce the required delay.

---

# 1️⃣ TON — Timer ON Delay

TON stands for **Timer ON Delay**.

The timer waits for a specified amount of time after its input becomes TRUE before activating its output.

### Example

```text
Start
  |
  |----[ ]--------[ TON 5s ]----
                         |
                         ▼
                    Motor Start
```

If the Start condition remains TRUE for 5 seconds, the timer reaches its preset time.

### Behaviour

```text
Input:   OFF ─── ON─────────────── OFF
                 │
                 │<--- 5 seconds --->
                 │
Output:  OFF ───────────── ON ───── OFF
```

### Typical applications

- Motor startup delays
- Pump sequencing
- Conveyor delays
- Machine startup sequences
- Process stabilization

---

# 2️⃣ TOF — Timer OFF Delay

TOF stands for **Timer OFF Delay**.

The output remains active for a specified amount of time after the input becomes FALSE.

### Example

```text
Fan Command
    |
    |----[ ]--------[ TOF 10s ]----
                           |
                           ▼
                        Fan Output
```

When the command turns OFF, the fan continues running for another 10 seconds before stopping.

### Behaviour

```text
Input:   OFF ─── ON──────── OFF
                 │           │
                 │           │<--- 10 seconds --->
                 │           │
Output:  OFF ──────────────── ON────── OFF
```

### Typical applications

- Cooling fans
- Ventilation systems
- Motor cooling
- Purging systems
- Delayed shutdown

---

# 3️⃣ RTO — Retentive Timer

RTO stands for **Retentive Timer On**.

Unlike a normal TON timer, an RTO retains its accumulated time when its enabling condition becomes FALSE.

The accumulated value remains until the timer is explicitly reset.

### Example

A machine needs to operate for a total of 60 minutes before maintenance.

The machine may stop several times during production.

An RTO can accumulate the operating time:

```text
Run
 │
 ├── 20 min ──► Accumulated = 20 min
 │
 ├── Machine stops
 │
 ├── 15 min ──► Accumulated = 35 min
 │
 ├── Machine stops
 │
 └── 25 min ──► Accumulated = 60 min
```

The timer reaches the required accumulated operating time.

### Typical applications

- Equipment runtime tracking
- Preventive maintenance
- Operating-hour monitoring
- Filter replacement intervals
- Machine service schedules

---

# 📊 TON vs TOF vs RTO

| Timer | Meaning | Main Behaviour |
|-------|---------|----------------|
| TON | Timer ON Delay | Delays turning ON |
| TOF | Timer OFF Delay | Delays turning OFF |
| RTO | Retentive Timer | Accumulates and retains time |

---

# 🏭 Real-World Example

Imagine a water treatment plant with two pumps.

### Requirement

When Pump 1 starts:

1. Pump 1 runs immediately.
2. Wait 10 seconds.
3. Pump 2 starts.
4. If Pump 1 stops, Pump 2 should stop after a short delay.

This could involve multiple PLC timer instructions.

Simplified sequence:

```text
Pump 1 Start
     │
     ▼
Pump 1 ON
     │
     ▼
TON Timer
     │
   10 sec
     │
     ▼
Pump 2 ON
```

This type of timing logic is common in industrial sequencing.

---

# ⚙️ Timer Parameters

Depending on the PLC platform, a timer typically has parameters such as:

### Preset Time

The target duration.

Example:

```text
Preset = 10 seconds
```

### Accumulated Time

The amount of time currently measured.

Example:

```text
Accumulated = 7 seconds
```

### Done Status

Indicates that the timer has reached its preset value.

---

# 🔄 Timer Sequence

A simplified TON sequence:

```text
Input becomes TRUE
        │
        ▼
Timer starts counting
        │
        ▼
Accumulated Time increases
        │
        ▼
Preset Time reached
        │
        ▼
Timer Done
        │
        ▼
Output condition becomes TRUE
```

---

# ⚠️ Important Engineering Consideration

Timer behaviour can vary between PLC manufacturers and programming environments.

For example, Siemens, Rockwell Automation, Schneider Electric, and other PLC platforms may represent timer instructions and parameters differently.

Therefore, always consult the documentation for the specific PLC platform being used.

The underlying timing concepts, however, remain important across PLC systems.

---

# 🛠️ Practical Exercise

Design a Ladder Logic sequence for a water pumping system.

### Requirements

1. Press Start.
2. Pump 1 starts immediately.
3. Wait 5 seconds.
4. Pump 2 starts.
5. Press Stop.
6. Pump 2 stops immediately.
7. Pump 1 stops after 3 seconds.

Identify where you would use:

- TON
- TOF

Draw the ladder logic and explain the sequence.

---

# 📝 Knowledge Check

1. What does TON stand for?

2. What is the purpose of an ON-delay timer?

3. What does TOF stand for?

4. Give one example where an OFF-delay timer would be useful.

5. What makes an RTO different from a normal TON?

6. What is the difference between preset time and accumulated time?

7. Why should PLC documentation be checked before implementing timer logic?

---

# 💡 Key Takeaways

- PLC timers allow automation programs to respond to time-based conditions.
- TON delays an ON operation.
- TOF delays an OFF operation.
- RTO retains accumulated time until reset.
- Timers are important for sequencing industrial equipment.
- Timer implementation can differ between PLC manufacturers.

---

# 📚 References

- IEC 61131-3 – Programmable Controllers Programming Languages
- Siemens TIA Portal Documentation
- Rockwell Automation Studio 5000 Documentation
- Schneider Electric PLC Documentation
- AutomationDirect PLC Programming Resources

---

# ⏭️ Next Lesson

**Day 25 – PLC Counters: CTU, CTD & Reset**

We'll explore:

- Count Up (CTU)
- Count Down (CTD)
- Counter reset
- Production counting
- Batch control
- Real-world industrial examples

---

> **"Automation isn't only about what happens—it is also about when it happens."**
