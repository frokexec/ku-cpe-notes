# Threads & Concurrency

#index

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

## Links

[[Multicore Programming]]

[[Multithreading Models]]

[[Thread Libraries]]

[[Implicit Threading]]

[[Threading Issues]]

[[Operating System Examples]]
