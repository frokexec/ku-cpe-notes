# Scheduling Criteria

Different CPU-scheduling algorithms have different properties, and the choice of a particular algorithm may favor one class of processes over another. In choosing which algorithm to use in a particular situation, we must consider the properties of the various algorithms.

Many criteria have been suggested for comparing CPU-scheduling algorithms. Which characteristics are used for comparison can make a substantial difference in which algorithm is judged to be best. The criteria include the following:

- Max **CPU utilization** - keep the CPU as busy as possible
- Max **Throughput** - Number of processes that complete their execution per time unit
- Min **Turnaround time** - Sum of the periods spent waiting to get into memory, waiting in the ready queue, executing on the CPU, and doing I/O. (Completion Time - Arrival Time)
- Min **Waiting time** - Amount of the a process has been *waiting in the ready queue*
- Min **Response time** - The time from the submission of a request until the first response is produced.

## Algorithms

- [[First-Come, First-Served (FCFS) Scheduling]]
- [[Shortest-Job-Next (SJN) Scheduling]]
- [[Shortest-Remaining-Time-First Scheduling]]
