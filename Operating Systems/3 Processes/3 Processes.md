# 3 Processes

## Process Concept

Process - a program in executing; process execution must progress in sequential fashion

Multiple parts

- Program code - text section
- Including PC and processor registers
- Stack - containing temporary data
- Data section - containing global vars
- Heap - containing memory dynamically allocated during run-time
- Program is passive entity
- Process is active entity

### Process in Memory

![[Pasted image 20230720091404.png]]

### Process State

- New - being created
- Ready - ready for CPU to process
- Running - running in CPU, is interrupted it will move back to ready
- Waiting - waiting for something e.g. I/O
- Terminated - done

![[Pasted image 20230720091644.png]]

### Process Control Block (PCB)

Information associated with each process

- Process state
- PC
- CPU registers
- CPU scheduling information - priorities, scheduling queue pointers
- Memory-management information - memory allocated in process
- Accounting information - CPU used, clock time elapsed since start
- I/O status information - I/O devices allocated to process, list of open files

#### Threads

- More threads more PC

### Process Scheduling

**Process scheduler** selects among available processes for next execution on CPU core
Goal is to maximize CPU use, quickly switch processes ibti CPU core

- **Ready queue** - ready to execute
- **Wait queues** - waiting for an event

These queues is a linked list pointing to PCB

### Representation of Process Scheduling

![[Pasted image 20230720070449.png]]

### CPU Switch From Process to Process

A **context switch** occurs when the CPU switches from one process to another

![[Pasted image 20230720070545.png]]

Nothing is executing between saving state and reloading state in PCB

### Context Switch

- When CPU switches to another process, the system must save the state of the old process and load the saved state for the new process via a **context switch**
- Context of a process represented in the PCB
- Context-switch time is pure **overhead**; the system does no useful work while switching

## Operation on Processes

Systems must provide mechanisms for

- Process **creation**
- Process **termination**

### Process Creation

Parent process create children processes, forming a tree or processes.
Process is identified and managed via a **process identifier** (PID).

#### Resource sharing options

```
- Parent and children share all resources
- Children share subset of parent's resources
- Parent and child share no resources
```

#### Execution option

- Execute concurrently
- Parent waits until children terminate

#### Address space

The range of virtual addresses that the operating system assigns to a user or separately running program

- Child duplicate of parent
- Child has a program loaded into it

#### Tree or processes in Linux

See `pstree`

![[Pasted image 20230720092536.png]]

### Process Termination

A process terminates when it finishes executing its final statement and asks
the operating system to delete it by using the `exit()` system call.

- Return child status to parent
- Process's resources are deallocated by OS.

Parent may terminate the execution of children processes using `abort()` system call for

- Child has exceeded allocated resources
- Task assigned to child in no longer required
- The parent is exiting (**cascading termination**)

#### Zombie Process

A process that has completed its task but the parent is not reading the process state. In the other words, if no parent waiting process is a **zombie**

#### Orphan Process

If parent terminated without invoking `wait()`, process is an **orphan**

See <https://www.geeksforgeeks.org/difference-between-zombie-orphan-and-daemon-processes/>

## Interprocess Communication

Processes can be **independent** or **cooperating**

- Cooperating processes need interprocess communication (IPC)

Two models of IPC (more in textbook)

- Shared memory
- Message passing

![[Pasted image 20230720101845.png]]

### Producer-Consumer Problem

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

### IPC - Shared Memory

An area of memory shared among the processes that wish to communicate

- The communication is **under the control of users processes** not the OS

### What about Filling all the Buffers?

Suppose that we wanted to provide a solution to the consumerproducer problem that fills all the buffers.

We can do so by having an integer **counter** that keeps track of the number of full buffers.

- Initially, counter is set to 0
- Produce: counter += 1
- Consume: counter -= 1

### IPC - Message Passing

![Message Passing System](https://www.tutorialspoint.com/assets/questions/media/60294/message%20passing%20technique.jpg)

Processes communicate with each other without resorting to shared variables

Two operations:

- `send(message)`
- `receive(message)`

The message size can be fixed or variable

If processes `P` and `Q` which to communicate, they need to:

- Establish a **communication link** between them
- Exchange messages via send/receive

### Implementation of Communication Link

- Physical
	- Shared memory
	- Hardware bus
	- Network
- Logical
	- Direct or indirect
	- **Synchronous or asynchronous**
	- Automatic or explicit buffering

### Direct Communication

 Processes must name each other explicitly:
	- `send(P,message)`
	- `receive(Q,message)`

Properties of communication link

- A link is established automatically between every pair of processes that want to communicate
- A link is associated with **exactly two processes**
- Between each pair of processes, there exists exactly one link

### Indirect Communication

Messages are directed and received from mailboxes or ports

- Each mailbox has a unique id
- Processes can communicate only if they share a mailbox

Properties of communication link

- A link is established between a pair of processes only if both members of the pair have a shared mailbox
- A link may be associated with more than two processes
- Between each pair of communicating processes, a number of different links may exist, with each link corresponding to one mailbox

### Synchronization

#### Blocking (Synchronous)

- **Blocking send** - the sender is blocked **until the message is received**
- **Blocking receive** - the receiver is blocked until a message is available

#### Non-blocking (Asynchronous)

- **Non-blocking send** - the sender sends the message and continue
- **Non-blocking receive** - the receiver receives a valid message or null message

### Buffering

Queue of messages attached to the link

- **Zero capacity** - _no messages are queued_ on a link. Sender must wait for receive (_rendezvous_, only one message can pass at a time)
- **Bounded capacity** - finite _length of n_ messages, sender must wait if link is full
- **Unbounded capacity** - _infinite length_, sender never waits

### Example IPC Systems

#### POSIX IPC Systems

- Uses POSIX Shared Memory
	- Process creates/opens shared memory segment
		`shm_fd = shm_open(name, O_CREAT | O_RDWR, 0666)`
	- Set the size of the object (`ftruncate(shm_fd, 4096`)
	- Memory-map (`mmap`) a file pointer to the shared memory object
	- Reading and writing to shared memory is done by using the pointer returned by `mmap()`

#### Mach IPC Systems

- Message based
	- Even system calls are messages
	- Each task gets two ports at creation - _Kernel_ and _Notify_
	- Messages are sent and received using `mach_msg()`
	- Ports needed for communication, created via `mach_port_allocate()`
	- Send and receive are flexible; for example four options if mailbox full:
		- Wait indefinitely
		- Wait at most n milliseconds
		- Return immediately
		- Temporarily cache a message

#### Windows IPC Systems

- Message-passing centric via advanced _local procedure call (LPC)_ facility
	![[Pasted image 20230728210011.png]]
- Only works between processes on the same system
- Use ports (like mailboxes) to establish and maintain communication channels
- Communication works as follows:
	- The client opens a _handle_ to the subsystem's _connection port_ object
	- The client sends a connection request
	- The server creates two private _communication ports_ and returns the handle to one of them to the client
	- The client and server use the corresponding port handle to send messages or callbacks and to listen for replies

### Pipes

Conceptually, a pipe is a connection between two processes, such that the standard output from one process becomes the standard input of the other process. [s](https://www.geeksforgeeks.org/pipe-system-call/)

#### Piping issues

- Is communication unidirectional or bidirectional
- In the case of two-way communication, is it half or full-duplex?
- Must there exists a relationship (i.e., _parent-child_) between the communicating processes?
- Can the pipes be used over a network?

#### Type of pipes

- **Ordinary pipes** - cannot be accessed from outside the process that created it. Typically, a parent process creates a pipe and uses it to communicate with a child process that it created.
- **Named pipes** - can be accessed _without_ a parent-child relationship

#### Ordinary pipes (anonymous pipes)

- Unidirectional
- Allow communication in standard producer-consumer style
- Producer writes to one end (write-end)
- Consumer reads from the other end (read-end)
- **Require parent-child relationship** between communicating processes

![[Pasted image 20230728215558.png]]

#### Named Pipes (FIFOs)

- More versatile and offer more capabilities than ordinary pipes
- Can facilitate communication between unrelated processes and persist even after the processes are terminated
- **No parent-child relationship is necessary**
- Several processes can use the named pipe for communication

![[Pasted image 20230728220131.png]]

## Communications in Client-Server Systems

### Sockets

Sockets are a programming interface that allows processes to communicate over a network, either locally or across different machines. They provide a standard mechanism for IPC between processes running on different devices, using different OS, or even different networks.

- Concatenation of IP address and _port_ - a number included at start of message packet to differentiate network services on a host
- Communication consists between a pair of sockets
- All ports below 1024 are used for standard services
- Special IP address 127.0.0.1 (_loopback_) to refer to system on which process is running

#### Types of sockets

- **Transmission Control Protocol (TCP)**
	- Reliable, connection-oriented
	- The data is sent _in streams_, _ensuring that all data arrives_ in the correct order and without errors.
	- Is well-suited for application that require data integrity
		- Web browsers
		- Email clients
		- File transfer applications
- **User Datagram Protocol (UDP)**
	- Unreliable, connectionless communication
	- Data is sent as _individual packets_, and there is _no guarantee_ of delivery, order, or error checking.
	- Used in applications where speed and reduced overhead are critical than data reliability
		- Video streaming
		- Online gaming
		- DNS

### Remote Procedure Calls (RPC)

A protocol that allows a program running on one device to call a subroutine or function (a procedure) on another device, as if the function was a local procedure.
In other words, RPC enables IPC between processes running on different machines over a network

- RPC abstracts procedure calls between processes on networked systems
	- Uses ports for service differentiation
- _Stubs_ - client-side proxy for the actual procedure on the server
- The _client-side stub_ locates the server and _marshalls_ the parameters
- The _server-side stub_ receives this message, unpacks the marshalled parameters, and performs the procedure on the server

_**Marshalling**_ is a specific form of serialization focused on _preparing data for network communication_

![[Pasted image 20230728225353.png]]

- Data representation handled via _External Data Representation (XDR)_ format to account for _different architectures_
	- Platform Independence
	- Data Type Representation
	- Language Independence
	- Compactness and Efficiency
	- Endianness handling
 - Messages can be delivered _exactly once_ rather than _at most once_
 - OS typically provides a rendezvous (or _matchmaker_) service to connect client and server

_**The External Data Representation (XDR)**_ defines a _standard representation for data in the network_ to support heterogeneous network computing

![[Pasted image 20230728231937.png|Execution of RPC]]

## kw

- rendezvous
- marshalling
