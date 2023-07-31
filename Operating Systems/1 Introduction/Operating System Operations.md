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

## System Call

A [system call](https://www.geeksforgeeks.org/introduction-of-system-call/) is a procedure that provides the interface between a process and the operating system. It is the way by which a computer program requests a service from the kernel of the operating system.

## Examples

| Types of System Calls   | Windows                                                          | Linux                                        |
| ----------------------- | ---------------------------------------------------------------- | -------------------------------------------- |
| Process Control         | CreateProcess()  <br>ExitProcess()  <br>WaitForSingleObject()    | fork()  <br>exit()  <br>wait()               |
| File Management         | CreateFile()  <br>ReadFile()  <br>WriteFile()  <br>CloseHandle() | open()  <br>read()  <br>write()  <br>close() |
| Device Management       | SetConsoleMode()  <br>ReadConsole()  <br>WriteConsole()          | ioctl()  <br>read()  <br>write()             |
| Information Maintenance | GetCurrentProcessID()  <br>SetTimer()  <br>Sleep()               | getpid()  <br>alarm()  <br>sleep()           |
| Communication           | CreatePipe()  <br>CreateFileMapping()  <br>MapViewOfFile()       | pipe()  <br>shmget()  <br>mmap()             |
