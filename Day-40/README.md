# 📘 Day 40 – PLC Data Types, Memory & Tag Management

> 365 Days to SCADA Engineer — Day 40/365

Today I learned how PLCs store and organize information.

So far, I've been working with:

- Boolean conditions
- Analog values
- Comparisons
- Calculations
- Timers
- Control logic

But where does all this information actually live?

Inside the PLC, data is stored in memory using different **data types, tags, and memory structures**.

Understanding this is essential for writing organized and reliable PLC programs.

---

## 🎯 Learning Objectives

By the end of this lesson, I should understand:

- What PLC data types are
- What BOOL means
- What integer data types are
- What REAL means
- What PLC tags are
- Why meaningful tag names matter
- The difference between digital and analog data
- How PLC memory stores process information
- Why data types affect calculations
- How good tag management improves troubleshooting

---

# 1. What Is a Data Type?

A data type tells the PLC what kind of information a variable contains and how it should be handled.

For example:

```text
BOOL  → TRUE / FALSE
INT   → Integer number
DINT  → Larger integer
REAL  → Decimal / floating-point value
