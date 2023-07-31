# Operating System Examples

## Windows Threads

Windows API–primary API for Windows applications

- Implements the one-to-one mapping, kernel-level
- Each thread contains
	- A thread id
	- Register set representing state of processor
	- Separate user and kernel stacks for when thread runs in user mode or kernel mode
	- Private data storage area used by run-time libraries and dynamic link libraries (DLLs)
- The register set, stacks, and private storage area are known as the context of the thread
- The primary data structures of a thread include:
	- ETHREAD (executive thread block)–includes pointer to process to which thread belongs and to KTHREAD, in kernel space
	- KTHREAD (kernel thread block)–scheduling and synchronization info, kernel-mode stack, pointer to TEB, in kernel space
	- TEB (thread environment block)–thread id, user-mode stack, thread-local storage, in user space

![[Pasted image 20230731154755.png]]

## Linux Threads

- Linux refers to them as *tasks* rather than threads
- Thread creation is done through `clone()` system call
- `clone()` allows a child task to share the address space of the parent task (process)
- Flags control behavior
- struct `task_struct` points to process data structures (shared or
unique)
