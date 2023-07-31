# Processes

#index

## Process Concept

Process - a program in executing; process execution must progress in sequential fashion

Multiple parts

- Program code - text section
- Including PC and processor registers
- Stack - containing temporary data
- Data section - containing global vars
- Heap - containing memory dynamically allocated during run-time
- Program is passive entity
- Process is active entity

### Process in Memory

![[Pasted image 20230720091404.png]]

### Process State

- New - being created
- Ready - ready for CPU to process
- Running - running in CPU, is interrupted it will move back to ready
- Waiting - waiting for something e.g. I/O
- Terminated - done

![[Pasted image 20230720091644.png]]

### Process Control Block (PCB)

Information associated with each process

- Process state
- PC
- CPU registers
- CPU scheduling information - priorities, scheduling queue pointers
- Memory-management information - memory allocated in process
- Accounting information - CPU used, clock time elapsed since start
- I/O status information - I/O devices allocated to process, list of open files

#### [[Threads & Concurrency#Threads|Threads]]

- More threads more PC

### Process Scheduling

**Process scheduler** selects among available processes for next execution on CPU core
Goal is to maximize CPU use, quickly switch processes on CPU core

- **Ready queue** - ready to execute
- **Wait queues** - waiting for an event

These queues is a linked list pointing to PCB

### Representation of Process Scheduling

![[Pasted image 20230720070449.png]]

### CPU Switch From Process to Process

A **context switch** occurs when the CPU switches from one process to another

![[Pasted image 20230720070545.png]]

Nothing is executing between saving state and reloading state in PCB

### Context Switch

- When CPU switches to another process, the system must save the state of the old process and load the saved state for the new process via a **context switch**
- Context of a process represented in the PCB
- Context-switch time is pure **overhead**; the system does no useful work while switching

## Communication Between Processes

- [[Interprocess Communication]]
- [[Communications in Client-Server Systems]]

## Operation on Processes

Systems must provide mechanisms for

- [[Process Creation]]
- [[Process Termination]]

## Continue

[[Threads & Concurrency]]
