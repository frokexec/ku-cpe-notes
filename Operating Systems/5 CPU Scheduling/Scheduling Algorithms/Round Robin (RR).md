#preemptive

# Round Robin (RR)

- Each process gets a small unit of CPU time (time quantum q), usually 10-100 milliseconds. After this time has elapsed, the process is preempted and added to the end of the ready queue.
- If there are n processes in the ready queue and the time quantum is q, then each process gets 1/n of the CPU time in chunks of at most q time units at once. No process waits more than (n-1)q time units.
- Timer interrupts every quantum to schedule next process
- performance
	- q large -> FCFS
	- q small -> RR
- Note that q must be large with respect to context switch, otherwise overhead is too high
- Typically, higher average turnaround than SJF, but better response
- q should be large compared to context switch time
- q usually 10 milliseconds to 100 milliseconds,
- Context switch < 10 microseconds

![[Pasted image 20230808004908.png]]

![[Pasted image 20230808004215.png]]
