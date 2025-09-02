Class: [[Team Projects]]
Date: 08-27-2025
Topics: #teamprojects #capstone #requirements #raspberry-pi 

Design Challenge

- Death star plans are accessed via a raspberry pi
- An engineer in the secret lab must transmit the plans from the raspberry pi to a rebel server in a way the guards will not detect
- The rebel server must reveal the plans to the galaxy via a public web page that enables downloading the plans
- It must run on mobile device must analyze the images to find a weakness ( depicted as red circle)
- The app must display a scrollable table containing images
- Plans are represented by 1024x1024 PNG
- Right before testing you get the flash drive with 90 incorrect and 10 correct images
- Software on the raspberry pi must identify which are correct
- All 10 must be transferred in an elapsed time of 600 seconds
	- time limit only applies to transmission
- All communications between raspberry pi and server must be encrypted
- Industry standard encryption is fine
- Do not have to encrypt meta data only the payload
- Raspberry pi can be within line of sight of server
	- Must receive the md5 sum of the image for confirmation of lossless communication
- Sever must be at least 5 meters from lab window

What we are provided:

- A PC with EZ connect wifi will be provided
- Up to two of each: keyboard, mouse, HDMI display
- Mobile device/ emulator to host mobile app component

Constraints

- Wifi, cellular, and bluetooth will be instantly detected
- A wire is detectable so the communication method must be wireless
- Total cost of the project must not go over 300
- Must be tested within the basement of Russ
- Complete solution must be completed by last week of semester
- Only what is inside the red circle needs to be transmitted 

New Requirements

- there is a stored personal message on something must be viewed by only one person and it must be authenticated without a password 

Raspberry Pi 

- Raspberry Pi Model 4B board
- broadcom BCM2711 Quad-Core Cortex A72
- connected via ethernet, usb, and 2 displays
- 40 pin GIPO header
- has a GPU with 4k
- SPI - serial peripheral interface 
	- very fast can send and receive simultaneously 
	- requires more pins 
- I2C - inter integrated circuit
- UART - receiver/ transmitter 
