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
