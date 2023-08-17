#nonpreemptive #preemptive 

# Multilevel Queue

- The ready queue consists of multiple queues
- Multilevel queue scheduler defined by the following parameters:
	- Number of queues
	- Scheduling algorithms for each queue
	- Method used to determine which queue a process will enter when that process needs service
	- Scheduling among the queues
- No process in lower priority queue will run unless the queue with higher priority is empty

## Characteristics

- Multiple queues
- Queue assignments - Each queue is assigned a different priority
- Scheduling algorithms - Each queue operates with its own algorithm
- Queue management - Each queue is managed independently
- Fairness and starvation prevention
	- Priority adjustments
	- Aging
- Migration - a process may migrate to another queue based on their performance characteristics

![[Pasted image 20230808103625.png]]
