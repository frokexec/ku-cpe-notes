#preemptive 
# Multilevel Feedback Queue

- A process can move between the various queues.
- Multilevel-feedback-queue scheduler defined by the following parameters:
- Number of queues
	- Scheduling algorithms for each queue
	- Method used to determine when to upgrade a process
	- Method used to determine when to demote a process
	- Method used to determine which queue a process will enter when that process needs service
- Aging can be implemented using multilevel feedback queue

## Example

- Three queues:
	- Q0–RR with time quantum 8 milliseconds
	- Q1–RR time quantum 16 milliseconds
	- Q2–FCFS
- Scheduling
	- A new process enters queue Q0 which is served in RR
		- When it gains CPU, the process receives 8 milliseconds
		- If it does not finish in 8 milliseconds, the process is moved to queue Q1
	- At Q1 job is again served in RR and receives 16 additional milliseconds
		- If it still does not complete, it is preempted and moved to queue Q2


![[Pasted image 20230808110629.png]]
