# Implicit Threading

## Implicit Threading

One way to address these difficulties and better support the design of concurrent and parallel applications is to transfer the creation and management of threading from application developers to compilers and run-time libraries. This strategy, termed *implicit threading*.

- Growing in popularity as number of threads increase, program correctness more difficult with explicit threads
- Creating and management of threads done by compilers and run-time libraries rather than programmers (👍)
- Five methods explored
	- Thread Pools
	- Fork-Join
	- OpenMP
	- Grand Central Dispatch
	- Intel Threading Building Blocks

These strategies generally require application developers to
identify tasks—not threads—that can run in parallel.
Typically using the [[Implicit Threading#Many-to-Many |Many to Many Model]].

### Thread Pools

- Collection of pre-created threads
- Threads can be reused to execute multiple tasks
- Avoid the overhead of thread creation
- Advantages
	- Faster to service a request with an existing thread than creating a new thread

### Fork-Join

- Multiple threads (tasks) are *forked*, and then *joined*
- Break down a task into smaller sub-tasks (forking)
- Combine the results to obtain the final result (joining)
- well-suited for *recursive algorithms* or tasks that can be divided into independent parts

![[Pasted image 20230731122313.png |Fork-join parallelism]]

![[Pasted image 20230731122342.png |Fork-join parallelism]]

### OpenMP

An API that supports *shared-memory* multiprocessing programming in C, C++, and FORTRAN.

- Allows developers to parallelize sections of code by inserting *compiler directives*, *pragmars*, or using runtime
- Developers can Identify *parallel regions* blocks of code that can run in parallel

### Grand Central Dispatch (GCD)

- Developed by Apple for managing concurrency on Apple platforms
- It handles the underlying thread management and load balancing *automatically*.
- A task can be expressed either as a [function](https://en.wikipedia.org/wiki/Subroutine "Subroutine") or as a "[block](https://en.wikipedia.org/wiki/Blocks_(C_language_extension) "Blocks (C language extension)")".
- Blocks are placed in *dispatch queue* (FIFO)
	- Assigned to available thread in thread pool when removed from queue
- Two types of ***dispatch queues***
	- **serial** - blocks removed in FIFO order, queue is per process, called *main queue*
		- executes tasks one at a time
		- each task must complete before the next one starts
		- useful when user want to perform tasks in *specific order*
	- **concurrent** - removed in FIFO order but several may be removed a time
		- executes multiple tasks concurrently (may start and finish at different times)
		- enables efficient use of multiple cores
		- improve performance for tasks that can be *executed independently*
		- ideal for tasks that don't have dependencies on each other

![[Pasted image 20230731124931.png]]

### Intel Threading Building Blocks (TBB)

- A C++ template library for parallel programming
- Simplifies the creation of multithreaded applications
- The task scheduler provides load balancing and is cache aware
- A serial version of a simple for loop

```cpp
for (int i= 0; i< n; i++) {
	apply(v[i]);
}
```

- The same loop written using TBB with `parallel_for` statement:

```cpp
parallel_for (size_t(0), n, [=](size_t i) {apply(v[i]);});
```
