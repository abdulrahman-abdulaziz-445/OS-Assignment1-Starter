# Assignment Questions

## Instructions
Answer all 4 questions with detailed explanations. Each answer should be **3-5 sentences minimum** and demonstrate your understanding of the concepts.

---

## Question 1: Thread vs Process

**Question**: Explain the difference between a **thread** and a **process**. Why did we use threads in this assignment instead of creating separate processes?

**Your Answer:**

A process is an independent execution unit with its own virtual address space and allocated resources, while a thread is a lightweight sub unit that shares the same memory heap, We used threads because they avoid the massive overhead of process communication and the heavy context switching costs associated with separate memory blocks. By sharing the same address space, our threads could directly access and update the shared processMap and processQueue in real time, This approach made the simulation significantly more efficient and easier to implement than launching twenty separate system processes

---

## Question 2: Ready Queue Behavior

**Question**: In Round-Robin scheduling, what happens when a process doesn't finish within its time quantum? Explain using an example from your program output.

**Your Answer:**

If a process like P1 isn't finished when its time is up, the scheduler essentially acts like a polite bouncer and tells it to head to the back of the line. In our code, this happens whenever remainingTime is still greater than zero after a quantum runs. You’ll see the program print "yields CPU for context switch" before popping that thread right back into the processQueue. It’s the digital version of a "fair play" rule, ensuring one heavy task doesn't hog the CPU while everyone else is stuck waiting.

Example from my output:
```
╔════════════════════════════════════════════════════════════════════════════════╗
║                     ✓  ALL PROCESSES COMPLETED  ✓                            ║
╚════════════════════════════════════════════════════════════════════════════════╝

  Total context switches: 26

╔════════════════════ SUMMARY TABLE ════════════════════╗
║ Process Name    | Burst Time      | Waiting Time    ║
╠═══════════════════════════════════════════════════════╣
║ P1              | 2640        ms | 3           ms ║
║ P2              | 3851        ms | 35204       ms ║
║ P3              | 4071        ms | 36073       ms ║
║ P4              | 2105        ms | 8731        ms ║
║ P5              | 4399        ms | 37169       ms ║
║ P6              | 5364        ms | 38580       ms ║
║ P7              | 3417        ms | 40962       ms ║
║ P8              | 7078        ms | 48741       ms ║
║ P9              | 7221        ms | 49833       ms ║
║ P10             | 4271        ms | 47445       ms ║
║ P11             | 1872        ms | 28994       ms ║
║ P12             | 7350        ms | 51081       ms ║
║ P13             | 2758        ms | 33906       ms ║
║ P14             | 1524        ms | 36683       ms ║
```

**Explanation of example:**
- every process in the queue reached a remainingTime of 0.
- This number tracks how many times the CPU swapped tasks. total is 26, proves the scheduler didn't just run every process once


---

## Question 3: Thread States

**Question**: A thread can be in different states: **New**, **Runnable**, **Running**, **Waiting**, **Terminated**. Walk through these states for one process (P1) from your simulation.

**Your Answer:**

[Write your answer here. For each state, explain when P1 enters that state during the simulation. Use your understanding of the code to trace through the lifecycle.]

1. **New**: P1 is in the New state the moment the Process process = new Process(...) line runs inside the for loop. At this point, the process object and its thread have been created in memory, but the thread hasn't actually started doing anything yet

2. **Runnable**: P1 enters the Runnable state when processQueue.add(thread) is called. In Java, once a thread is added to a scheduler and is ready to be picked, It’s not actually using the CPU yet, but it's waiting its turn in the queue.

3. **Running**: P1 moves to the Running state the moment the code executes currentThread.start(). This triggers the run() method in the Process class.

4. **Waiting**: P1 enters a Waiting state TIMED_WAITING during two : Thread.sleep(stepTime) / currentThread.join()

5. **Terminated**: P1 reaches the Terminated state once its remainingTime hits 0 and the run() method finishes. 

---

## Question 4: Real-World Applications

**Question**: Give **TWO** real-world examples where Round-Robin scheduling with threads would be useful. Explain why this scheduling algorithm works well for those scenarios.

**Your Answer:**

### Example 1: [Name of application/scenario]

**Description**: 
[Describe the real-world scenario or application]

**Why Round-Robin works well here**: 
[Explain why Round-Robin scheduling is suitable. Consider fairness, responsiveness, predictability, etc.]

### Example 2: [Name of application/scenario]

**Description**: 
[Describe the real-world scenario or application]

**Why Round-Robin works well here**: 
[Explain why Round-Robin scheduling is suitable. Consider fairness, responsiveness, predictability, etc.]

---

## Summary

**Key concepts I understood through these questions:**
1. 
2. 
3. 

**Concepts I need to study more:**
1. 
2. 
