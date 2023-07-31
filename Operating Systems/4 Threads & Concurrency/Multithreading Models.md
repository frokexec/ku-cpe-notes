# Multithreading Models

## Many-to-One

- Many user-level threads mapped to single kernel thread
- One thread blocking causes all to block
	- the entire process will block if a thread makes a blocking system call
- Few systems currently use this model

![[Pasted image 20230729195009.png]]

## One-to-one

- Each user-level thread maps to kernel thread
- Creating a user-level thread creates a kernel thread
- More concurrency than many-to-one
- Number of threads per process sometimes restricted due to overhead

![[Pasted image 20230729195038.png]]

## Many-to-Many

- Allows many user level threads to be mapped to many kernel threads
- Allows the OS to create a sufficient number of kernel threads

![[Pasted image 20230729195048.png]]

## Two-level

- Similar to M:M, except that it allows a user thread to be bound to kernel thread
- Associates multiple ULTs with a smaller number of KLTs
