# I/O Structure

## Two methods for handling I/O

- Control return to user program **only upon I/O completion**
	- Wait instruction idles the CPU until the next interrupt
	- Wait loop
	- No simultaneous I/O processing
- Control return to user program **without waiting for I/O completion**
	- **[[System calls]]** - request to the OS to allow user to wait for I/O completion
	- **Device-status table** contains entry for each I/O device indicating its type, address, and state
