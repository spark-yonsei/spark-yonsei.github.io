---
layout: post
title:  "Analog - Bandgap Reference"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 3
---

Bandgap Voltage Reference는 PVT variation이나 loading 상황에 관계없이 일정한 전압을 주려고 쓴다.

Bandgap reference에는 BJT랑 저항이 들어가기 때문에 면적이 많이 필요하다. 그래서 비싸다.
그리고 noise, precision specification을 원하는 수준까지 올리려면 power가 많이 필요할 수 있다.

bandgap에는 3종류가 있다.
BJT, MOSFET, 2TR

2TR은 NMOS 2개로 Bandgap을 만든 경우고, power 소비가 적어야 할때 쓴다.

MOSFET으로 bandgap을 만들때에는 weak inversion region을 쓴다. BJT처럼 exponential하니까.

그 외 회로에서도 power를 적게 써야 할 때 가끔 weak inversion region을 쓴다.

weak inversion region은 gm이 부족하지 않나?
이건 W 키우면 된다.
그럼 면적 손해가 일어나지 않나?
L 줄이면 된다.

캐패시턴스가 작을수록 트랜지스터의 f_T가 크다.
전압을 크게 넣으면 f_T가 커진다는 어조로 적혀있는데, 이거 확인좀

왜 MOS로 bandgap 많이 안만들고 BJT 쓰냐?
MOS로 만들면 공정 variation이 좀 크다.


Bandgap referenceㄹ르 만드는, 널리 쓰이는 방법중 하나는 parasitic BJT를 쓰는 방식이다.
이 방식에서는 PTAT 전압과 CTAT 전압을 더해 bandgap reference를 만든다.
그 외에 PTAT 전류와 CTAT 전류를 더할수도 있고, 뭐 다양한 방법들이 있다.

대부분의 기존 design들은 error correction을 위해 amplifier를 쓴다.
amplifier를 쓰면 온도랑 supply voltage에 둔감해지긴 하는데,
amplifier는 power도 많이 먹고 면적도 많이 먹는다.

amplifier를 안쓰는 design들도 있긴 하다.
이 경우에는 MOSFET을 saturation mode로 쓰기 때문에, MOSFET이 power를 많이 먹는다.

근데, amplifier든 saturated device든 voltage headroom이 필요하다.
그래서 이런걸 쓰면 supply voltage 내리는 데에 한계가 있다.

게다가, 이런 design들은 온도에 둔감한 전압 출력을 위해 matching이 잘된 저항들을 필요로 하기에,
면적이 넓은 저항들을 써야 한다. 그래서 면적 손해를 본다.

그래서, 여기서 제시하는 구조는 amp도 없고, saturated device도 없고, 저항도 없는 구조다.
이 구조는 power consumption이 작기 때문에 power를 아끼기 위한 duty cycling도 필요 없고, startup도 필요 없다.
는 내용이 'A portable 2-Transistor Picowatt Temperature-Compensated Voltage Reference Operating at 0.5V'의 내용이다.

