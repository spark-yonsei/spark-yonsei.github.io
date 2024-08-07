---
layout: post
title:  "Analog - PLL"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 3
---

PLL : Phase Locked Loop<br>
<br>
<br>
PLL은 Clock 신호를 입력받아, 다른 주파수의 Clock 신호를 출력한다.
Oscillator 회로로는 만들기 어려운 수백MHz, GHz 대역의 Clock 신호를 만드는 데에 쓰인다.

고주파 Clock이 아니더라도, Clock의 Jitter를 없애기 위해 PLL을 사용하기도 한다.
Data와 Clock의 sync를 맞추기 위해 

PLL은 3개 회로를 기본으로 한다.
PD: Phase Detector
CP: Charge Pump
VCO: Voltage Controlled Oscillator

PLL이 왜 필요한가?
data는 어디 안들르고 바로 오지만, clock은 tree처럼 이곳저곳에서 쪼개져서 들어온다.
그래서 바로 오는 data와 쪼개져서 느리게 들어오는 clock과 도달 시점이 달라서 phase 차이가 날 수 있다.
이걸 보상해주기 위해 PLL을 쓸 수 있다.


PLL의 


PLL은 layout해놓으면 캐패시터가 엄청나게 커다랗다.
Loop filter에 엄청나게 커다란 캐패시터가 들어가기 때문이다.

PLL이 Lock되면, PLL block에서 Lock 신호를 high로 올려준다.
다른 block들은 그거 보고 동작하기 시작하면 된다.



chip이 켜지면 Analog trimming data 등 정보가 들어있는 Flash memory를 읽는데,
Flash memory를 PLL이 Lock 되기 전에 읽기도 한다. PLL이 Lock되는 데에는 시간이 좀 걸리니까, 시간 아끼기 위해서다.

PLL은 출력 신호의 phase와 입력 신호의 phase를 비교하는 feedback system이다.
비교는 PLL 안의 phase detector에서 진행된다.

그니까, 이런 식이다.

*그냥, XOR gate를 phase detector로 사용할 수 있다
이상적인 phase detector면 출력 전압의 시간 평균과 phase 차이가 비례하며, phase 차이가 0이면 출력 전압의 시간 평균도 0이다.



PLL 안에 loop filter가 있어서, 나중에 lock이 안풀리는 문제가 있었던 적이 있다.

PLL에서 왜 lock detection을 하나? 처음에는 PLL 주파수랑 external 주파수랑 좀 다르니까.
주파수가 같아지면 그때 PLL clock으로 바꿔준다. 그게 external과 lock이 된 상태다.

PLL을 왜 쓰냐? 여기서는 피에조센서에 쓸 PWM이 필요하다보니 clock boosting이 필요해서 썼다.

PLL:
보통 오실레이터에서 출력되는 클락은 8MHz, 12MHz, 16MHz라서 실제 시스템 동작속도보다 느리다
그래서 PLL은 주파수를 올리고 안정적으로 만든다
여기서 나온 클락신호가 cpu에 전달된다

Mcu 내의 다른 로직들은 보통 cpu보다 구동 주파수가 낮다. 그래서 prescaler(전치분주기)로 주파수를 내려준다


PLL은 lock되면 lock신호가 high가 된다. high가 되면 다른 block들이 동작하면 된다.
Flash 읽을때, PLL이 lock 되기 전에 읽는 경우도 있다. 시간 아끼기 위해서 이런 동작을 한다. Lock되는데에 시간이 좀 걸리니까.

주파수가 16MHz밖에 안되는데 PLL을 쓰는 경우도 있었다. 이건 jitter 줄이려고 쓴거다.

prescaler: clock을 다른 주파수로 만든다. /2, /4, /8 등.
clock gating: 안쓰는 block은 clock마저 안들어가게 꺼버리는거. power 아끼려고 쓰는 기술이다.






요즘 많이 쓰는 구조가 charge pump PLL이다.

Oscillator 회로에서 바로 수백M, GHz 수준 주파수를 만들 수가 없으니,
일단 저주파 clock 만들어놓고 이걸 PLL로 주파수를 높인다. 이게 RF에서의 PLL



생각해보면, PD가 XOR gate랑 상당히 비슷하다는 것을 알 수 있다.

그래서 PD는 그렇다 치고, PLL은 뭔가?

우리가 VCO를 동작시키고 있는데, VCO의 출력파형의 phase가 reference clock의 phase랑 딱 맞았으면 좋겠을 경우, 어떻게 해야 할까?

VCO에 넣는 전압을 잠시 바꿨다가 원래대로 돌려놓으면 된다.
전압이 바뀌면 출력 파형의 주파수가 변하니까, 이걸로 phase 맞춰놓고 다시 전압 복구해서 원래 주파수로 돌려놓으면 된다.

