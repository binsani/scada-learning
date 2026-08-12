# 📘 Day 29 – Analog Outputs & Variable Control

## 🎯 Learning Objective

Understand how PLCs use analog output modules to send variable control signals to industrial equipment.

Today I am learning:

- Analog Output (AO) modules
- 4–20 mA outputs
- 0–10 V outputs
- Control valves
- Variable Frequency Drives (VFDs)
- Speed control
- Setpoints
- PLC-to-actuator signal flow

---

# 📖 What is an Analog Output?

An Analog Output (AO) module allows a PLC to send a continuously varying electrical signal to an external device.

While a digital output might simply command:

```text
ON
```

or:

```text
OFF
```

an analog output can provide a range of control values.

For example:

```text
0–10 V
```

can represent different speeds or positions.

---

# 🔌 Common Analog Output Signals

Two common industrial analog output signals are:

### 4–20 mA

Example:

```text
4 mA  → Minimum
12 mA → 50%
20 mA → Maximum
```

### 0–10 V

Example:

```text
0 V  → Minimum
5 V  → 50%
10 V → Maximum
```

The actual relationship depends on how the receiving device is configured.

---

# 🔄 Analog Output Signal Flow

A typical control path can look like this:

```text
PLC Program
     │
     ▼
Control Setpoint
     │
     ▼
Analog Output Module
     │
     │ 4–20 mA / 0–10 V
     ▼
Control Device
     │
     ▼
Industrial Process
```

For example:

```text
PLC
 │
 │ 4–20 mA
 ▼
Control Valve
 │
 ▼
Water Flow
```

---

# 🏭 Example 1: Control Valve

Imagine a process where a PLC controls a water valve.

The PLC sends:

```text
4 mA  → Valve minimum position
12 mA → Valve approximately 50%
20 mA → Valve maximum position
```

The valve position changes according to the received control signal.

This allows the PLC to regulate the process rather than simply opening or closing the valve.

---

# ⚙️ Example 2: Variable Frequency Drive

A PLC can also provide a speed reference to a Variable Frequency Drive (VFD).

The VFD controls the speed of an electric motor.

Conceptually:

```text
PLC
 │
 │ Analog Speed Reference
 ▼
VFD
 │
 ▼
Motor
 │
 ▼
Pump
```

For example, a configured signal might represent:

```text
0 V  → 0% speed
5 V  → 50% speed
10 V → 100% speed
```

The exact scaling depends on the VFD configuration.

---

# 🎛️ Setpoints

A **setpoint** is the desired value for a process variable.

For example:

```text
Desired Tank Level = 70%
```

The PLC can use the setpoint as part of its control strategy.

Another example:

```text
Desired Motor Speed = 60%
```

The PLC may convert this desired value into an analog output signal.

---

# 🔗 Connecting Analog Input and Analog Output

Now we can connect the concepts from Days 27–29.

Consider a tank system.

### Measurement

```text
Level Transmitter
       │
       │ 4–20 mA
       ▼
PLC Analog Input
       │
       ▼
Scaling
       │
       ▼
Tank Level = 40%
```

### Control

The PLC determines that more water is required.

```text
PLC Control Logic
       │
       ▼
Analog Output
       │
       │ 4–20 mA
       ▼
Control Valve
       │
       ▼
Water Flow
```

The complete process becomes:

```text
Process
   │
   ▼
Sensor
   │
   ▼
Analog Input
   │
   ▼
PLC
   │
   ▼
Control Logic
   │
   ▼
Analog Output
   │
   ▼
Actuator
   │
   ▼
Process
```

This creates a basic closed-loop control concept.

---

# 🔄 Open Loop vs Closed Loop

## Open Loop

An open-loop system sends a command without using feedback to automatically adjust the command.

Example:

```text
PLC
 │
 ▼
Motor
```

The PLC commands the motor, but the control decision does not depend on a measured process variable.

---

## Closed Loop

A closed-loop system uses feedback.

Example:

```text
        ┌──────────────────────┐
        │                      │
        ▼                      │
PLC → Control Valve → Process  │
 ↑                         │   │
 │                         ▼   │
 └────── Level Sensor ◄────┘
```

The PLC receives the process measurement and can adjust the output accordingly.

---

# 🧠 Why Analog Outputs Matter

Industrial processes often require more than simple ON/OFF control.

Examples:

- Adjusting valve position
- Controlling motor speed
- Controlling pump speed
- Regulating flow
- Adjusting temperature
- Controlling pressure

Analog outputs allow the PLC to influence these processes continuously.

---

# 📊 Analog Output Example

Suppose a PLC controls a VFD using:

```text
0–10 V
```

Configured as:

| Output | Speed Reference |
|--------|-----------------|
| 0 V | 0% |
| 2.5 V | 25% |
| 5 V | 50% |
| 7.5 V | 75% |
| 10 V | 100% |

If the PLC needs a 75% speed reference:

```text
PLC
 ↓
7.5 V
 ↓
VFD
 ↓
Motor ≈ 75% reference
```

The exact motor speed depends on the VFD configuration, motor characteristics, and control mode.

---

# ⚠️ Important Engineering Consideration

An analog output signal does not automatically guarantee that the controlled device will produce exactly the expected physical result.

The complete system depends on:

- Device configuration
- Signal scaling
- Calibration
- Wiring
- Control mode
- Equipment characteristics
- PLC configuration

Engineers therefore need to verify the complete signal chain.

---

# 🛠️ Practical Exercise

Design a simple tank filling system.

### Requirements

A PLC controls a valve using a:

```text
4–20 mA analog output
```

The valve is configured so that:

```text
4 mA  → 0% open
12 mA → 50% open
20 mA → 100% open
```

The tank has a level transmitter connected to a PLC analog input.

Design the following signal flow:

```text
Tank
 ↓
Level Sensor
 ↓
4–20 mA
 ↓
PLC Analog Input
 ↓
Scaling
 ↓
Control Logic
 ↓
PLC Analog Output
 ↓
4–20 mA
 ↓
Control Valve
 ↓
Tank
```

Explain how the PLC could use the measured level to determine the valve command.

---

# 📝 Knowledge Check

1. What is an analog output?

2. What is the difference between a digital output and an analog output?

3. Give two examples of equipment that can receive an analog output.

4. What is a setpoint?

5. What is a VFD?

6. Why might a PLC use a 4–20 mA output?

7. What is the difference between open-loop and closed-loop control?

8. What role does feedback play in closed-loop control?

---

# 💡 Key Takeaways

- Analog outputs allow PLCs to send variable control signals.
- Common output signals include 4–20 mA and 0–10 V.
- Control valves can use analog signals for variable positioning.
- VFDs can use control references from PLCs to control motor speed.
- A setpoint represents a desired process value.
- Closed-loop systems use feedback to influence control decisions.
- Analog inputs and outputs can work together to create industrial control systems.

---

# 📚 References

- IEC 61131-3 – Programmable Controllers Programming Languages
- IEC 60381 – Analog Signals for Process Control Systems
- Siemens TIA Portal Documentation
- Rockwell Automation Documentation
- Schneider Electric PLC Documentation

---

# ⏭️ Next Lesson

**Day 30 – PLC Interlocks & Permissive Logic**

We'll explore:

- Interlocks
- Permissives
- Equipment protection
- Start conditions
- Stop conditions
- Safety-related considerations
- Real-world motor and pump control logic

---

> **"A PLC doesn't just observe the process—it can also influence how the process operates."**
