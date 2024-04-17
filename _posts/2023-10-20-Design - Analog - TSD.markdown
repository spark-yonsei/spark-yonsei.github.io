---
layout: post
title:  "Analog - TSD"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 3
---

TSD: Thermal Shutdown.

외부 온도가 너무 높아지면 TSD 회로가 동작해서 chip을 꺼버린다.

이때, 온도가 왔다갔다하면 chip이 꺼졌다 켜졌다 하는걸 방지하기 위해 on/off 온도에 hysteresis를 준다.


TSD 내부는 어떻게 생겼나?
BJT 하나 넣어서 CTAT 특성 만들어놓고, CTAT 전압이랑 온도가 변해도 일정한 VREF 전압을 비교한다.
그리고 그 전압 차이를 온도 차이로 간주해서 온도를 측정하고, 너무 차이나면 꺼지게 만들어둔다.

TSD는 VREF쪽 amp의 matching을 잘 해줘야 한다. 하여간 matching이 좀 중요한 회로다.