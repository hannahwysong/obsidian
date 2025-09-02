Class: [[OS Internals and Design]]
Date: 08-27-2025
Topics: #OS #ARM #assembly #hardware #CPU #i356Processor 

prev notes - [[OS Introduction]]

Defining Requirements 
- Before we can implement an OS, we must identify what requirements there are 
	- What hardware should it run on 
	- does it need to be RTOS multiprocessor, etc
- User Goals: 
	- convenient to use 
	- easy to learn 
	- reliable and safe 
- System Goals: think about having to write code
	- easy to design implement maintain and operate 
	- flexible, reliable, and efficient 
	- error free 
- Separation of Mechanisms and Policies 
	- mechanisms determine how to do something
	- policies determine what will be done 
		- changing one will not inherently effect the other
	- Scheduling CPU Access: 
		- Mechanism: the CPU scheduler itself that switches processes in and out of the CPU 
		- Policy: the scheduling algorithm which determines which process runs next
	- The CPU scheduler should be able to operate without any scheduling algorithm 
- Hardware Requirements 
	- OS were originally written in Assembly, which is unique to CPU 
	- Assembly either works on x86 or ARM not both
	- Now most OS are written in C 
	- C can work on x86, ARM, RISC-V, MIPS, etc.
- Using a High Level Language: allows you to 
	- write code faster
	-  code is compact 
	- code is easier to understand and debug
	- easier to port to numerous architectures 
- Requirements of the OS 
	- OS is a resource manager 
		- allocates time for programs to run
		- allocates memory for programs to use 
		- allocates usage of devices for programs