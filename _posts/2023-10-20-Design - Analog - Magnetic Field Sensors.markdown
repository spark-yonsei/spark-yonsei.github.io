---
layout: post
title:  "Analog - Magnetic Field Sensors"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 3
---

Hall Sensor는 작은 signal voltage를 쓰기 때문에, 온도/전압 흔들림이나 기계적 stress에 많이 영향받는다.

TMR Sensor: Tunnel Magnetoresistive Sensor

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

