Class: [[OS Internals and Design]]
Date: 09-10-2025
Topics: 

Implementing Multiprocessing in C 
- OS switches between multiple processes and execute each individually 
	- preemptive - hard to implement but better solution
	- cooperative - easy to implement but worse solution 
To implement cooperative multitasking: 
- write set of tasks that we want to execute
- write a scheduler that can schedule tasks from a maintained list of PCBs
- pass the task to a scheduler that maintains PCBs for each task passed to it in order
- write a yield() function to save state of current task in PCB and resume the state or start the next task 

Threads 
- a thread is a schedulable execution context
	- all the information a CPU needs to execute a stream of instructions 
- a process may have more than 1 thread
- multithreaded processes share the same address space 
	- shares code data and any open files but has its own registers and stack
- can be executed simultaneously by using CPU cores
	- core is the CPU hardware 
	- a thread instructions/ data provided to the core 
- most modern OS schedule threads not processes 
	- threads live inside process 
Thread Abstraction
- kernal has its own thread internally for every user mode thread or process 
- threads don't have to rely on processes and vice versa 
- concurrency is executing multiple computations at the same time 
	- this requires multiple physical CPU cores 
- threads allow a process to do many things simultaneously 
- creating a new process has much more overhead than using a thread
	- OS or user processes can create as much threads as they want and are not bound by how many physical cores exist 
	- A process can create as many threads as it wants but there can only be as many processes as cores exist
- A multiprocess OS can run or switch between multiple processes 
- A multithreaded OS can allow processes to use multiple threads 
	- only if there are available CPU cores to use 

Portable Operating System Interface 
- portable operating system interface (POSIX) is a set of standards used to maintain compatibility between OSs
- standards allow for OSs to use standardized methods for threads, I/O, file operations, and other OS functions 
	- defines both the kernel and user-level application programming interfaces (APIs), along with command line shells and utility interfaces 
Threads in POSIX
- int pthread_create(pthread_t \*thr, pthread_attr_t \*attr, void \*(\*fn)(void \*), void \*arg);  
	- Create a new thread thr, with attributes attr, to run a function fn, using arguments  
- arg  
	- If the syntax for fn looks confusing, just know it is a pointer to a function, that accepts a pointer as its arguments, and a pointer as its return value, each are void to allow the developer flexibility to choose any type they want to return or pass as arguments  
- void pthread_exit(void \*return_value);  
	- Exit or terminate the current thread and return a value return_value  
- int pthread_join(pthread_t thread, void \*\*return_value);  
	- Wait for thread thread, to exit, and capture its return value return_value  
- void pthread_yield();  
	- Tell the OS to allow other threads to execute and pause this thread  
	- Helpful when this thread needs to wait for something (like I/O)  
Implementing POSIX Compliant Threads 
- kernel can implement thread creating using a system call and maintain user threads with kernel threads
	- every process that wants a thread must use this system call
	- OS has final say whether or not its created. Has control of access to threads 
- most modern OS are not POSIX compliant 
- creates process abstraction in kernel 
Thread Types 
- two levels of threads: kernel and user threads 
	- kernel: managed and scheduled with the kernel with direct access to CPU 
	- user: managed and scheduled with the user program so multiple parts of the user program can execute simultaneously 
Contention Scope 
- level at which contention for resources occurs between threads 
	- can be in user or kernel space
- Two methods for scheduling threads: Process-Content Scope (PCS) and System-Contention Scope (SCS)
- in PCS threads within the process compete with each other 
- scheduling mechanism is local to the process 
	- thread library has control over which thread will be scheduled 
- in SCS threads within the kernel compete with each other
- scheduling mechanism is within the OS, which determines which threads get to execute on CPU 
- most modern OS only allow for SCS scheduling and the one-to-one thread model 
Many-To-One Thread Model
- each user-level thread is mapped to a single kernel thread per process
	- OS handles multiple threads as a single task
- implemented using a user level library rather than system call
- if one thread blocks the entire kernel thread will become blocked
	- prevents the other threads from executing 
- not true parallelism, the single kernel thread can only execute the user threads on 1 CPU core
	- only one kernel thread can be mapped to a program
- user level threads are required to allocate a new stack and maintain a queue of runnable threads 
- a scheduler running in user space selects the next runnable thread from queue and gives it to the kernel thread to execute 
- Many things can cause a thread to get blocked
	- OS must provide non-blocking versions of system calls so the thread can yield temporarily