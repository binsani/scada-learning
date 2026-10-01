# 📘 Day 43 – PLC State Machines & Sequence Control

**Day 43/365 — Learning how PLCs control processes step by step**

Today I’m moving from reusable PLC logic into **sequence control**.

Many industrial processes are not simply:

> ON → OFF

They happen through a series of controlled steps.

For example, an automated tank filling process might be:

```text
START
  ↓
CHECK PERMISSIVES
  ↓
OPEN INLET VALVE
  ↓
START PUMP
  ↓
FILL TANK
  ↓
REACH LEVEL
  ↓
STOP PUMP
  ↓
CLOSE VALVE
  ↓
PROCESS COMPLETE
This is where state machines and sequence control become useful.

🎯 Learning Objectives

Today I want to understand:

What a PLC state is
What a state machine is
Why sequence control is important
How a process moves between states
The difference between states and transitions
How timers and sensors can trigger transitions
How sequence control connects to SCADA
How to design a simple industrial sequence
1. What Is a PLC State?

A state represents the current condition or step of a process.
For example:
IDLE
FILLING
MIXING
DRAINING
COMPLETE
FAULT
At any particular moment, the process is operating according to its current state.
For example:
Current State = FILLING
The PLC executes the logic associated with the filling stage.
2. What Is a State Machine?
A state machine is a control structure where a process moves between predefined states according to specific conditions.
Conceptually:
             ┌──────────────┐
             │     IDLE     │
             └──────┬───────┘
                    │ Start
                    ▼
             ┌──────────────┐
             │   FILLING    │
             └──────┬───────┘
                    │ Level Reached
                    ▼
             ┌──────────────┐
             │   MIXING     │
             └──────┬───────┘
                    │ Timer Done
                    ▼
             ┌──────────────┐
             │   DRAINING   │
             └──────┬───────┘
                    │ Empty
                    ▼
             ┌──────────────┐
             │  COMPLETE    │
             └──────────────┘
The exact implementation varies between PLC platforms.
3. States vs Transitions

This is one of the most important concepts.

State

Describes what the process is currently doing.
Examples:
IDLE
FILLING
MIXING
DRAINING
Transition

Describes what must happen before moving to another state.

Examples:
Start button pressed
Tank reaches high level
Timer expires
Tank reaches low level
Fault detected
Think of it as:
STATE
   ↓
Condition evaluated
   ↓
TRANSITION
   ↓
NEXT STATE
4. Example: Automatic Tank Process
Imagine a simple mixing tank.
The process is:
1.Wait for Start
2.Fill the tank
3.Mix the material
4.Drain the tank
5.Return to idle
We could define:
STATE 0 = IDLE
STATE 1 = FILLING
STATE 2 = MIXING
STATE 3 = DRAINING
STATE 4 = COMPLETE
STATE 99 = FAULT
5. State 0 — IDLE
In the IDLE state:
Pump = OFF
Inlet Valve = CLOSED
Mixer = OFF
Drain Valve = CLOSED
The PLC waits for a valid start condition.
Transition:
StartCommand = TRUE
        ↓
      FILLING
StartCommand = TRUE
        ↓
      FILLING
6. State 1 — FILLING

During FILLING:
Inlet Valve = OPEN
Pump = ON
Mixer = OFF
Drain Valve = CLOSED
The PLC monitors the tank level.

When the required level is reached:
HighLevel = TRUE
the sequence can transition to:

MIXING
7. State 2 — MIXING

During MIXING:

Inlet Valve = CLOSED
Pump = OFF
Mixer = ON
Drain Valve = CLOSED

A timer can determine how long mixing should continue.

For example:

MixTime = 60 seconds

When:

MixTimer.Done = TRUE

the sequence moves to:
8. State 3 — DRAINING

During DRAINING:

Inlet Valve = CLOSED
Pump = OFF
Mixer = OFF
Drain Valve = OPEN

The PLC monitors the tank level.

When:

LowLevel = TRUE

the sequence can transition to:

COMPLETE
9. State 4 — COMPLETE

The process has finished.
The PLC can:

Inlet Valve = CLOSED
Pump = OFF
Mixer = OFF
Drain Valve = CLOSED

Then the sequence can return to:

IDLE

and wait for the next cycle.

10. Fault State

Industrial sequences should also consider abnormal conditions.

For example:
For example:

Any State
    │
    │ Fault Detected
    ▼
┌──────────────┐
│    FAULT     │
└──────────────┘

A fault could be caused by:

Motor fault
Emergency stop
Sensor failure
Communication failure
Invalid process condition
Safety system trip

The response must depend on the actual equipment, process, and safety design.

A PLC sequence should not be treated as a substitute for a properly engineered safety system.

11. Why State Machines Are Useful

Without a clear sequence structure, complex PLC programs can become difficult to understand.

You may end up with hundreds of conditions controlling different outputs.

A state-based design makes the process easier to describe:

IDLE
↓
FILL
↓
MIX
↓
DRAIN
↓
COMPLETE
This can make troubleshooting much easier.

When something goes wrong, an engineer can ask:

"Which state is the process currently in?"

That immediately narrows the investigation.
12. State Machine vs Simple Boolean Logic

Simple control:

IF Start THEN
    Pump := TRUE;
END_IF;

Sequence control:

IF State = FILLING THEN
    Pump := TRUE;
END_IF;
The second approach gives the pump a specific role within a larger process sequence.

The exact programming syntax depends on the PLC platform.

13. Conceptual Structured Text Example

A simplified example:
CASE State OF

    IDLE:
        Pump := FALSE;
        Mixer := FALSE;
        InletValve := FALSE;
        DrainValve := FALSE;

        IF StartCommand THEN
            State := FILLING;
        END_IF;


    FILLING:
        InletValve := TRUE;
        Pump := TRUE;

        IF HighLevel THEN
            State := MIXING;
        END_IF;


    MIXING:
        Mixer := TRUE;

        IF MixTimerDone THEN
            State := DRAINING;
        END_IF;


    DRAINING:
        DrainValve := TRUE;

        IF LowLevel THEN
            State := COMPLETE;
        END_IF;


    COMPLETE:
        State := IDLE;


    FAULT:
        Pump := FALSE;
        Mixer := FALSE;
        InletValve := FALSE;
        DrainValve := FALSE;

END_CASE;
This is conceptual Structured Text. Exact syntax and implementation depend on the PLC platform.

14. State Machine Design Principles

A good sequence should clearly define:

Entry Conditions

What causes the process to enter a state?

State Actions

What should the equipment do while in that state?

Exit Conditions
What causes the process to leave the state?

Fault Behavior

What happens if something goes wrong?

Recovery

How does the process return to a safe and controlled state?

15. State Machines and SCADA

State information can be extremely useful to SCADA operators.

Instead of only seeing:

Pump = ON
Valve = OPEN

SCADA could display:
Process State:
FILLING

Tank Level:
72%

Pump:
RUNNING

Inlet Valve:
OPEN
This provides more context to the operator.

A SCADA system can also display:

IDLE
FILLING
MIXING
DRAINING
COMPLETE
FAULT

The exact operator interface should be designed according to the process and HMI principles being used.

16. State Machines and Alarms

State information can also provide context for alarms.

For example:
State = FILLING
Tank Level = Not Increasing
Pump = Running

This could indicate a process problem worth investigating.

Compare that with:

State = IDLE
Pump = OFF
Tank Level = Not Increasing

The same physical measurement may have completely different meanings depending on the process state.

This is one reason context matters in industrial control systems.

🧪 17. Practical Exercise

Design a sequence for a simple water tank.
Process
IDLE
↓
FILLING
↓
FULL
↓
DRAINING
↓
EMPTY
↓
IDLE
States
IDLE
FILLING
FULL
DRAINING
EMPTY
FAULT
Inputs
StartCommand
HighLevel
LowLevel
PumpFault
EmergencyStop
Outputs
InletValve
Pump
DrainValve

Now define:

What happens in each state?
What causes each transition?
What happens if the pump faults during filling?
What happens if the high-level sensor never activates?
What should happen when Emergency Stop is activated?
How would SCADA display the current state?
🧠 18. Knowledge Check
Question 1

What does a state represent?

Answer: The current condition or stage of a process.

Question 2

What is a transition?

Answer: A condition or event that causes the process to move from one state to another.

Question 3

Why are state machines useful?

Answer: They provide a structured way to organize multi-step processes and can make sequence logic easier to understand, troubleshoot, and maintain.

Question 4

Can a state machine contain a FAULT state?

Yes.

A sequence can include fault handling, although safety-related functions may require separate dedicated safety systems depending on the application.

🔧 19. Common Mistakes

Avoid:

Creating states without clear transition conditions
Having multiple states control the same output unpredictably
Forgetting fault handling
Creating transitions that can never occur
Allowing a sequence to become stuck without diagnostics
Using unclear state names
Mixing safety functions into ordinary sequence logic without proper engineering
Assuming every PLC platform implements state machines in the same way
🏭 20. Real-World Thinking

Today I learned that industrial automation is often about controlling processes, not just individual devices.

A pump is one device.

A tank filling, mixing, and draining is a process.

State machines provide a structured way to describe that process:

IDLE
  ↓
FILL
  ↓
MIX
  ↓
DRAIN
  ↓
COMPLETE

This is another step toward thinking like an automation engineer rather than simply writing isolated PLC instructions.

📚 References
IEC 61131-3 — Programmable Controllers — Programming Languages
Siemens SIMATIC PLC programming documentation
Rockwell Automation Logix Designer documentation
Schneider Electric PLC programming documentation
📈 Progress

