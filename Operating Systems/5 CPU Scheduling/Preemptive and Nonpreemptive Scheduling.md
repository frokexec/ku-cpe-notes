# Preemptive and Nonpreemptive Scheduling

CPU-scheduling decisions may take place under the following four circumstances

1. When a process switches from the *running state* to the *waiting state*
2. When a process switches from the *running state* to the *ready state* (when interrupt occurs)
3. When a process switches from the *waiting state* to the *ready state* (at completion of I/O)
4. When a process *terminates*

- No choice for situations 1 and 4 (the process is not ready).
- There is a choice for situation 2 and 3

When scheduling takes places only under *circumstances 1 and 4*, we say that the scheduling scheme is *nonpreemptive*; otherwise, it is *preemptive*.
