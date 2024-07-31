---
layout: post
title:  "Digital - Serial Communication Protocols"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 6
---


Serial Communication Protocol에는 UART, I2C, SPI가 있다.


UART (Universal Asynchronous Receiver-Transmitter):
UART는 device간 단거리 통신에 쓰이는 asynchronous serial communication protocol이다.

UART 통신은 전선 2개를 사용한다.
하나는 데이터 송신용(Tx), 하나는 데이터 수신용(Rx)이다.

UART 통신은 clock 신호를 사용하지 않는다.
그래서 각 data frame 앞뒤로 start bit, stop bit가 있어야 한다.

구조가 간단한 통신 방식이다.
GPS, 블루투스 등에 쓰인다.


SPI (Serial Peripheral Interface):

SPI는 전선 4개를 사용한다.
MOSI (Master Out Slave In): Data 송신
MISO (Master In Slave Out): Data 수신
SCLK (Serial Clock): Clock 신호
CS (Chip Select): 대상 device 선택

SPI 통신은 master-slave 구조로 진행된다.
master가 통신을 시작해서, 1개 또는 여러개 slave로 데이터를 전송한다.

Full-duplex 통신을 지원한다. 데이터를 전송하면서 동시에 데이터를 받을 수 있다는 뜻이다.

SPI는 데이터 전송 rate가 높아서,
빠르고 효율적인 데이터 전송이 필요한 곳에 쓰인다.


I2C (Inter-Integrated Circuit):

I2C는 multi-master, multi-slave, bidirectional이다.

2개 전선을 쓴다.
SDA (Serial Data Line): 양방향 데이터 송수신
SCL (Serial Clock Line): Clock 신호

I2C를 쓰면, 서로 다른 address를 쓰는 여러개 device가 1개 bus에 연결될 수 있다.

I2C는 SPI, UART보다 느리지만 더 간단한 구조고 전선도 덜 쓴다.
그래서 pin이 적어야 하는 센서, EEPROM 메모리칩, real-time clock 등에 쓰인다.



SDA: bus를 통해 data 전달
SCL: master, slave 사이 data transfer를 synchronize한다.

I2C가 위 2개보다 나은 점:
Flexibility – The I2C protocol supports multi-master, multi-slave communication, which implies you can add a lot of functionality to your design. More than one master IC controlling and communicating with the slave ICs can speed things up and add functionalities to the embedded system.

Addressing feature – Yet another advantage of the I2C protocol lies in its inherent ability to use chip addressing. It means that you can easily add components to the bus without any complexity. It eliminates the necessity of CS (chip select) lines.

Simplicity – I2C protocol doesn’t complicate the design. It requires only two bidirectional signal lines to establish communication among multiple devices. Further, the pin count is low as well.

Better error handling mechanism – To improve the error detection and correction mechanism, the I2C protocol relies on ACK/NACK feature, which is a robust error correction feature. ACK stands for Acknowledgement whereas NACK means No Acknowledgement.

Adaptable – The I2C protocol is adaptable in the sense that it can work well with both slow ICs and fast ICs.


I2C가 위 2개보다 안좋은점:
Conflicts – Due to chip addressing, there’s always a possibility of an address conflict.

Slower speeds – I2C protocol uses pull-up resistors rather than the push-pull ones used by its peers. Due to the open-drain design, the speed is limited.

Requires more space – Now, as an embedded system engineer, you know how valuable PCB real estate is. So, it isn’t such a positive attribute that the I2C protocol requires so much space for its pull-up resistors.


slave는 master에게 ACK을 보내야 한다.
그래서 신호 받기만 할거여도 SDA는 출력을 보낼 수 있는 구조여야 한다.

I2C 통신으로 특정 code pattern을 넣어야 특정 레지스터들에 접근 가능하도록 하는게 protection 기능이다.
예를 들어, analog trimming data 영역은 사용자가 못건드리게 protection을 걸어놓는다. 이거 건드리면 동작이 아예 안될수도 있다.




I3C: Improved Inter-Integrated Circuit

I2C operates in five main modes:

Standard Mode: 100 kHz
Fast Mode: 400 kHz
Fast Mode Plus: 1 MHz
High Speed: 3.4 MHz
Ultra-Fast Mode: 5 MHz
I3C, on the other hand, has a Standard Data Rate of 12.5 MHz, with new versions of I3C supporting data rates up to 100 Mbps. Needless to say, I3C supports speeds that far surpasses that of I2C.

Backward Compatibility
When developing I3C, the ability for the protocol to be fully backward compatible was a significant focus. I3C applications can operate with I2C slave devices as well as native I3C devices. This backward compatibility allows engineers time to phase out their existing I2C applications. This phase-out time is necessary for embedded systems engineers because it makes the adoption of the new protocol much easier and streamlined.

Dynamic Addressing
I2C has a device addressing technique called static addressing. This, in simple terms, means that manufacturers lock in their device addresses in production. One of the drawbacks of this is that vendors may use the same address as another vendor for a product that uses I2C, causing issues during integration. During bus initialization, the I3C controller assigns a 7-bit dynamic address to each device on the I3C bus, thereby eliminating the problems associated with duplicate addresses because each I3C device receives a unique address from the master.

Hot-Join
Another new feature to I3C is the protocol's ability to allow other slave devices to be added or taken away from the system with no interrupts to the system as a whole. The system is called hot-join. This mechanism allows slaves to join the bus after the bus is already configured.

In-band Interrupt
The I3C interface uses a push-pull clock line and an open-drain data line for operations. The data line allows slaves to take control and initiate interrupts when needed. This feature is unique to I3C as this same application on the I2C bus would require a third line. I3C slaves can request an interrupt when the bus is idle, whereas I2C slaves cannot. I3C assesses conflicts between multiple slaves by allowing the lowest assigned address to win.

Power Efficiency
Another attribute important to any new technology is its ability to manage power consumption better than previous product iterations. Computers need to be faster but use much less energy than the prior model; new iterations of bus protocols are no different.

Due to a change in output method from an open drain method to a push-pull output, I3C can be much more energy efficient than I2C. An open-drain process requires pull-up resistors that, when activated, require a significant amount of power to operate. Push-pull operations do not require pull-up resistors to work, meaning the method can reduce energy consumption because it does not need to power any external resistors to function.

Another factor that plays into the power-saving quality of I3C over I2C is its data transfer speed improvements. The benefits here are simple to understand. Because messages can now be sent over the I3C bus at significantly faster rates, the bus can turn on and shut off target devices much quicker than was possible with I2C. This process saves a noticeable amount of power consumption compared to I2C.
