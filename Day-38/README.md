# 📘 Day 38 – PLC Math Instructions & Process Calculations

> 365 Days to SCADA Engineer — Day 38/365

Today I learned how PLCs perform mathematical calculations.

A PLC doesn't only read sensors and turn outputs ON or OFF.

It can also calculate values that are important for:

- Process control
- Scaling
- Monitoring
- Production calculations
- Energy calculations
- Flow and level calculations
- Alarm limits
- Engineering-unit conversions

---

## 🎯 Learning Objectives

By the end of this lesson, I should understand:

- Basic PLC math operations
- Addition and subtraction
- Multiplication and division
- Process calculations
- Percentage calculations
- Average calculations
- Why data types matter
- How calculations can be used in industrial automation

---

# 1. Why PLCs Need Math

Consider a water treatment system.

The PLC might receive:

```text
Tank Level = 6.5 m
Flow Rate = 25 m³/h
Pump Runtime = 4.5 hours
