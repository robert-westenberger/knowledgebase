---
title: Arduino Board
description: 
published: true
date: 2021-06-16T02:41:56.763Z
tags: arduino, hardware
editor: markdown
---

# Arduino Uno Hardware
* USB
	* Upload instructions to arduino, send data and receive from computer
* Power Connector
	* Supply power to the board. Can be powered with standard wall power adapter (stepped down to 5 volts).
  
![microcontroller.png](/microcontroller.png)
* Microcontroller - Tiny computer that contains a processor to execute instructions, includes varios types of memory to hold data and instructions, and provides various avenues for sending and receiving data.

![poweranalogsockets.png](/poweranalogsockets.png)
* Power Sockets
	* Offers power connections and ability to use external reset button
* Analog sockets
	* Inputs that are used to measure electrical signals that vary in voltage. Pins A4 and A5 can also be used for sendign data to and receiving it from other devices. 

![digital_sockets.png](/digital_sockets.png)
* Digital I/O Pins / Sockets
	* Detect whether or not an electrical signal is present or generate a signal on command. Pins 0 and 1 are the **serial port**, used to excahnge data with other devices, such as a computer via the USB connector circuitry. 
  * The pins with tilde (~) can also generate a varying electrical signal (which looks like a wave on an oscilloscope, thus the wavy tilde). This can be useful for things like lighting efects or controlling electric motors.
  
![leds.png](/leds.png)
* TX
	* Lights up when data is being transmitted
* RX
	* Lights up when data is being received
* L 
	* For own use. Connected to the digital i/o pin 13. 
  
![reset.png](/reset.png)
* reset button

## Arduino Shields
Shields are boards that can be plugged on top of the Arduino circuit board to expand its capabilities. There are shields that contain an ethernet interface for example, that lets the arduino communicate over networks and the internet. 