# 📘 Day 39 – PLC Comparators & Analog Threshold Logic

> 365 Days to SCADA Engineer — Day 39/365

Today I learned how PLCs compare values and use those comparisons to make control decisions.

A PLC can receive a process value such as:

- Tank level
- Temperature
- Pressure
- Flow
- Speed

But simply knowing the value isn't enough.

The PLC often needs to ask questions such as:

> Is the level greater than the high limit?

> Is the temperature below the required value?

> Has the pressure reached the alarm threshold?

This is where **comparators** become important.

---

## 🎯 Learning Objectives

By the end of this lesson, I should understand:

- What PLC comparators are
- Greater than `>`
- Less than `<`
- Equal to `=`
- Greater than or equal to `>=`
- Less than or equal to `<=`
- How analog values are compared
- How comparisons influence control logic
- The difference between comparison logic and process alarms

---

# 1. What Is a Comparator?

A comparator checks the relationship between two values.

For example:

```text
Level > 8 m

