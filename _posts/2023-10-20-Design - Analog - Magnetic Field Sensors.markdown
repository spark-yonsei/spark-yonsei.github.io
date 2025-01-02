---
layout: post
title:  "Analog - Sensors"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 3
---

Magnetic Sensors:
Magnetic sensor에는 Hall Sensor와 TMR Sensor가 있다.

Hall Sensor:
Hall Sensor는 작은 signal voltage를 쓰기 때문에, 온도/전압 흔들림이나 기계적 stress에 많이 영향받는다.

TMR(Tunnel Magnetoresistive) Sensor:
magnetoresistive effect에 의해, 자기장이 변하면 전기저항이 변하는 현상을 이용한다.
이때 tunnel effect를 통해, 자기장이 바뀌면 전기저항이 크게 바뀌도록 한 구조가 TMR Sensor다.

TMR Element: 맨 아래 고정된 solid layer, 가운데에 barrier layer, 맨 위에 Free layer가 있다.

외부 자기장에 의해 free layer의 magnetization 방향이 변하는데, solid layer는 영향을 안받아 안변한다.
그래서 자기장에 의해 2개 layer 사이 magnetization각도가 바뀌고, 그 각도가 저항을 결정한다.

TMR Sensor들은 Wheatstone bridge 형태로 연결해서 쓴다.

Hall Sensor: cost-effective
TMR Sensor: better SNR, low power consumption

그래서 TMR sensor가 demanding application들에서 더 선호된다.


2가지 sensor를 동시에 쓰기도 한다.
Hall sensor는 high current detection, TMR sensor는 low current detection에 쓰는 식으로.





지문센서는 14MHz 초음파를 쓴다
초음파는 보통 kHz대역이라 14MHz 만드는게 힘들었다

TCAD로 소자 만들어서 했었다
제작은 DB하이텍에 맡겼다

노이즈 없애는게 많이 어려웠다

캠시스 초음파 지문인식센서 찾아보면 나온다
유리 밑에 센서 넣어서, 위에 손가락 대면 인식하도록 만들었다


터치센서는 fringing field 변화를 인식해 동작한다.