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

Power와 thermal management는 뗄래야 뗄 수 없는 관계다.
옛날에는 AP정도에만 temp sensor가 들어갔는데, 요즘은 온갖 제품에 temp sensor가 다 들어간다.



Dvfs: dynamic voltage frequency scaling
동작하다가 너무 뜨거워지면 전압 주파수 내려서 식히고, 적절히 식으면 다시 전압 주파수 올리는 방식

온도와 성능이 모두 일정 범위 내에 있을 수 있도록 하는 기술이다

Dvfs 없으면?
온도 증가 -> 전류 증가 -> 온도 증가
이렇게 positive feedback 반복된다

그래서 열관리도 중요한데, 딱히 이런건 전공하는 사람들이 없다

요즘은 soc 안에 hot spot이 여러 곳이라, 온도센서가 여러 곳에 들어가야 한다

근데 온도센서가 크기 때문에 여러개 넣기는 또 어렵다

온도센서 회로가 왜 크냐면, 모든 pvt corner를 버티게 만들어야 하기 때문이다. 산포가 작아야 한다.

온도센서에는 BJT가 들어가는데, 전원전압이 너무 내려가면 쓸 수가 없다.
그리고 사실 PnR을 위해서는 BJT가 없는게 낫다.