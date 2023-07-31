# Multicore Programming

- Multicore or multiprocessor systems puts pressure on programmers, challenges include:
	- Dividing activities
	- Balance
	- Data splitting
	- Data dependency
	- Testing and debugging
 - **Parallelism** implies a system can perform more than one task simultaneously
 - **Concurrency** supports more than one task making progress
	 - Single processor / core, scheduler providing concurrency

![[Pasted image 20230729151255.png]]

## Types of parallelism

- **Data parallelism** - distributes subsets of the same data across multiple cores, same operation on each
- **Task parallelism** - distributing threads across cores, each thread performing unique operation

![[Pasted image 20230729172705.png |Data and Task Parallelism]]

## Amdahl's law

Identifies performance gains from adding additional cores to an
application that has both serial and parallel components

$speedup \le \frac{1}{S + (\frac{1-S}{N})}$

- S is serial portion
- N processing cores

![[Pasted image 20230729174522.png]]

## User Threads and Kernel Threads

### User Threads

Management done by user-level threads library

- POSIX `Pthreads`
- Windows threads
- Java threads

### Kernel threads

Supported by the kernel. Virtually all general-purpose OS including:

- Windows
- Linux
- macOS
- iOS
- Android

![[Pasted image 20230729194400.png]]
