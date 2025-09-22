Class: [[OS Internals and Design]]
Date: 09-15-2025
Topics: 

First-in-first Out 
- The scheduler will execute processes in the order they are created/ arrive
	- not the ready queue 
- processes only release the CPU when they are terminated or waiting
- method is cooperative (processes must release CPU)
	- easy to implement 
	- i/o not prioritized and forced to wait
- some processes feel slow while others super fast
- turnaround time is the completion time minus the arrival time 
- waiting time is the turnaround time minus the burst time 

Round Robin (RR)
- scheduler processes evenly giving each process a fixed amount of time to run on the CPU 
	- quanta is how many of these slices of time (e.g. 100 clock cycles) a process may use 
- this method is preemptive ( uses a clock to force processes to stop )
- need to find quanta where context switching takes the least amount of time
	- if too large then processes spend forever waiting vs too short then it spends most time context switching
- waits until each program in list has ran for quanta then restarts list 

Shortest Process Next (SPN)
- scheduler schedules process with least amount of expected work (CPU) time to run until the process has an i/o request or terminates
- optimal waiting time 
- can be preemptive or cooperative
	- preemptive version uses shortest remaining time first and prioritizes i/o bound jobs over CPU bound jobs - shortest remaining time first
- long processes may never get a chance to run
- prediction cannot be sure how long a process needs to run 

Multilevel Feedback Queue (MLFQ) 
- scheduler schedules bast on past behavior of the processes to predict future priorities 
	- used in modern UNIX systems
	- overcomes the limitations of preemptive SPN
- can favor jobs that have least amount of CPU time
- adapts based on how processes run and changes scheduling behavior based on history
- kernel keeps track of how often a process waits for i/o and prioritizes the processes that often access i/o
- consists of multiple queues with priority based on predicted run time 
	- uses RR scheduling for each priority queue 
		- once finished run the next priority level queue with RR 
- increase RR quanta exponentially for each priority level 
	- gives CPU bound processes more time 
- new processes start in the highest priority queue 
- if processes wants to exceed its quanta decrease the processes priority level by one 
	- process is using more CPU time than expected 
- process does not exceed its quanta, increase priority level by one up to the highest priority level
	- process is using less CPU than expected 
	- can happen if process begins waiting for i/o quickly
- i/o bound jobs become higher priority 
- cpu bound jobs become lower priority 

Improving Fairness 
- SPN is optimal, but unfair and can starve long processes, increasing fairness must increase the waiting time 
Possible Solutions:
- each queue gets a fraction of CPU time 
	- only fair if priority level queues have the same number of processes 
- adjust the priority of processes if they are not getting ran
	- every process becomes high priority which causes system overload 
Lottery Scheduling 
- each process gets a set of tickets
	- more tickets to short running processes 
	- fewer tickets to longer running processes 
- each quantum, randomly pick a winning ticket
- CPU time is proportional to the number of tickets given to a process 