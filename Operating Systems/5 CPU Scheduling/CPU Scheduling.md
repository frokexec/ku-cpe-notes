# CPU Scheduling

## Basic Concepts

- In a single-processor system, only one process can run at a time
- Any others must wait until the CPU is free and can be rescheduled
- A process is executed until it must wait, typically for the completion of some I/O request
- CPU just sits idle while a process is waiting for I/O to complete -> time wasted
- The object of [[Multiprogramming & Multitasking#Multi programming|multiprogramming]] is to have some process running at all times, to maximize *CPU utilization*
	- Several processes are kept in memory at one time
	- When one process has to wait, the OS *takes the CPU away from that process and gives the CPU to another process*
- [[CPU-IO Burst Cycle]]
- [[CPU Scheduler]] & [[Dispatcher]]
- [[Preemptive and Nonpreemptive Scheduling]]

[[Scheduling Algorithms]]
