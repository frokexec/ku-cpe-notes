# First-Come, First-Served (FCFS) Scheduling

#nonpreemptive

|Process|Burst Time|
|-|-|
|P1|24|
|P2|3|
|P3|3|

Suppose that the processes arrive in the order: P1, P2, P3
The Gantt Chart for the schedule is:

![[Pasted image 20230803165409.png]]

- Waiting time for P1 = 0; P2 = 24; P3 = 27
- Average waiting time: (0 + 24 + 27)/3 = 17

Suppose that the processes arrive in the order: P2, P3, P1
The Gantt chart for the schedule is:
![[Pasted image 20230803165234.png]]

- Waiting time for P1 = 6; P2 = 0; P3 = 3
- Average waiting time: (6 + 0 + 3)/3 = 3
- Much better than previous case
- Convoy effect - short process behind long process
	- Consider one CPU-bound and many I/O-bound processes
