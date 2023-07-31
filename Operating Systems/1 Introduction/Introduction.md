# Introduction

#index

## What is an Operating System

Intermediary between a user of a computer and the computer hardware

### OS goals

- Execute user programs and make solving user problem easier
- Make the computer system convenient to use
- Use the computer hardware in an efficient manner

## Computer System Structure

### Components

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

## Abstract View of Components of Computer

![[Pasted image 20230716195550.png]]

## What Operating Systems Do

It manages all of the software and hardware on the computer. It performs basic tasks such as file, memory and process management, handling I/O and controlling peripheral devices.

### Defining Operating Systems

Present in toasters through ships, spacecraft, game machines, TVs and industrial control systems.
Born when fixed use computers for military become more general purpose and needed resource management and program control.

### Operating System Definition

- **No universally accepted definition**.
- "The one program running at all times on the computer" is the **kernel**
- Everything else is either
	- A system program
	- An application program (not associated with the OS)

## Computer System Organization

- Computer-system operation
	- One or more CPUs, device controllers connect through common **bus** providing access to shared memory
	- Concurrent executing of CPUs and devices competing for memory cycles
	![[Pasted image 20230716202739.png]]

### Computer System Operation

- I/O devices and the CPU can **execute concurrently**
- Each device controller is in charge of a particular device type
- Each device controller has a local buffer
- Each device controller type has an OS **device driver** to manage it
- CPU moves data from/to main memory to/from local buffers
- I/O is from the device to local buffer of controller
- Device controller informs CPU that it has finished its operation by causing an **[[interrupt]]**

## Links

- _[[Interrupt]]
- [[IO Structure]]
- [[Storage Structure]]
- [[Direct Memory Access Structure]]
- [[Operating System Operations]]
- [[Multiprogramming & Multitasking]]
- [[Dual mode operation]]
- [[Timer]]
- [[Resource Management]]
- [[IO Subsystem]]
- [[Protection and Security]]
- [[Virtualization]]
- [[Distributed Systems]]
- [[Computer System Architecture]]
- [[Computing Environments]]
- [[Free and Open-Source Operating Systems]]

## Practice Exercises

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

## Continue

[[Operating System Services]]
