# CPU Scheduler

Whenever the CPU becomes idle, the OS must *select one of the processes in the ready queue* to be executed. The selection process is carried out by the *CPU scheduler*.

Note that the ready queue is not necessarily a first-in, first-out (FIFO) queue. As we shall see when we consider the various *scheduling algorithms*, a ready queue can be implemented as a FIFO queue, a priority queue, a tree, or simply an unordered linked list.
