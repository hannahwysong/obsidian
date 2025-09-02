Class: [[OS Internals and Design]]
Date: 08-29-2025
Topics: #OS #OS-structure #hardware #assembly #boot-loader #kernal #HAL #MBR #BIOS #UFEI #x86 

- modern motherboards have removed the north and southbride 
	- north has been migrated into the CPU 
	- a chip handles the responsibility of south
The Boot Process
- PSU sends power to the system 
- BIOS (basic input and output ) prepares hardware and loads the boot-loader from the master boot record MBR into memory 
	- BIOS is stored on a chip on the motherboard 
	- master boot record (MBR) is the first 512 bytes on the storage device 
	- power on set (POST) initializes the RAM
	- if bootable disk is found, starts its boot-loader
- Unified Extensible Firmware Interface (UEFI) is modern BIOS 
	- provides GUI interface
	- mouse support
	- secure boot
	- faster boot times 
	- up to 128 physical partitions 
- Boot-loader is stored in the MBR
	- sets up hardware for OS and loads kernel into memory 
	- MBR specifies which partitions are available on storage
	- boot-loader code in the MBR can jump the computers execution of active partition code
	- multiple partitions can be used to boot different OS from the same storage device 
- Kernel is now running and initialize and execute core functions of the operating system
	- kernel connects and manages resources for OS 
The Shutdown Process 
- OS cannot pull the plug when turned off
	- unsaved files in RAM need to be saved to storage 
	- OS needs to request processes terminate 
		- processes may be in virtual memory (slow storage) and have to finish before terminating 
	- the kernel sends a signal to the BIOS that turns the PSU off 
The Kernel 
- lowest level of the operating system 
- low level programming necessary to interface the hardware directly 
	- usually a combination of both C and assembly 
Execution Modes 
- x86 based processors have two main CPU modes: 
	Real Mode
	- 16 bit instructions, 16 bit registers, 16 bit addresses 
	- can call BIOS interrupts 
	- no protections 
	- CPU boots into this mode 
	Protected Mode 
	- 32 bit instructions, 32 bit registers, 32 bit addresses 
	- cannot call BIOS interrupts 
	- extra protections, multitasking, virtual memory 
	- all major OS run in protected mode
	Long Mode 
	- 64 bit instructions, 64 bit registers, 64 bit addresses 
	- 8 more registers available 
	- more secure 
	- compatible with 32 and 16 bit applications 
- Protected mode is enabled by setting bit 0 to 1 in register CR0
	- switching back is not easy
Hardware Abstraction Layer 
- OS must implement a hardware abstraction layer (HAL)
- acts as an interface between hardware and the OS 
- located within the kernel 
- HAL allows us to: 
	- write to display
	- write to storage
	- read from keyboard
	- read from storage
VGA Text Mode 
- limited, cant display nice graphics 
- must be ran in Real Mode 
	- registers AH and AL are set 
Write to Display
- write to display by writing to memory locations starting at 0xB800
- each char on display is comprised of two bytes: 
	- [ascii](https://www.asciitable.com/) (0xB8000)
	- [color](https://wiki.osdev.org/Printing_To_Screen) (0xB8001) 
		- The most significant 3 bits specifies the background color  
		- The least significant 4 bits specifies the text color

