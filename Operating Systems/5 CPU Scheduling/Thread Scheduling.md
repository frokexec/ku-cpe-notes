# Thread Scheduling

- Distinction between user-level and kernel-level threads
- When threads supported, **threads scheduled, not processes**
- [[Multithreading Models#Many-to-One|Many-to-One]] and [[Multithreading Models#Many-to-Many|Many-to-Many]] models, thread library schedules user-level threads to run on LWP
	- Known as process-contention scope (PCS) since scheduling competition is within the process
	- Typically done via priority set by programmer
- Kernel thread scheduled onto available CPU is **system-contention scope (SCS)**–competition among all threads in system
