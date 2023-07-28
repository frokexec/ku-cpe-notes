---
date created: 2023-07-16 19:55
date updated: 2023-07-19 16:34
---

# What is an Operating System

Intermediary between a user of a computer and the computer hardware

## OS goals

- Execute user programs and make solving user problem easier
- Make the computer system convenient to use
- Use the computer hardware in an efficient manner

# Computer System Structure

## Components

- Hardware
  - CPU
  - Memory
  - I/O devices
- Operating system
  - Controls and coordinates use of hardware among various applications and users
- Application programs
- Users
  - People
  - Machines
  - Other computers

# Abstract View of Components of Computer

![[Pasted image 20230716195550.png]]

# What Operating Systems Do

It manages all of the software and hardware on the computer. It performs basic tasks such as file, memory and process management, handling I/O and controlling peripheral devices.

# Defining Operating Systems

Present in toasters through ships, spacecraft, game machines, TVs and industrial control systems.
Born when fixed use computers for military become more general purpose and needed resource management and program control.

# Operating System Definition

- **No universally accepted definition**.
- "The one program running at all times on the computer" is the **kernel**
- Everything else is either
  - A system program
  - An application program (not associated with the OS)

# Computer System Organization

- Computer-system operation
  - One or more CPUs, device controllers connect through common **bus** providing access to shared memory
  - Concurrent executing of CPUs and devices competing for memory cycles
  ![[Pasted image 20230716202739.png]]

# Computer System Operation

- I/O devices and the CPU can **execute concurrently**
- Each device controller is in charge of a particular device type
- Each device controller has a local buffer
- Each device controller type has an OS **device driver** to manage it
- CPU moves data from/to main memory to/from local buffers
- I/O is from the device to local buffer of controller
- Device controller informs CPU that it has finished its operation by causing an **interrupt**

# Interrupt

An interrupt is a signal emitted by hardware or software when a process or an event needs immediate attention.

## Common Functions of Interrupts

- Through the **interrupt vector**, which contains the addresses of all service routines.
- Interrupt architecture muse save the address of the interrupted instruction
- A trap or exception is a software-generated interrupt caused either by an error or a user request
- An OS is interrupt driven

## Interrupt vector

Table of pointers in memory contains the addresses of interrupt service routines (ISR) or interrupt handler at a fixed location for a given CPU.

## Interrupt Service Routine

An interrupt service routine (ISR) is a software routine that hardware invokes in response to an interrupt. ISR examines an interrupt, determines how to handle it, executes it, and returns a logical interrupt value.

## Examples (from ChatGPT)

1. User presses a key on the keyboard.
2. The keyboard hardware sends an electrical signal to the computer's CPU to indicate that a key has been pressed.
3. The CPU receives the interrupt signal and temporarily suspends the currently executing process.
4. The CPU transfers control to the interrupt handler routine specific to keyboard interrupts.
5. The interrupt handler reads the key code from the keyboard controller, processes it, and stores it in a buffer (main memory).
6. If there is a process waiting for keyboard input, the interrupt handler wakes up that process and provides it with the input data.
7. The interrupt handler updates the state of the system, such as updating the display or triggering specific actions based on the key pressed.
8. Once the interrupt handler completes its task, it returns control to the interrupted process.
9. The interrupted process resumes execution from where it was paused, continuing its normal operation.

## Interrupt Timeline

![[Pasted image 20230716205259.png]]

1. I/O device sends an interrupt signal (IRQ | Interrupt Request) to CPU
2. If CPU is in EI (Enable Interrupt) state, it will response to the IRQ and send back Interrupt Acknowledge to the device
3. The CPU will set its state to DI (Disable Interrupt)
4. It will stop processing the running program
5. The device sends **Interrupt Vector** to CPU
6. Move the data from PC registers and common registers to stack
7. Process the subprogram to serve the device that send the IRQ
8. Move the data form stack back to PC registers and registers
9. Set the CPU state back to EI (Enable Interrupt)
10. Continue to process the running program

## Interrupt types

Interrupts can be split into categories depending on what triggered them:

- exceptions - triggered by the CPU itself
- IRQs - triggered by external hardware (e.g. network card)
- software interrupts - triggered explicitly by the code that was running
- IPIs (inter-processor interrupts) - triggered by a different CPU

Exceptions can be further broken down into sub-categories:

- aborts - things that prevent the interrupted code from continuing. These are things that indicate a major problem - e.g. division by zero, hardware failures, etc.
- traps - things that don't prevent the interrupted code from continuing. These can be used for debugging, for virtual memory management, etc.

## Interrupt-drive I/O Cycle

![[Pasted image 20230716205745.png]]

# I/O Structure

## Two methods for handling I/O

- Control return to user program **only upon I/O completion**
  - Wait instruction idles the CPU until the next interrupt
  - Wait loop
  - No simultaneous I/O processing
- Control return to user program **without waiting for I/O completion**
  - **System call** - request to the OS to allow user to wait for I/O completion
  - **Device-status table** contains entry for each I/O device indicating its type, address, and state

# Storage Structure

## Main memory

- Random access
- Typically volatile (easily evaporated)
- Typically DRAM

## Secondary Storage

- Nonvolatile
- HDD
- NVM

## Definitions and Notation

- Kilobyte - 1024 bytes
- Megabyte - 1024^2 bytes
- Gigabyte - 1024^3 bytes
- Terabyte - 1024^4 bytes
- Petabyte - 1024^5 bytes

# Storage Device Hierarchy

![[Pasted image 20230716215604.png]]

# Direct Memory Access Structure

![[Pasted image 20230719152855.png]]

- Used for high-speed I/O devices able to transmit information at close to memory speeds
- Transfers blocks of data from buffer storage directly to main memory **without CPU intervention**
- Only one interrupt is generated per block, rather than the one interrupt per byte

## DMA Example

if a computer wants to send data from system memory to a printer, it issues a DMA transfer request to the printer's DMA controller

# Operating System Operations

- Bootstrap program (load the kernel)
- Kernel loads
- Starts **system daemons**
- Kernel **interrupt driven** (hardware and software)
  - Hardware interrupt by one of the devices
  - Software interrupt (**exception** or **trap**):
    - Software error
    - Request for OS service - **system call**
    - Other process problems
      - infinite loop
      - processes modifying each other or the OS

# System Call

A [system call](https://www.geeksforgeeks.org/introduction-of-system-call/) is a procedure that provides the interface between a process and the operating system. It is the way by which a computer program requests a service from the kernel of the operating system.

## Examples

| Types of System Calls   | Windows                                                          | Linux                                        |
| ----------------------- | ---------------------------------------------------------------- | -------------------------------------------- |
| Process Control         | CreateProcess()  <br>ExitProcess()  <br>WaitForSingleObject()    | fork()  <br>exit()  <br>wait()               |
| File Management         | CreateFile()  <br>ReadFile()  <br>WriteFile()  <br>CloseHandle() | open()  <br>read()  <br>write()  <br>close() |
| Device Management       | SetConsoleMode()  <br>ReadConsole()  <br>WriteConsole()          | ioctl()  <br>read()  <br>write()             |
| Information Maintenance | GetCurrentProcessID()  <br>SetTimer()  <br>Sleep()               | getpid()  <br>alarm()  <br>sleep()           |
| Communication           | CreatePipe()  <br>CreateFileMapping()  <br>MapViewOfFile()       | pipe()  <br>shmget()  <br>mmap()             |

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

# Dual mode operation

Dual-mode operation allows OS to protect itself and other
system components
• User mode and kernel mode

Some instructions designated as privileged, only executable in kernel mode

![[Pasted image 20230718233509.png]]

# Timer

Timer to prevent infinite loop (or process hogging resources)

- It is set to interrupt the computer after some time period
- OS set the counter (privileged instruction)

# Resource Management

## Process Management

A process is a program in execution. It is a unit of work within the system.
Program is a **passive entity**; Process is an **active entity**.

| Program                                                                      | Process                                                                                       |
| ---------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| Program contains a set of instructions designed to complete a specific task. | Process is an instance of an executing program.                                               |
| Program is a passive entity as it resides in the secondary memory.           | Process is a active entity as it is created during execution and loaded into the main memory. |

- Single-threaded process: one PC specifying location of next instruction to execute
- Multi-threaded process: one PC per thread

### Process Management Activities

The OS is responsible for the following activities in connection with process management:

- Creating and deleting both user and system processes
- Suspending and resuming processes
- Providing mechanisms for process synchronization
- Providing mechanisms for process communication
- Providing mechanisms for deadlock handling

## Memory Management

- All (or part) of the instructions must be in memory
- All (or part) of the data that is needed by the program must be in memory

### Memory Management Activities

- Keeping track of which parts of memory are currently being used and by whom
- Deciding which processes and data to move into and out of memory
- Allocating and de-allocating memory space as needed

## File-system Management

### File-system Management Activities

- Creating and deleting files and directories
- Primitives to manipulate files and directories
- Mapping files onto secondary storage
- Backup files onto stable (non-volatile) storage media

## Mass-Storage Management

- Mounting and un-mounting
- Free-space management
- Storage allocation
- Disk scheduling
- Partitioning
- Protection

## Caching

- Cache smaller than storage being cached
  - Cache management important design problem
  - Cache size and replacement policy

## Characteristics of Various Types of Storage

![[Pasted image 20230719153506.png]]

## Migration of data "A" from Disk to Register

![[Pasted image 20230719153816.png]]

- Multitasking environments must be careful to use most recent value, no matter where it is stored in the storage hierarchy

- Multiprocessor environment must provide **cache coherency** (shared memory hierarchy) in hardware such that all CPUs have the most recent value in their cache

# I/O Subsystem

aka I/O system, is a critical component of OS responsible for managing communication between CPU and external devices .

## I/O Subsystem components

- Device drivers
- I/O manager
- Buffering
- Caching
- Interrupt Handing
- Error Handling

# Protection and Security

**It is a concept**

## Protection

Any mechanism for controlling access of processes or users to resources defined by the OS

- Access control
- Memory protection
- File permissions
- Hardware Protection

## Security

Defense of the system against internal or external attacks

- DoS
- worms
- viruses
- ID theft
- Theft of service

# Virtualization

Virtual environment

![[Pasted image 20230719161406.png]]

# Distributed Systems

A distributed system is a computing environment in which various components **are spread across multiple computers** (or other computing devices) **on a network**.

## Network Operating System

It is a specialized type of operating system designed to manage and control network resources and provide services to clients and users in a networked environment.

![[Pasted image 20230719161734.png]]

# Computer System Architecture

## Single-Processor Systems

## Multiprocessors Systems

- Increased throughput
- Economy of scale
- Increased reliability
  - Asymmetric Multiprocessing - each processor is assigned a specie task.
  - Symmetric Multiprocessing - each processor performs all tasks.
    - ![[Pasted image 20230719162140.png]]

### Dual-Core

- Multi-chip and multi-core
  ![[Pasted image 20230719162349.png]]
  
## Multiprocessors Keywords
- NUMA

## Clustered Systems

A clustered system is a group of interconnected computers or servers that work together as a single system to enhance performance, availability, and fault tolerance.

Like multiprocessor systems, but multiple systems working together

- Usually sharing storage via a **storage-area network (SAN)**
- Provides a **high-availability** service which survives failures
  - **Asymmetric clustering** - has one machine in hot-standby mode while other is running the applications
    - hot-standby host machine does nothing but monitor the active server
  - **Symmetric clustering** - has multiple nodes running applications, monitoring each other
- Some clusters are for HPC (applications must be written to use parallelization)
- Some have distributed lock manager to avoid conflicting operations

![[Pasted image 20230719163429.png]]


# Computing Environments

## Traditional Computing

## Mobile Computing

## Client-Server Computing

![[Pasted image 20230719164122.png]]

- Discord

## Peer-to-Peer Computing

![[Pasted image 20230719164411.png]]
 
- Decentralized
- Skype

## Cloud Computing

- Public cloud
- Private cloud
- Hybrid cloud
- SaaS
	- Word processor
- PaaS
	- Database
- IaaS
	- VM

![[Pasted image 20230719164600.png]]

## Real-Time Embedded Systems

![[Pasted image 20230719165102.png]]

# Free and Open-Source Operating Systems


# Practice Exercises
1. What are the three main purposes of an operating system?
2. We have stressed the need for an operating system to make efficient use of the computing hardware. 
3. When is it appropriate for the operating system to forsake this principle and to “waste” resources? Why is such a system not really wasteful?
4. What is the main difficulty that a programmer must overcome in writing an operating system for a real-time environment?
5. Keeping in mind the various definitions of operating system, consider whether the operating system should include applications such as web browsers and mail programs. Argue both that it should and that it should not, and support your answers.
6. How does the distinction between kernel mode and user mode function as a rudimentary form of protection (security)?
7. Which of the following instructions should be privileged?
	a. Set value of timer.
	b. Read the clock.
	c. Clear memory.
	d. Issue a trap instruction.
	e. Turn off interrupts.
	f. Modify entries in device-status table.
	g. Switch from user to kernel mode.
	h. Access I/O device.
8. Some early computers protected the operating system by placing it in a memory partition that could not be modified by either the user job or the operating system itself. Describe two difficulties that you think could arise with such a scheme.
9. Some CPUs provide for more than two modes of operation. What are two possible uses of these multiple modes? Timers could be used to compute the current time. Provide a short description of how this could be accomplished.
10. Give two reasons why caches are useful. What problems do they solve? What problems do they cause? If a cache can be made as large as the device for which it is caching (for instance, a cache as large as a disk), why not make it that large and eliminate the device?
11. Distinguish between the client–server and peer-to-peer models of distributed systems.