# 📘 Day 5 – SCADA Architecture

## 🎯 Learning Objective

Understand the overall architecture of a SCADA system, identify its major components, and learn how data flows from field devices to operators.

---

# 📖 What is SCADA Architecture?

SCADA architecture refers to the structure of hardware, software, communication networks, and field devices that work together to monitor and control industrial processes.

A typical SCADA system collects data from sensors, processes it through controllers, transmits it over communication networks, and presents it to operators through graphical interfaces.

---

# 🏗️ Main Components of a SCADA System

## 1️⃣ Field Devices

These interact directly with the physical process.

Examples:

- Sensors
- Temperature Transmitters
- Pressure Sensors
- Flow Meters
- Level Sensors
- Actuators
- Motors
- Pumps
- Valves

---

## 2️⃣ PLCs and RTUs

These serve as the brains of the field.

### PLC

- Executes control logic
- Reads sensor inputs
- Controls outputs
- Used in factories and plants

### RTU

- Collects data from remote sites
- Sends data to the control center
- Performs limited local control
- Designed for harsh environments

---

## 3️⃣ Communication Network

The communication network transfers data between field devices and the SCADA server.

Common communication technologies include:

- Ethernet
- Fiber Optics
- Radio
- Cellular (4G/5G)
- Satellite
- Wi-Fi

Common industrial protocols include:

- Modbus RTU
- Modbus TCP
- OPC UA
- DNP3
- IEC 60870-5-104
- Ethernet/IP
- PROFINET

---

## 4️⃣ SCADA Server

The SCADA server acts as the central management system.

Responsibilities include:

- Collecting field data
- Storing historical data
- Processing alarms
- Managing users
- Sending commands to PLCs and RTUs

---

## 5️⃣ HMI (Human Machine Interface)

Operators interact with the SCADA system through HMIs.

Typical HMI functions include:

- Monitoring equipment
- Starting and stopping machines
- Viewing alarms
- Viewing trends
- Acknowledging faults

---

# 🔄 SCADA Data Flow

The flow of information in a SCADA system typically follows this sequence:

```text
Sensors
   │
   ▼
PLC / RTU
   │
   ▼
Communication Network
   │
   ▼
SCADA Server
   │
   ▼
HMI
   │
   ▼
Operator
```

The operator can also send commands back through the HMI to the PLC or RTU to control field equipment.

---

# 🌍 Real-World Example

Imagine a water treatment plant.

### Sensors measure:

- Water level
- Pressure
- Flow rate
- Temperature

↓

### PLC

- Starts pumps
- Opens valves
- Stops pumps when the tank is full

↓

### Communication Network

Transfers operational data to the SCADA server.

↓

### SCADA Server

Processes data, stores historical records, and generates alarms.

↓

### HMI

Displays the plant status to the operator, who can monitor the system and issue control commands when necessary.

---

# 📊 Typical SCADA Architecture

```text
                Operator
                    │
                    ▼
          +-------------------+
          |        HMI        |
          +---------+---------+
                    │
                    ▼
          +-------------------+
          |    SCADA Server   |
          +---------+---------+
                    │
      Communication Network
                    │
      +-------------+-------------+
      |                           |
 +-----------+               +-----------+
 |    PLC    |               |    RTU    |
 +-----+-----+               +-----+-----+
       │                           │
   Sensors &                   Remote
   Actuators                  Field Devices
```

---

# 💡 Key Takeaways

- SCADA architecture connects field devices to operators.
- PLCs and RTUs gather and process field data.
- Communication networks transport industrial data.
- The SCADA server manages monitoring, alarms, and historical data.
- HMIs allow operators to monitor and control industrial processes.

---

# 🛠️ Practical Exercise

Using the architecture above, answer the following:

1. Which device collects data from sensors?
2. Which component stores historical process data?
3. Which component allows operators to control the plant?
4. What happens if the communication network fails?

Write your answers before moving to Day 6.

---

# 📝 Knowledge Check

1. What are the five main components of a SCADA system?

2. What is the role of the SCADA server?

3. What is the function of the communication network?

4. Which device executes control logic?

5. Can a SCADA system communicate with multiple PLCs and RTUs?

---

# 📚 References

- Siemens – SIMATIC SCADA Documentation
- Schneider Electric – EcoStruxure SCADA Expert
- Inductive Automation – Ignition SCADA Documentation
- ISA (International Society of Automation)
- NIST SP 800-82 – Guide to Industrial Control Systems (ICS) Security

---

# ⏭️ Next Lesson

**Day 6 – Industrial Communication Protocols**

We'll cover:

- What communication protocols are
- Modbus RTU
- Modbus TCP
- OPC UA
- DNP3
- Ethernet/IP
- PROFINET

---

> **"A SCADA system is only as effective as the architecture that connects every device, controller, and operator into one coordinated system."**
