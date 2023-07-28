# Process Concept

Process - a program in executing; process execution must progress in sequential fashion

Multiple parts

- Program code - text section

- Including PC and processor registers

- Stack - containing temporary data

- Data section - containing global vars

- Heap - containing memory dynamically allocated during run-time

- Program is passive entity

- Process is active entity

## Process in Memory

![[Pasted image 20230720091404.png]]

## Process State

- New - being created
- Ready - ready for CPU to process
- Running - running in CPU, is interrupted it will move back to ready
- Waiting - waiting for something e.g. I/O
- Terminated - done

![[Pasted image 20230720091644.png]]

## Process Control Block (PCB)

Information associated with each process

- Process state
- PC
- CPU registers
- CPU scheduling information - priorities, scheduling queue pointers
- Memory-management information - memory allocated in process
- Accounting information - CPU used, clock time elapsed since start
- I/O status information - I/O devices allocated to process, list of open files

### Threads

- More threads more PC

## Process Scheduling

**Process scheduler** selects among available processes for next execution on CPU core
Goal is to maximize CPU use, quickly switch processes ibti CPU core

- **Ready queue** - ready to execute
- **Wait queues** - waiting for an event

These queues is a linked list pointing to PCB

## Representation of Process Scheduling

![[Pasted image 20230720070449.png]]

## CPU Switch From Process to Process

A **context switch** occurs when the CPU switches from one process to another

![[Pasted image 20230720070545.png]]

Nothing is executing between saving state and reloading state in PCB

## Context Switch

- When CPU switches to another process, the system must save the state of the old process and load the saved state for the new process via a **context switch**
- Context of a process represented in the PCB
- Context-switch time is pure **overhead**; the system does no useful work while switching

# Operation on Processes

Systems must provide mechanisms for

- Process **creation**
- Process **termination**

## Process Creation

Parent process create children processes, forming a tree or processes.
Process is identified and managed via a **process identifier** (PID).

### Resource sharing options

```
- Parent and children share all resources
- Children share subset of parent's resources
- Parent and child share no resources
```

### Execution option

- Execute concurrently
- Parent waits until children terminate

### Address space

The range of virtual addresses that the operating system assigns to a user or separately running program

- Child duplicate of parent
- Child has a program loaded into it

### Tree or processes in Linux

See `pstree`

![[Pasted image 20230720092536.png]]

## Process Termination

A process terminates when it finishes executing its final statement and asks
the operating system to delete it by using the `exit()` system call.

- Return child status to parent
- Process's resources are deallocated by OS.

Parent may terminate the execution of children processes using `abort()` system call for

- Child has exceeded allocated resources
- Task assigned to child in no longer required
- The parent is exiting (**cascading termination**)

### Zombie Process
A process that has completed its task but the parent is not reading the process state. In the other words, if no parent waiting process is a **zombie**

### Orphan Process
If parent terminated without invoking `wait()`, process is an **orphan**

See https://www.geeksforgeeks.org/difference-between-zombie-orphan-and-daemon-processes/

# Interprocess Communication

Processes can be **independent** or **cooperating**

- Cooperating processes need interprocess communication (IPC)

Two models of IPC (more in textbook)

- Shared memory
- Message passing

![[Pasted image 20230720101845.png]]

## Producer-Consumer Problem

Producer _process_ produces information that is consumed by _consumer_ process

One solution to the producer–consumer problem uses shared memory.
To allow producer and consumer processes to run concurrently, we must have available a buffer of items that can be filled by the producer and emptied by the consumer.

Two variations:
- unbounded-buffer (no practical limit on the size of buffer)
  - producer never waits
  - consumer waits if there is **no buffer to consume**
- bounded-buffer
  - producer must wait if all buffers are full
  - consumer waits if there is no buffer to consume

## IPC - Shared Memory

An area of memory shared among the processes that wish to communicate

- The communication is **under the control of users processes** not the OS

## What about Filling all the Buffers?

Suppose that we wanted to provide a solution to the consumer- producer problem that fills all the buffers.

We can do so by having an integer **counter** that keeps track of the number of full buffers.

- Initially, counter is set to 0
- Produce: counter += 1
- Consume: counter -= 1

## IPC - Message Passing

Processes communicate with each other without resorting to shared variables

Two operations:
- `send(message)`
- `receive(message)`

The message size can be fixed or variable

If processes `P` and `Q` which to communicate, they need to:
- Establish a **communication link** between them
- Exchange messages via send/receive

## Implementation of Communication Link
- Physical
	- Shared memory
	- Hardware bus
	- Network
- Logical
	- Direct or indirect
	- **Synchronous or asynchronous**
	- Automatic or explicit buffering

## Direct Communication
 Processes must name each other explicitly:
	- `send(P,message)`
	- `receive(Q,message)`

Properties of communication link
- A link is established automatically between every pair of processes that want to communicate
- A link is associated with **exactly two processes**
- Between each pair of processes, there exists exactly one link
 

## Indirect Communication
Messages are directed and received from mailboxes or ports
- Each mailbox has a unique id
- Processes can communicate only if they share a mailbox

Properties of communication link
- A link is established between a pair of processes only if both members of the pair have a shared mailbox
- A link may be associated with more than two processes
- Between each pair of communicating processes, a number of different links may exist, with each link corresponding to one mailbox

## Synchronization

### Blocking
- Blocking send - the sender is blocked until the message is revived
- Blocking receive - the receiver is blocked until a message is available

### Non-blocking
- Non-blocking send - the sender sends the message and continue
- Non-blocking receive - the receiver receives a valid message or null message

## Buffering
Queue of messages attached to the link

- Zero capacity - no messages are queued on a link. Sender must wait for receive (rendezvous)
- Bounded capacity - finite length of n messages, sender must wait if link is full
- Unbounded capacity - infinite length, sender never waits