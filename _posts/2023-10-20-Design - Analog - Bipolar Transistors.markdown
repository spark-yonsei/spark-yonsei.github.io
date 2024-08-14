---
layout: post
title:  "Analog - Bipolar Transistors"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 3
---

Bipolar transistor들은 CMOS 대비 더 높은 gm, 더 낮은 1/f noise를 갖는다.
breakdown voltage도 더 높고, reliability도 더 높다.

대신 shot noise는 있다
이건 고주파 noise

온도센서에는 BJT가 들어가는데, 전원전압이 너무 내려가면 쓸 수가 없다.
그리고 사실 PnR을 위해서는 BJT가 없는게 낫다.

온도 센서 회로와 TSD 회로 모두 BJT를 사용한다.


TSD 내부는 어떻게 생겼나?
BJT 하나 넣어서 CTAT 특성 만들어놓고, CTAT 전압이랑 온도가 변해도 일정한 VREF 전압을 비교한다.
그리고 그 전압 차이를 온도 차이로 간주해서 온도를 측정하고, 너무 차이나면 꺼지게 만들어둔다.