# Shortest-Remaining-Time-First Scheduling

#preemptive

- Preemptive version of [[Shortest-Job-Next (SJN) Scheduling|SJN]]
- Whenever a new process arrives in the ready queue, the decision on which process to schedule next is redone using the [[Shortest-Job-Next (SJN) Scheduling|SJN]] algorithm.

|Process|Arrival Time|Burst Time|
|-|-|-|
|1|0|8|
|2|1|4|
|3|2|9|
|4|3|5|

![[Pasted image 20230803170832.png]]

Average waiting time = \[(10-1)+(1-1)+(17-2)+(5-3)\]/4 = 26/4 = 6.5
