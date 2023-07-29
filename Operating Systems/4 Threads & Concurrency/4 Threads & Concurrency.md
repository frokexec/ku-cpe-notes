# 4 Threads & Concurrency

## Overview

### Threads

- a basic unit of CPU utilization.
- it comprises
	- thread ID
	- PC
	- register set
	- stack
 - it shares with other threads belonging to the same process its *code section, data section and other OS resources*
 - **different from threads in CPU specification** but they use hardware threads to execute their instructions

>  Threads in CPU specifications (hardware threads) are related to the physical capabilities of the processor to execute multiple threads concurrently, while threads in operating systems (execution threads or lightweight processes) are software-level constructs that allow for concurrent execution within a process.

### Motivation

Most software applications that run on modern computers and mobile devices are multithreaded. An application typically is implemented as a separate process with several threads of control.

- An application that creates photo thumbnails from a collection of images may use a separate thread to generate a thumbnail from each separate image.
- A web browser might have one thread display images or text while another thread retrieves data from the network.

![[Pasted image 20230729135556.png |Single-threaded and multithreaded processes]]
A busy web server may have several (perhaps thousands of) clients concurrently accessing it. If the web server ran as a traditional single-threaded process, it would be able to service only one client at a time.

One solution is to have the server run as a single process that accepts requests. When a request is made, rather than creating another process, the server creates a new thread to service the request and resumes listening for additional requests.

![[Pasted image 20230729144621.png |Multithreaded Server Architecture]]

### Benefits

- **Responsiveness** - Multithreading an interactive application may allow program to continue running even if part of it is blocked or is performing lengthy operation.
- **Resource Sharing** - Threads share resources of process which they belong. Easier than shared memory or message passing.
- **Economy** - Cheaper than process creation, thread switching *lower overhead than (process) context switching*
- **Scalability** - The benefits of multithreading can be greatly increased in a multiprocessor architecture, where threads may be running in parallel on different processors.

## Multicore Programming

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

### Types of parallelism

- **Data parallelism** - distributes subsets of the same data across multiple cores, same operation on each
- **Task parallelism** - distributing threads across cores, each thread performing unique operation

![[Pasted image 20230729172705.png |Data and Task Parallelism]]

### Amdahl's law

Identifies performance gains from adding additional cores to an
application that has both serial and parallel components

$speedup <= \frac{1}{S + (\frac{1-S}{N})}$

- S is serial portion
- N processing cores

![[Pasted image 20230729174522.png]]

### User Threads and Kernel Threads

#### User Threads

Management done by user-level threads library

- POSIX `Pthreads`
- Windows threads
- Java threads

#### Kernel threads

Supported by the kernel. Virtually all general-purpose OS including:

- Windows
- Linux
- macOS
- iOS
- Android

![[Pasted image 20230729194400.png]]

## Multithreading Models

### Many-to-One

- Many user-level threads mapped to single kernel thread
- One thread blocking causes all to block
	- the entire process will block if a thread makes a blocking system call
- Few systems currently use this model

![[Pasted image 20230729195009.png]]

### One-to-one

- Each user-level thread maps to kernel thread
- Creating a user-level thread creates a kernel thread
- More concurrency than many-to-one
- Number of threads per process sometimes restricted due to overhead

![[Pasted image 20230729195038.png]]

### Many-to-Many

- Allows many user level threads to be mapped to many kernel threads
- Allows the OS to create a sufficient number of kernel threads

![[Pasted image 20230729195048.png]]

### Two-level

- Similar to M:M, except that it allows a user thread to be bound to kernel thread
- Associates multiple ULTs with a smaller number of KLTs
