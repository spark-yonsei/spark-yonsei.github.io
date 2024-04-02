---
layout: post
title:  "Analog - LDO"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 3
---

LDO : Low Dropout Regulators<br>
<br>
<br>
IC가 제대로 동작하기 위해서는 흔들리지 않는 일정한 전압이 필요한 부분들이 있다.<br>
OP AMP 의 입력, MOSFET의 Gate 등 전류를 흐르게 하지 않는 노드면 BGR 회로(Bandgap Reference Circuit)으로 전압을 주면 되지만,<br>
<br>
저항, Logic Gate 등 전류를 소모하는 load가 연결된 경우에는 BGR을 쓰면 전압이 이상하게 나온다.<br>
그래서, 이때는 LDO라는 회로를 써줘야 한다.<br>
<br>
<div style="float: left">
    <img src="/public/img/LDO1.png" style="width: 50%; height: auto;" alt="my picture" />
</div>

PMOS를 써서 만들면 Common Source 구조가 되고,<br>
NMOS를 써서 만들면 Source Follower 구조가 된다.<br>
<br>
Stability:<br>
어떤 주파수로 load current를 당겨도 LDO 출력전압이 안떨어질까?<br>
안타깝게도 그렇지는 않다. frequency response가 일정하지 못하다.<br>
<br>
그럼 frequency response를 어떻게 확인할 것인가?<br>
Loop Gain을 본다.<br>
<div style="float: left">
    <img src="/public/img/LDO2.png" style="width: 50%; height: auto;" alt="my picture" />
</div>

