---
---
# The Fundamentals

### Every Program is
```
causes --> black box --> effects
```

### Input and Output
```javascript
Input:   time              // cause
Output:  terminal          // effect
Input:   time, numbers     // cause
Output:  numbers           // effect
Input:   time, voice       // cause
Output:  gate opnes        // effect
```

### The Controller
- A program is always listening for inputs (like clicks, commands, voltage—but at least for time).
```
inputs   -->  controller 
outputs  <--  controller
```

### The Role of the Controller
- **The controller is what is listening.**
- There's always an invisible: `if (true)` or `while (true)`
- The controller calls **use case interactors**.
- **Use case interactors** are made of:
  - Domain objects
  - Ports
    - **Ports** are implemented as **adapters**.

---
---

# Types of Inputs/Causes

### Entry Point Inputs
- Examples:
  - The `args` in `Main(string[] args) {}`
  - External configuration files
  - Environment variables

### Runtime Inputs
- Examples:
  - HTTP requests
  - Console input (`Console.ReadLine()`)
  - Voltage change
    
---
---

# Types of Controllers

### Entry Point Controllers
- Control what happens based on entry point inputs.
- Examples:
  - Service configuration
  - Dependency injection (DI) registration

### Runtime Controllers
- Control what happens based on runtime inputs.
- Examples:
  - A web server (itself a controller)
  - A loop listening for voltage changes
  - A scheduled job (listens to time as an implicit runtime input)

---
---

# Primary Axis: Program Lifetime

### Terminating Programs
- Programs that execute for a finite duration and terminate after completing their task.
- Examples:
  - File compressors
  - Compilers
  - One-off scripts

### Long-running Programs
- Programs designed to keep running indefinitely or until explicitly terminated.
- Examples:
  - Web servers
  - System daemons
  - Background services

---
---

# Secondary Axis: Mode of Operation

### Interaction as a Fundamental Concept
- At the core, a program can be seen as a function of time and other optional inputs:
  ```
  Effects = f(Causes)
  Causes = [time, optionally anything else]
  ```

- **Listening to triggers**: Programs explicitly wait for external events
  - Examples:
    - Network requests
    - User input
    - Sensory data 
- **Listening to time**: Programs implicitly react to time.
  - Examples:
    - A sleep timer in a terminating program.
    - Iterations in a loop tied to the system clock.
    - Daemons waiting for scheduled tasks (e.g., `cron`).


### The Illusion of "Non-Interactivity"
- **Terminating Programs**: May appear non-interactive due to limited or predefined input/output interactions (e.g., reading a file and producing an output). However:
  - They interact with system resources (e.g., disk, memory, CPU cycles).
  - Time dictates when they begin and end.

- **Daemon or Server Programs**: Seem autonomous but are constantly monitoring (interacting with) triggers like requests or system events.

---
---

# Key Insight
**Time is an implicit input to all programs, and every program is interactive.**
