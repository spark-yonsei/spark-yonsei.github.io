---
layout: post
title:  "Digital - Bus Protocols"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 6
---

AHB는 burst가 되는데, APB는 안된다.

<br>
PCI Bus: Peripheral Component Interconnect Bus<br>
컴퓨터 메인보드에 주변 장치를 장착하는데에 쓰이는 컴퓨터 버스의 일종이다.<br>
<br>
PXI: PCI eXtensions for Instrumentation<br>
여러가지 장비들을 측정, 제어하는데에 사용되는 플랫폼이다.<br>

AMBA(Advanced Microcontroller Bus Architecture):<br>
ARM에서 정의한 BUS protocol을 말한다. AHB, ASB, APB, AXI가 있다.<br>
<br>
AHB(Advanced High Performance Bus):<br>
고속으로 동작하는 장치들이 연결된 bus<br>
<br>
ASB(Advanced System Bus)<br>
고속으로 동작하고, AHB와 달리 Rising Edge와 Falling Edge 모두 사용한다.<br>
<br>
APB(Advanced Peripheral BUS):<br>
비교적 느린 속도로 주변 장치들을 제어하며, 전력효율을 위해 간단한 인터페이스를 갖는다.<br>
<br>
AXI(Advanced eXtensible Interface):<br>
다중채널 연결용 버스다.<br>


AMBA: ARM에서 정의한 on-chip interconnect protocol
AMBA = Advanced Microcontroller Bus Architecture

AMBA에는 여러가지 Bus protocol들이 있다.
APB = Advanced Peripheral Bus
낮은 Bandwidth를 갖는 주변기기(peripheral)를 위한 bus protocol

AHB: Advanced High-performance Bus
APB보다 높은 성능을 갖는다. 64/128bit를 지원하고, multi-master도 가능하다.
AHB-Lite는 single master를 위한 bus protocol이다.

AXI: Advanced eXtensible Interface
A/D phases, bursts, multiple outstanding addresses, OoO response를 지원한다.

ACE = AXI Coherency Extensions
ACE는 AXI의 superset이다. ACE는 multicore cluster들에 system-wide coherency를 제공한다.

CHI: Coherent Hub Interface
CHI는 credited coherency protocol, layered architecture for scalability

뒤로 갈수록 새로 나온거다. APB가 제일 옛날, CHI가 제일 최근에 나왔다.
AMBA도 AMBA4, AMBA5 이런 식으로 세대가 있다.
CHI는 AMBA5에 추가된 Bus protocol이다.