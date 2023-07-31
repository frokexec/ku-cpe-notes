# Computer System Architecture

## Single-Processor Systems

## Multiprocessors Systems

- Increased throughput
- Economy of scale
- Increased reliability
	- Asymmetric Multiprocessing - each processor is assigned a specie task.
	- Symmetric Multiprocessing - each processor performs all tasks.![[Pasted image 20230719162140.png]]
- Multi-chip and multi-core
	![[Pasted image 20230719162349.png|A dual-core design]]

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
