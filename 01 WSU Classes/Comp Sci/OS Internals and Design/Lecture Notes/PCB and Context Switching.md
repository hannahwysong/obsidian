Class: [[OS Internals and Design]]
Date: 09-08-2025
Topics: 

Creating a Process
 - want to execute different program other than creating child process
	 - use execve(), execvp(), execlp()
	- int execve(char \*prog, char \*\*argv, char \*\*envp)  
		 - prog - full path of program to run  
		 - argv - arguments the program should run with  
		 - envp - environment variables such as PATH, and HOME  
		 - Returns -1 if an error has occurred calling the program, i.e. program could not be found  
		 - The current process is now overtaken by the program we have specified  
	- int execvp(char \*prog, char \*\*argv)  
		- Search PATH for prog using the current environment  
	- int execlp(char \*prog, char \*argv, ...)  
		- List arguments one at a time, finishing with NULL
Terminate a Process
- forcefully terminate using exit(status) or kill(pid, SIGTERM)
	- void exit (int status)  
		- status - status code returned to waitpid  
		- Terminates the current process  
		- By convention, status of 0 is success, non-zero is error  
	- int kill(int pid, int sig)  
		- pid - the process id you want to terminate/kill  
		- sig - either SIGTERM (15) or SIGKILL (9)  
	- SIGTERM - safely terminate the process but allow the process to do some clean up before it is forced to terminate  
	- SIGKILL - immediately terminate the process and give no warning or time for  process to clean up
Process Control Block (PCB)
- tracks state of process 
	- contains process state, process number, program counter, registers, memory limits, list of open files, and other details 
Scheduling Processes 
- os must schedule individual processes 
	- if there are multiple cores parallel processes can run simultaneously
- OS looks at list of PCBs finds the ready ones and decides which to run 
- can decide this order by:
	- FIFO
	- round robin
	- priority 
Preemptive Multitasking 
- process can be paused for a short time where something else is allowed to run 
- the OS can remove a programs access to the CPU without asking permission 
	- aka involuntarily kicked off the CPU 
- process may preempt itself
	- makes a system call, waits to read disk, makes another runnable process 
- if process A is stuck waiting for our keyboard while process B is running, and we finally press a key, preempt process B and let the process A get a chance to capture the keyboard input
	- known as context switching 
Cooperative Multitasking 
- process willingly gives up control of CPU for another process 
- machine can be locked up by a program that is stuck 
	- much easier to implement because it does not have interrupts 
Context Switch
- switching between running processes 
- Process P 0 is currently executing but we want to run P 1  
		1. Save P 0’s PCB data  
		2. Reload P 1’s PCB data  
		3. Run P 1
- steps are the same for switching back to P 0
- costs CPU time and memory to store and access PCB data 
- very hardware dependent 
- must be tailored to a  certain instruction set architecture 