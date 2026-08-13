# 📘 Day 31 – PLC Sequences & State-Based Control

## 🎯 Learning Objective

Understand how PLCs control processes that must happen in a specific order using sequences and operating states.

Today I am learning:

* Sequential control
* PLC states
* State transitions
* Start and stop sequences
* Step-by-step machine operation
* State-based control logic
* Practical tank and pump sequences

---

# 📖 What is Sequential Control?

Sequential control means performing a series of actions in a specific order.

Instead of:

```text
START → MOTOR ON
```

a real process might require:

```text
START
  ↓
Check Conditions
  ↓
Open Valve
  ↓
Confirm Valve Open
  ↓
Start Pump
  ↓
Monitor Process
  ↓
Stop Pump
  ↓
Close Valve
  ↓
Sequence Complete
```

Each step depends on conditions being satisfied before the process can move to the next step.

---

# 🔄 What is a PLC State?

A state represents the current operating condition of a machine or process.

For example, a pump system could have:

```text
IDLE
RUNNING
STOPPING
FAULT
```

The PLC determines which state the process is currently in and what actions are allowed.

---

# 🧠 Example States

A simple tank filling system could use:

```text
STATE 0 → IDLE

STATE 1 → CHECK PERMISSIVES

STATE 2 → OPEN INLET VALVE

STATE 3 → START PUMP

STATE 4 → FILL TANK

STATE 5 → STOP PUMP

STATE 6 → CLOSE VALVE

STATE 7 → COMPLETE
```

The PLC moves from one state to another when the required transition condition is satisfied.

---

# 🔀 State Transitions

A transition is the condition that allows the process to move from one state to another.

Example:

```text
IDLE
  │
  │ Start Command
  ▼
CHECK PERMISSIVES
  │
  │ All Conditions OK
  ▼
OPEN VALVE
  │
  │ Valve Open Feedback
  ▼
START PUMP
  │
  │ Pump Running Feedback
  ▼
FILL TANK
```

The PLC should not simply assume that an action happened.

Feedback can be used to confirm the actual equipment state.

---

# 🏭 Example: Automatic Tank Filling

Consider an automatic tank filling system.

### Step 1 — Idle

The system waits for an operator start command.

```text
State = IDLE
```

### Step 2 — Check Permissives

The PLC checks:

```text
Auto Mode
AND
No Fault
AND
Source Available
AND
Required Valve Available
```

If all conditions are satisfied:

```text
Move to State 2
```

### Step 3 — Open Valve

The PLC commands the inlet valve to open.

```text
Valve Command = OPEN
```

The PLC waits for valve feedback.

```text
Valve Open Feedback = TRUE
```

### Step 4 — Start Pump

Once the valve is confirmed open:

```text
Pump Start = TRUE
```

The PLC can then verify:

```text
Pump Running Feedback = TRUE
```

### Step 5 — Fill Tank

The tank begins filling.

The PLC continuously monitors:

```text
Tank Level
Pump Status
Valve Status
Faults
```

### Step 6 — Stop Condition

When the tank reaches the target level:

```text
Tank Level ≥ 80%
```

the PLC initiates the stopping sequence.

### Step 7 — Stop Pump

```text
Pump Start = FALSE
```

The PLC can verify that the pump has stopped.

### Step 8 — Close Valve

```text
Valve Command = CLOSE
```

The sequence is complete when the appropriate feedback is received.

---

# 🔗 Complete Sequence

```text
             START
               │
               ▼
             IDLE
               │
        Start Command
               │
               ▼
      CHECK PERMISSIVES
               │
          Conditions OK
               │
               ▼
         OPEN VALVE
               │
       Valve Feedback
               │
               ▼
          START PUMP
               │
       Pump Feedback
               │
               ▼
          FILL TANK
               │
        Level ≥ 80%
               │
               ▼
          STOP PUMP
               │
               ▼
         CLOSE VALVE
               │
               ▼
          SEQUENCE
          COMPLETE
```

---

# ⚠️ What Happens if Something Goes Wrong?

A sequence must also account for abnormal conditions.

For example:

```text
Valve Command = OPEN
        ↓
No Valve Open Feedback
        ↓
Timeout
        ↓
FAULT
```

Another example:

```text
Pump Command = ON
        ↓
No Running Feedback
        ↓
Fault Condition
        ↓
STOP SEQUENCE
```

This is where the concepts from previous lessons become useful.

```text
Permissives
     +
Interlocks
     +
Feedback
     +
Timers
     +
Comparators
     ↓
Reliable Sequence Logic
```

---

# 🔄 State Machine Concept

A state machine can be represented as:

```text
┌──────────┐
│   IDLE   │
└────┬─────┘
     │ Start
     ▼
┌──────────┐
│  CHECK   │
└────┬─────┘
     │ OK
     ▼
┌──────────┐
│   OPEN   │
│  VALVE   │
└────┬─────┘
     │ Feedback
     ▼
┌──────────┐
│   RUN    │
│   PUMP   │
└────┬─────┘
     │ Level Reached
     ▼
┌──────────┐
│   STOP   │
│   PUMP   │
└────┬─────┘
     │
     ▼
┌──────────┐
│ COMPLETE │
└──────────┘
```

The PLC continuously evaluates the current state and determines whether the transition to the next state is allowed.

---

# 🧩 Why State-Based Control is Useful

State-based control makes complex processes easier to understand and troubleshoot.

Instead of having hundreds of unrelated conditions, engineers can ask:

> "What state is the machine currently in?"

Then:

> "What condition is preventing it from moving to the next state?"

This can make troubleshooting much easier.

---

# 🛠️ Practical Exercise

Design a state sequence for a tank filling system.

### Requirements

The system should:

1. Start in IDLE.
2. Wait for an operator start command.
3. Check permissives.
4. Open the inlet valve.
5. Confirm the valve is open.
6. Start the pump.
7. Confirm the pump is running.
8. Fill the tank.
9. Stop the pump when level reaches 80%.
10. Close the inlet valve.
11. Return to IDLE.

### Add Fault Conditions

The sequence should enter a FAULT state if:

* Valve fails to open within the expected time.
* Pump fails to start.
* A required permissive is lost.
* A configured process fault occurs.

Draw the sequence as a state diagram.

---

# 📊 Example State Table

| State       | Description        | Transition     |
| ----------- | ------------------ | -------------- |
| IDLE        | Waiting for start  | Start command  |
| CHECK       | Verify permissives | Conditions OK  |
| OPEN_VALVE  | Command valve open | Valve feedback |
| START_PUMP  | Command pump       | Pump feedback  |
| FILL        | Fill tank          | Level ≥ 80%    |
| STOP_PUMP   | Stop pump          | Pump stopped   |
| CLOSE_VALVE | Close valve        | Valve closed   |
| COMPLETE    | Sequence finished  | Return to IDLE |
| FAULT       | Abnormal condition | Operator reset |

---

# 📝 Knowledge Check

1. What is sequential control?

2. What is a PLC state?

3. What is a state transition?

4. Why is equipment feedback important?

5. Give five possible states for a pump sequence.

6. What could happen if a valve command is sent but the PLC receives no open feedback?

7. How can timers be used in sequence control?

8. How do permissives and interlocks work together with sequences?

---

# 💡 Key Takeaways

* Many industrial processes operate through a sequence of steps.
* A PLC state represents the current operating condition.
* Transitions determine when the process can move to another state.
* Equipment feedback helps confirm that commanded actions actually occurred.
* Timers can detect conditions that take too long.
* Permissives determine whether an operation is allowed.
* Interlocks can stop or prevent operation under defined conditions.
* State-based control provides a structured way to manage complex processes.

---

# 📚 References

* IEC 61131-3 – Programmable Controllers
* Siemens TIA Portal Documentation
* Rockwell Automation Documentation
* Schneider Electric Automation Documentation

---

# ⏭️ Next Lesson

**Day 32 – PLC Fault Handling & Diagnostics**

We'll explore:

* PLC fault conditions
* Equipment faults
* Fault detection
* Alarm conditions
* Diagnostic logic
* Fault reset
* Troubleshooting PLC sequences

---

> **"Complex industrial processes become easier to control when you break them into clear states and transitions."**

