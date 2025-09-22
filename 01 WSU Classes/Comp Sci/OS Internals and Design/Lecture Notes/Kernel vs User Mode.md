Class: [[OS Internals and Design]]
Date: 08-27-2025
Topics: #OS #kernal #assembly #user-mode #OS-structure #I/O #runtime-stack

#### Design Principles
Kernels 
- protected part of the OS that runs in kernel mode 
	- opposed to user run programs 
- protects OS data structures and device registers 
Structuring an OS 
- layers exist to perform certain functionality
- modifying one layer does not modify another 
- lower levels have high privileges for accessing hardware 
	- layer 1: hardware
	- layer 2: scheduling 
	- layer 3: memory management 
	- layer 4: process management
	- layer 5: I/O Buffer
	- layer 6: User programs 
Monolithic OS Structure 
- entire OS is working in kernel space
Microkernel OS Structure 
- basic functionality in the core of the software system 
- has minimum amount of features to implement an OS 
	- hardware interfaces 
	- task scheduling 
- file system, device drivers, and user programs are all ran in user mode
OS Protections 
- protects memory 
- protects I/O 
- protects CPU 
- protects user programs from each other
- protects OS from user programs 
Kernel Mode 
- has most privileges for accessing memory, I/O, interrupts, special instructions, and halting the CPU 
- operating system has complete control over the hardware 
User Mode 
- least amount of privileges to prevent programs from using hardware 
Kernel vs User Mode 
- switches between nodes should be through system calls 
	- System call: mechanism used by programs to request services from the OS 
Memory Protections
- os protects user programs from tampering with each other 
- os must protect user programs from tampering with it 
- OS uses a base memory addresses and a max memory address for a process to prevent tampering
I/O Access 
- Interrupt based I/O - sends an interrupt request when CPU needs it, handled immediately
- Memory Mapped I/O - accessed by reading and writing to a portion of regular address space
- Port Mapped I/O - uses a separate address (not memory) to identify port address and special instructions to read or write to the port
	- distinction between addressing space is made in the control bus 
Runtime Stack
- keeps track of all the variables and data in program
- Stack Pointer (ESP or SP for 32/16 bit) - top of stack
	- used to keep track of the top of the runtime stack
- Frame Pointer(EBP or BP for 32/16 bit) - bottom of current frame
	- used to keep track of the start of variables in current frame or function

#### Hardware and The OS 
The CPU 
- central processing unit executes instructions we provide to it
- has an specific instruction set architecture (ISA) the defines what instructions and how
ISA - Instruction Set Architecture 
- blueprint for the tools the CPU has 
- defines what registers, instructions, and systems 
	- x86, ARM, RISC-V, MIPS are examples
- code for one ISA cannot be ran on another without rewriting code 
- c program can be compiled for multiple ISA
RAM - Random Accessed Memory
- stores all programs and data
- without RAM, CPU wouldn't have instructions to execute 
- a program has to be loaded into RAM before ran 
Storage Device
- holds files and programs 
	- Hard Disk Drive (HDD), Solid State Drive (SSD), floppy disk
- our storage device is an I/O device 
- to execute a program or read a file it is copied from the memory into RAM 
Motherboard
- connects the CPU, RAM, and I/O devices together
- Components on the motherboard that assist in data transfer: 
	- Northbridge: interconnects CPU, RAM, and southbridge (fast)
	- Southbridge: interconnects I/O devices (slow)
- data travels on bus paths 
