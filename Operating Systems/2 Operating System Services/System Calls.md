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
