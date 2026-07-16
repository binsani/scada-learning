# 📘 Day 2 – PLC Fundamentals

## 🎯 Learning Objective

Understand what a **Programmable Logic Controller (PLC)** is, why it is used in industrial automation, its main components, and how it operates.

---

# 📖 What is a PLC?

A **Programmable Logic Controller (PLC)** is a rugged industrial computer designed to automate and control machines and industrial processes.

Unlike a standard computer, a PLC is built to operate reliably in harsh industrial environments where there may be:

- High temperatures
- Dust
- Moisture
- Electrical noise
- Continuous operation (24/7)

PLCs receive information from sensors, process the information according to a programmed logic, and control outputs such as motors, pumps, valves, and alarms.

---

# 🏭 Where Are PLCs Used?

PLCs are widely used across many industries, including:

- 🏭 Manufacturing Plants
- 💧 Water Treatment Facilities
- ⛽ Oil & Gas Operations
- ⚡ Power Generation
- 🚦 Traffic Control Systems
- 🏢 Building Automation
- 📦 Warehouses and Conveyor Systems

---

# ⚙️ Main PLC Components

A typical PLC consists of the following components:

| Component | Purpose |
|-----------|---------|
| CPU | Executes the control program and makes decisions |
| Power Supply | Provides electrical power to the PLC |
| Input Modules | Receive signals from sensors and switches |
| Output Modules | Control actuators such as motors, valves, and relays |
| Communication Modules | Allow communication with SCADA systems, HMIs, and other PLCs |

---

# 🔄 PLC Scan Cycle

A PLC continuously repeats the following cycle:

1. **Read Inputs**
   - Collect signals from sensors and field devices.

2. **Execute Program**
   - Run the control logic programmed by the engineer.

3. **Update Outputs**
   - Turn motors, valves, lights, and other devices ON or OFF.

4. **Diagnostics & Communication**
   - Perform internal checks and exchange data with other systems.

This process repeats many times every second, allowing the PLC to respond quickly to changes in the industrial process.

---

# 🏭 Real-World Example

Imagine a water storage tank.

The PLC monitors the water level using a level sensor.

- If the tank level becomes **low**, the PLC starts the water pump.
- As the tank fills, the PLC continuously monitors the level.
- Once the tank reaches the **maximum level**, the PLC automatically stops the pump.
- If a fault occurs, the PLC activates an alarm and sends information to the SCADA system.

This automation eliminates the need for continuous manual operation.

---

# 💡 Key Takeaways

- A PLC is a specialized industrial computer.
- PLCs automate machines and industrial processes.
- They replace traditional relay-based control systems.
- PLCs are reliable, flexible, and designed for harsh environments.
- PLCs are one of the core building blocks of every modern SCADA system.

---

# 🛠️ Practical Exercise

Think about an automatic water tank at home.

Identify:

- What would serve as the **Input**?
- What would be the **PLC**?
- What would be the **Output**?

Write your answers in your own words.

---

# 📚 References

- Siemens – SIMATIC PLC Documentation
- Rockwell Automation – PLC Learning Resources
- Schneider Electric – Industrial Automation Documentation
- IEC 61131-3 Standard (PLC Programming Languages)

---

# ⏭️ Next Lesson

**Day 3 – RTU vs PLC**

We'll compare:

- What an RTU is
- PLC vs RTU
- When each is used
- Advantages and disadvantages
- Real-world examples

---

> **"Every expert was once a beginner who kept learning."**
