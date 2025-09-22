Class: [[OS Internals and Design]]
Date: 09-03-2025
Topics: #OS #C #code #assembly 

###### Write to Display

- translate x and y into linear address 
```
w/screen width = 80
h/screen height = 25 
x = column (0 < x < 79)
y = row (0 < x < 25)
start = 0x8000
address to place character = 2 x (x + y(w)) + start/0xB8000
	= 0xB80A0 (next row)
```
- equation multiplied by 2
- address 0xB8001 is the color
	- color x2A = 0010 1010 
		- Digits 0**010** is the background color
		- Digits **1010** is the text color 
	- uses the colors number translated into hex or binary 

###### Reading from Keyboard

- 0x60 - keyboard data port
	- returns keyboard [scan codes](https://wiki.osdev.org/PS/2_Keyboard)
	- controls key press and release - modified by leading bit of binary 
		- QWERTY uses scan code set 1
- 0x64 - keyboard status port 
Reading from the Port in Assembly 
- in al, 0x60 ; put byte from port 80 into al
	- inb (input byte) 
	- inw (input word)
- scan code must be converted into ASCII
- should check if keyboard is ready for data before sending 

###### Determine Press or Release  

 uint8 scan code = inb(0x60)
 if  ((scan code & 0x80) == 0x80) - performs bitwise and 
 // release
 else 
// press
###### Status of Keyboard 

uint8 status code = inb(0x64)
if ((status code & 0x01) == 0x01) 
// not ready
else 
// ready 

Ex. scan code = 
p is pressed = 0x1A/ 00011010 
 p release = 0x9A/ 10011010
 status code 
 **Bit 0 = 1** → there is data waiting in port 0x60
 **Bit 0 = 0** → ready to receive data

###### Reading and Writing to Storage 

- floppy disks are easiest to interface with
Cylinder-Head-Sector-Addressing 
- CHS addressing scheme accesses a specific memory location in storage
	- required by INT13 and iNT2 which are BIOS interrupts 
To Read from Cylinder 0, head 0, sector 2: 
- CHS = 0,0,2
	- sectors start at 1 
	- cylinder and head start at 0
- must provide all 3 to communicate where to read from 
- early computers needed to know physical location of data since head(disk read and write) must manually write to the location
- Most modern OS use logical block addressing 
Logical Block Addressing 
- LBA provides a linear address space for accessing sectors 
	- a sector (512 bytes) is the minimal amount of addressing retrieved to write to storage