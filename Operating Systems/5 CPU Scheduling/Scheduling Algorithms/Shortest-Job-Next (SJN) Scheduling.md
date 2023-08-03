# Shortest-Job-Next (SJN) Scheduling

#nonpreemptive

- aka Shortest Job First (SJF)
- Associate with each process the length of its next CPU burst
- Use these lengths to schedule the process with the shortest time
- SJN is optimal–gives minimum average waiting time for a given set of processes
- Preemptive version called [[Shortest-Remaining-Time-First Scheduling]]
- How do we determine the length of the next CPU burst?
	- Could ask the user
	- Estimate
	- [[Determining Length of Next CPU Burst]]

|Process| Burst Time|
|-|-|
|P1|6|
|P2|8|
|P3|7|
|P4|3|

SJF scheduling chart

![[Pasted image 20230803170104.png]]

Average waiting time = (3 + 16 + 9 + 0) / 4 = 7
