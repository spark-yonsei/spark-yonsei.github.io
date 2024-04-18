---
layout: post
title:  "Analog - PLL"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 3
---

PLL : Phase Locked Loops<br>
<br>
<br>
원래는 주파수 높은 clock을 만들려고 쓰지만, 동작 주파수가 낮은 경우에도 clock의 jitter를 없애기 위해 PLL을 쓰기도 한다.
PLL이 Lock되면, PLL block에서 Lock 신호를 high로 올려준다.
다른 block들은 그거 보고 동작하기 시작하면 된다.

chip이 켜지면 Analog trimming data 등 정보가 들어있는 Flash memory를 읽는데,
Flash memory를 PLL이 Lock 되기 전에 읽기도 한다. PLL이 Lock되는 데에는 시간이 좀 걸리니까, 시간 아끼기 위해서다.

PLL은 출력 신호의 phase와 입력 신호의 phase를 비교하는 feedback system이다.
비교는 PLL 안의 phase detector에서 진행된다.

그니까, 이런 식이다.

*그냥, XOR gate를 phase detector로 사용할 수 있다
이상적인 phase detector면 출력 전압의 시간 평균과 phase 차이가 비례하며, phase 차이가 0이면 출력 전압의 시간 평균도 0이다.



생각해보면, PD가 XOR gate랑 상당히 비슷하다는 것을 알 수 있다.

그래서 PD는 그렇다 치고, PLL은 뭔가?

우리가 VCO를 동작시키고 있는데, VCO의 출력파형의 phase가 reference clock의 phase랑 딱 맞았으면 좋겠을 경우, 어떻게 해야 할까?

VCO에 넣는 전압을 잠시 바꿨다가 원래대로 돌려놓으면 된다.
전압이 바뀌면 출력 파형의 주파수가 변하니까, 이걸로 phase 맞춰놓고 다시 전압 복구해서 원래 주파수로 돌려놓으면 된다.



PLL 안에 loop filter가 있어서, 나중에 lock이 안풀리는 문제가 있었던 적이 있다.

PLL에서 왜 lock detection을 하나? 처음에는 PLL 주파수랑 external 주파수랑 좀 다르니까.
주파수가 같아지면 그때 PLL clock으로 바꿔준다. 그게 external과 lock이 된 상태다.

PLL을 왜 쓰냐? 여기서는 피에조센서에 쓸 PWM이 필요하다보니 clock boosting이 필요해서 썼다.

PLL:
보통 오실레이터에서 출력되는 클락은 8MHz, 12MHz, 16MHz라서 실제 시스템 동작속도보다 느리다
그래서 PLL은 주파수를 올리고 안정적으로 만든다
여기서 나온 클락신호가 cpu에 전달된다

Mcu 내의 다른 로직들은 보통 cpu보다 구동 주파수가 낮다. 그래서 prescaler(전치분주기)로 주파수를 내려준다