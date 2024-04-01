---
layout: post
title:  "Digital - Serial Communication Protocols"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 6
---


💡Serial Communication Protocols(UART,I2C,SPI)📍📝

🔰 1. UART (Universal Asynchronous Receiver-Transmitter):
  ✔ UART is an asynchronous serial communication protocol commonly used for short-distance communication between devices.
 ✔ It uses two wires, one for transmitting data (TX) and another for receiving data (RX).
  ✔ UART does not have a clock signal, so the data is transmitted asynchronously using start and stop bits to mark the beginning and end of each data frame.
  ✔ It is a straightforward and simple protocol, commonly used in applications like serial communication between a microcontroller and a computer, GPS modules, and Bluetooth modules.

🔰 2. SPI (Serial Peripheral Interface):
 ✔ SPI is a synchronous serial communication protocol primarily used for
communication between microcontrollers and peripheral devices, such as sensors, displays, and memory chips.
 ✔ It requires four wires: a master-out-slave-in (MOSI) line for data transmission, a master-in-slave-out (MISO) line for data reception, a clock (SCK) line for synchronization, and a chip select (CS) line to select the target device.
 ✔ SPI operates in a master-slave configuration, where a master device initiates the communication and controls the data transfer to one or more slave devices.
  ✔ It supports full-duplex communication, meaning data can be simultaneously transmitted and received.
   ✔ SPI is known for its high data transfer rates and is commonly used in applications that require fast and efficient data transfer.

🔰 3. I2C (Inter-Integrated Circuit):
   ✔ I2C is a multi-master, multi-slave, and bidirectional serial communication protocol designed for communication between integrated circuits on a circuit board.
 ✔ It uses two wires: a serial data line (SDA) for bidirectional data transfer and a serial clock line (SCL) for synchronization.
   ✔ I2C allows multiple devices to share the same bus, with each device having a unique address.
   ✔ It supports both 7-bit and 10-bit addressing modes, providing the capability to connect a large number of devices.
 ✔ I2C is a slower protocol compared to UART and SPI, but it requires fewer wires and is commonly used in applications where simplicity and low pin count are important, such as sensors, EEPROM memory chips, and real-time clocks.


P.S: Repost this info & follow Vinay Varikooti for more knowledge.