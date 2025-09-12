Class: [[OS Internals and Design]]
Date: 09-12-2025
Topics: 

- many to one reduces computer overhead because the program can generate as many user threads for one kernel thread. 
One to One 
- every user thread is mapped to exactly one kernel thread
- direct association with a kernel level thread managed by an OS 
	- modern OS use this because the hardware can handle the overhead
- cpu core is mapped to a kernel thread which is mapped to a user model 
- applications are required to limit maximum user threads to the number of cores on the system
- user programs are less complex
Many-to-Many
- OS determines how many kernel threads to assign 
- if a user thread blocks, the other threads can continue to execute on separate kernel threads
- not commonly used due to its complexity 
Issues with threading
- Our processes don’t really know what is happening with the actual CPU cores
Process v Thread scheduling 
- multithreaded OS, threads are typically the main schedulable entity
- each thread can generally be thought of as its own process

CPU Scheduling 
- only one process is running on the CPU core at at a time
- all processes reside in a state queue 
Long Term Scheduling 
- how many procceses the OS will allow to exist 
- limited by memory
Short Term Scheduling
- OS selects a "ready" process from a queue 
- lives in the kernel and can make a decision when:
	- a process switches from running to waiting
		- i.e. access i/o
	- an interrupt occurs
		- waiting for keyboard data
	- processes is created or terminated
- non-preemptive scheduling method must wait for an event to occur before switching 
- preemptive allows a scheduler to interrupt a process
- a good scheduling algorithm utuilizes the CPU and I/O storage. IT also considers how 