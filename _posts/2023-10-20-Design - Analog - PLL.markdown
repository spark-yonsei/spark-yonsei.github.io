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


이상적인 phase det