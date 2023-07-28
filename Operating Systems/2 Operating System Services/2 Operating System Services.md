# Operating System Services

- User interface
- Program execution
- I/O operations
- File-system manipulation
- Communications
- Error detection
- Resource allocation
- Logging
- Protection and security

![[Pasted image 20230719170703.png]]

# System Calls

Programming interface to the services provided by the OS

- Typically written in a high-level language (C or C++)
- Mostly accessed by programs via a high-level API rather than direct system call use
	- Win32 API
	- POSIX
	- Java API

The caller need know nothing about how the system call is implemented

- Just needs to obey API and understand what OS will do as a result call
- Most details of OS interface hidden from programmer by API

## System Calls Example

- Copy
	![[Pasted image 20230719171145.png]]

## API - System Call - OS Relationship

![[Pasted image 20230719171747.png]]

## System Call Parameter Passing

- Simplest: pass the parameters in registers
	- In some cases, may be more parameters than registers
- Parameters stored in a block, or table, in memory, and address of block passed as a parameter in a register
	- This approach taken by Linux and Solaris
- Parameters placed, or **pushed**, onto the **stack** by the program and **popped** off the stack by the operating system

![[Pasted image 20230719172709.png]]

## Types of System Calls

- Process control
	- create process, terminate process
	- end, abort
	- load, execute
	- get process attributes, set process attributes
	- wait for time
	- wait event, signal event
	- allocate and free memory
	- dump memory if error
	- debugger
	- locks (managing access to shared data between processes)
- File management
	- create file, delete file
	- open, close
	- read, write, reposition
	- get and set file attributes
- Device management
	- request and release device
	- read, write, reposition
	- get and set device attributes
	- logically attach or detach devices
- Information maintenance
	- time and date
	- system data
	- process, file or device attributes
- Communications
	- communication connection
	- send, receive messages
	- shared-memory model
	- transfer status information
	- attach and detach remote devices
- Protection
	- access to resources
	- permissions
	- allow and deny user accesses

| Types of System Calls   | Windows                                                                       | Linux                                        |
| ----------------------- | ----------------------------------------------------------------------------- | -------------------------------------------- |
| Process Control         | CreateProcess()  <br>ExitProcess()  <br>WaitForSingleObject()                 | fork()  <br>exit()  <br>wait()               |
| File Management         | CreateFile()  <br>ReadFile()  <br>WriteFile()  <br>CloseHandle()              | open()  <br>read()  <br>write()  <br>close() |
| Device Management       | SetConsoleMode()  <br>ReadConsole()  <br>WriteConsole()                       | ioctl()  <br>read()  <br>write()             |
| Information Maintenance | GetCurrentProcessID()  <br>SetTimer()  <br>Sleep()                            | getpid()  <br>alarm()  <br>sleep()           |
| Communication           | CreatePipe()  <br>CreateFileMapping()  <br>MapViewOfFile()                    | pipe()  <br>shmget()  <br>mmap()             |
| Protection              | SetFileSecurity() InitializeSecurityDescriptor() SetSecurityDescriptorGroup() | chmod() umask() chown()                      |

# System Services

- File manipulation
	- Text editors to create and modify files
	- Special commands to search
- Status information sometimes stored in a file
	- Some ask the system for info - date, time, amount of available memory, disk space, number of users
	- Others provide detailed performance, logging, and debugging information
	- Typically, these programs format and print the output to the terminal or other output devices
	- Some systems implement a registry - used to store and retrieve configuration information
- Programming language support
	- Compilers, assemblers, debuggers and interpreters sometimes provided
- Program loading and execution
	- Absolute loaders, relocatable loaders, linkage editors, and overlay-loaders, debugging systems for higher-level and machine language
- Communications
	- Provide the mechanism for creating virtual connections among processes, users, and computer systems
- Background services
	- services, subsystems, daemons
- Application programs

# Linkers and Loaders

Source code compiled into object files designed to be loaded into any physical memory location – relocatable object file

![[Pasted image 20230719175040.png]]

**Linker** combines object file into **single binary executable** file (with libs)
**Loader** loads executable files into memory

- **Relocation** assigns final addresses to program parts and adjusts code and data in program to match those addresses

# Why Applications are Operating System Specific

App compiled on one system usually not executable on other OS.
Each OS provides its own **unique system calls**

## Application Binary Interface (ABI)

An interface between two binary program modules. Often, one of these modules is a library or operating system facility,

# Design and Implementation

- User goals–operating system should be convenient to use, easy to learn, reliable, safe, and fast
- System goals–operating system should be easy to design, implement, and maintain, as well as flexible, reliable, error-free, and efficient

# Policy and Mechanism

- Policy: What needs to be done?
- Mechanism: How to do something?

# Operating System Structure

General purpose is a very large program

## Monolithic Structure

- Separated in two parts
	- System
	- Kernel

Traditional UNIX System Structure

 ![[Pasted image 20230720063120.png]]
Linux System Structure

![[Pasted image 20230720063211.png]]

## Microkernel *

Move as much from kernel to the user space

- Easier to port
- Less error ที่เรากู้คืนไม่ได้

![[Pasted image 20230720063622.png]]

## Hybrid

# System Boot

- Small pieces of code - bootstrap loader, BIOS, stored in ROM or EEPROM locates the kernel, loads it into memory, and start it
- Sometimes two-step process where boot block at fixed location loaded by ROM coded, which loads bootstrap loader from disk
- Modern systems use UEFI instead of BIOS

# OS Debugging

- Core dump
	from application
- Crash dump
	from OS

## Performance Tuning

 - Trace listing
 - Profiling

## Tracing (follow)

Collects data for a specific event, such as steps involved in a system call invocation
