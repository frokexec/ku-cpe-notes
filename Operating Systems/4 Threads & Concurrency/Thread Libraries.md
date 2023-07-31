# Thread Libraries

- Thread library provides programmer with API for creating and managing threads
- Two primary ways of implementing
	- **User level Library** - entirely in user space (code and data structures)
		- invoking a function in the library results in a *local function call* in user space
	- **Kernel-level library** - supported by the OS
		- code and data structures exists in *kernel space*
		- invoking a function in the *API for the library* results in a *system call* to the kernel

## Main thread libraries

- **Pthreads**
	- May be provided either as user-level or kernel level
	- the library includes `pthreads.h` header file
	- *Specification* for thread behavior, not *implementation*
	- OS designer may implement the specification in any way
- **Win32 library**
	- kernel level library available on windows
	- include `windows.h` header file to create a thread
 - **Java threads**
	 - Managed by JVM
	 - Typically implemented using the threads model provided by underlying OS
	 - The java thread API allows threads to be created and managed directly as Java programs
