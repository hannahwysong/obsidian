Class: [[OS Internals and Design]]
Date: 09-19-2025
Topics: 

- all programs exist on the disk
- before executing they have to be brought into main memory (RAM) by the OS
	- CPU fetches instructions from RAM to execute program 

Memory Terminology 
- segment: chunk of memory assigned to a process 
- physical address: real memory address that corresponds to an actual physical memory location 
- virtual memory: an address relative to the start of the processes address space 
	- if a process exists within the range x1234 to x1FFF it will have virtual  addresses from x000 to xDCB
	- also called logical address 
- contiguous memory: memory contained within one region, one address after the other. 
- programs generate addresses for instructions and data using 3 methods: 
	- compile time - compiler decides where the program starts in memory at a fixed physical memory address. OS does nothing
	- load time - compiler decides a starting address, OS determines where this starting address is in physical memory. once loaded the process does not move in memory. 
	- execution time - compiler decides a starting address, OS determines where this starting address gets placed in physical memory. While running, the OS translates the virtual address to physical addresses 
Uniprogramming 
- running only 1 process and the OS 
- OS gets a fixed part of memory up to the highest address 
	- process is loaded at physical address x00000000
		- executes in a contiguous section of memory 
	- maximum address = memory size - os size
	- simple but does not allow for overlap of i/o and cpu usage
Requirements of Multiprogramming 
- transparency:
	- want multiple processes to coexist in physical memory 
	- no process should be aware memory is shared
	- processes should not care where they are in memory
- safety:
	- processes must not corrupt each other or the OS 
- efficiency: 
	- performance of CPU and memory should not be degraded 
Relocation 
- moving a process to any location in memory
- assume OS gets a fixed part of the memory up to the highest address 
	- with a compile time the process starts at address 0 with: Maximum address = Memory size - OS size
- base address: first physical address of the process 
- limit address: last physical address of the process 
Static Relocation 
- process is loaded, OS offsets all addresses to reflect the process's new location in memory
	- once its assigned to memory it cannot be moved
	- moving would require off-setting all the address for every instruction in the program
Dynamic Relocation
- Hardware has base register that gets added to virtual address, the result is the physical address 
- hardware compresses address with limit address
	- if the address exceeds the limit address execute a trap service routine to handle addressing error and ignore physical address
- assume all logical addresses are positive 
- benefits: 
	- OS can move a process in memory much easier
	- OS can allow a process to grow over time 
	- Hardware requirements are simple 
	- transparency: process unaware of other processes in memory 
	- safety: each memory access is checked by hardware 
	- efficiency: slightly slower but still fast 
- cons: 
	- extra hardware may increase time to access memory 
	- sharing memory between processes is impossible 
	- all running processes must coexist in physical memory 
	- still uses contiguous memory
	- moving a process to a new location in memory is very slow 
Memory Allocation 
- as processes start, grow, and terminate, OS tracks all used and unused memory. 
- new process starts the OS must decide where the process goes into memory 
	- hole: a location in memory that is not filled
	- OS wants to fill these holes with new processes
Memory Allocation Policies: 
- First Fit:  
	- allocates the process to the first hole it fits in 
	- generally faster than best fit
- Best Fit: 
	- allocates the process to the smallest hole the process will fit in 
	- generally better storage utilization than worst fit 
- Worst Fit: 
	- allocate the process to the largest hole in memory
	- remaining memory after the process may be large enough to fit another process or allow the process itself to grow
- for best and worst fit, OS must search entire list of holes to find the desired location to put the process.
Fragmentation 
- External fragmentation: memory between processes that is too small to be used
- internal fragmentation: occurs if memory split into fixed sized chunks 
	- if a process occupies one fixed sized chunk, but doesnt use it all
