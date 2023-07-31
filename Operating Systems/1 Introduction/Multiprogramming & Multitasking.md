# Multiprogramming & Multitasking

|                                  | Multiprogramming                                                                                                                        | Multitasking                                                                                                                |
| -------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| What it is?                      | The concurrent residency of more than one program in the main memory is called as multiprogramming                                      | The execution of more than one task simultaneously is called as multitasking.                                               |
| Purpose                          | Multiprogramming is useful in reducing the CPU idle time and it improves the throughput.                                                | Multitasking is used to execute several task at once to boost the CPU throughput.                                           |
| Number of CPU                    | In multiprogramming, only one CPU is required to the tasks.                                                                             | In multitasking, multiple CPUs are needed to accomplish the task.                                                           |
| Job processing time              | Multiprogramming requires more time to process the jobs                                                                                 | Multitasking requires moderate amount of time.                                                                              |
| Number of process being executed | One process is executed at a time. Once the process is completed, the system suspends that process and select a new process to execute. | In multitasking, multiple jobs can run concurrently, and the CPU is assigned to a certain job for a fixed duration of time. |
| Number of users                  | One at a time.                                                                                                                          | More than one                                                                                                               |
| Throughput                       | Throughput is less.                                                                                                                     | Throughput is moderate.                                                                                                     |
| Efficiency                       | Less                                                                                                                                    | Moderate                                                                                                                    |
| Categories                       | No further divisions                                                                                                                    | Single User & Multiuser.                                                                                                    |
| CPU switching                    | In multiprogramming, the CPU switches between processes swiftly.                                                                        | In multitasking, the CPU switches among the processes of several programs.                                                  |
| Mechanism                        | Multiprogramming uses the context switching mechanism.                                                                                  | Multitasking uses the timesharing mechanism.                                                                                |

## Multi programming

Multi-programming increases CPU utilisation by organising jobs (code and data) so that the CPU always has one to execute. The idea is to keep multiple jobs in main memory. If one job gets occupied with IO, CPU can be assigned to other job.

![[Pasted image 20230718225330.png]]

## Multi-tasking

Multi-tasking is a logical extension of multi-programming. Multitasking is the ability of an OS to execute more than one task simultaneously on a CPU machine. These multiple tasks share common resources (like CPU and memory). In multi-tasking systems, the CPU executes multiple jobs by switching among them typically using a small time quantum, and the switches occur so quickly that the users feel like interact with each executing task at the same time.

### Keywords

- process
- CPU scheduling
- swapping
- virtual memory

![[Pasted image 20230718225359.png]]
