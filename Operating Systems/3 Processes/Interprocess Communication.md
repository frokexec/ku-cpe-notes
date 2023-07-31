# Interprocess Communication

[[Processes]] can be **independent** or **cooperating**

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