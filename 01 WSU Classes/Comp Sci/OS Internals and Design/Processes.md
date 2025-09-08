Class: [[OS Internals and Design]]
Date: 09-05-2025
Topics: 

Process Abstraction 
- OS provides abstractions for our programs
	- breaks complex problems into manageable parts 
	- basically a simplified interface.
- OS provides a process abstraction for programs to get access to CPU time, memory, or other resources 
- A process (aka job or task) is an instance of a program
- ensures the data inside the process is unique to the process itself
	- processes are kept separate to prevent data mix ups
- Certain programs have to wait for a response, the CPU can be utilized other places
- old computers could only run one process after the other 
Context Switching
- switching between processes 
- longer than running one after the other, but over all more efficient
Parallelism 
- simultaneous execution of multiple tasks 
- parallelism is performed by multi core CPUS
	- 4 cores can run 4 processes at a time 
- process has access its own unique address space for code and data, opened files, and a "virtual" CPU 
- one process is isolated from another in memory
- to keep track of multiple processes information the OS uses a Process Control Block (PCB).
Inter-Process Communication 
- processes can communicate with each other 
	- share files and memory
	- can pass messages 
Process State 
- New 
	- wants to run 
	- OS admits the process to the pool of other processes that want to run
- Ready 
	- process is now ready but must be dispatched by OS
- Running 
	- process is executing on the CPU but it can be interrupted or forced to wait for I/O
- Waiting 
	- process cannot run because its waiting for something to happen
- Terminated
	- process was finished or was forcefully terminated 
- linux provides function fork() in c to create a new process 
- int fork(void);
	- creates a proccess that is an exact copy of the current one that starts immediately after the fork function call
	- returns process ID of new process to "parent"
	- returns 0 to child 
	- returns negative if error 
- program can also wait for your child processes to finish before contuining with the waitpid() function
- int waitpid(int pid, int stat, int op)
	- pid - process ID to wait for, -1 for any
	- stat - contains exit value of finished process
	- opt - custom options
- returns process ID or -1 on error 