# 📘 Day 23 – PLC Latching (Seal-In Circuits)

## 🎯 Learning Objective

Learn how PLCs use **latching (seal-in) circuits** to keep an output energized after a momentary Start button is released, and understand how Stop buttons safely interrupt the circuit.

---

# 📖 What is a Latching Circuit?

A latching circuit (also called a **seal-in circuit**) allows an output to remain ON after the Start button has been released.

Without a latching circuit, the output would only remain ON while the Start button is being pressed.

Latching circuits are widely used in industrial automation for:

- Motors
- Pumps
- Conveyors
- Fans
- Compressors
- Mixers

---

# 🤔 Why is Latching Needed?

Imagine pressing a Start button to run a conveyor.

Without latching:

- Conveyor runs only while the button is held.
- Releasing the button immediately stops the conveyor.

This is impractical in industrial environments.

A latching circuit keeps the conveyor running until a Stop button is pressed.

---

# ⚙️ Basic Start/Stop Circuit

```text
Stop      Start          Motor

--[/]------[ ]------------( )---
            |
            |
        Motor Contact
----------[ ]-------------
```

The Motor Contact is connected in parallel with the Start button.

Once the motor starts, its own contact keeps the circuit energized.

---

# 🔄 How It Works

### Step 1

The operator presses the **Start** button.

- Start contact closes.
- Motor output energizes.
- Auxiliary motor contact closes.

---

### Step 2

The operator releases the Start button.

Although the Start contact opens, the auxiliary contact keeps the circuit complete.

The motor continues running.

---

### Step 3

The operator presses the **Stop** button.

The Normally Closed Stop contact opens.

The circuit breaks.

The motor stops.

The auxiliary contact opens.

---

# 🏭 Real-World Example

Imagine a water pumping station.

When the water level becomes low:

- Operator presses Start.
- Pump starts.
- Pump continues running automatically.

When the storage tank becomes full:

- Operator presses Stop (or PLC logic issues a stop command).
- Pump turns OFF safely.

---

# 🛡️ Why is the Stop Button Normally Closed?

Industrial control systems usually use **Normally Closed (NC)** Stop buttons.

Reasons:

- Safer design
- Broken wire detection
- Fail-safe operation
- Better fault protection

If the wiring fails, the PLC interprets it as a stop condition.

---

# 📊 Ladder Diagram

```text
 Left Rail                     Right Rail

 |----[/ Stop ]----[ Start ]--------( Motor )----|
 |                     |
 |----[ Motor ]--------|
```

The Motor contact is called the **seal-in contact** because it seals the circuit after startup.

---

# ⚠️ Common Applications

Seal-in circuits are used in:

- Conveyor belts
- Water pumps
- Industrial fans
- Air compressors
- Packaging machines
- Production lines
- Mixing equipment

---

# 💡 Key Takeaways

- Latching keeps an output ON after the Start button is released.
- The Start button is usually Normally Open.
- The Stop button is usually Normally Closed.
- Seal-in circuits are one of the most common PLC programming patterns.
- They improve usability while maintaining safe operation.

---

# 🛠️ Practical Exercise

Design a ladder logic program for an exhaust fan.

Requirements:

- Start button
- Stop button
- Fan output
- Seal-in contact

Explain how the fan continues running after the Start button is released.

---

# 📝 Knowledge Check

1. What is a latching (seal-in) circuit?

2. Why is a seal-in contact used?

3. Why are Stop buttons usually Normally Closed?

4. What happens when the Stop button is pressed?

5. Name three industrial systems that commonly use latching circuits.

---

# 📚 References

- IEC 61131-3 – PLC Programming Languages
- Siemens TIA Portal Programming Manual
- Rockwell Automation Studio 5000 Documentation
- Schneider Electric PLC Programming Guide
- AutomationDirect PLC Learning Resources

---

# ⏭️ Next Lesson

**Day 24 – PLC Timers (TON, TOF, and RTO)**

We'll explore:

- On-delay timers (TON)
- Off-delay timers (TOF)
- Retentive timers (RTO)
- Practical timing applications
- Real-world automation examples

---

> **"A single press can keep an entire process running—that's the power of a well-designed seal-in circuit."**
