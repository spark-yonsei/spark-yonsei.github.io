---
layout: post
title:  "Analog - LDO - Amplifier Design"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 3
---

LDO : Low Dropout Regulators<br>
<br>
PMOS를 써서 만들면 Common Source 구조가 되고,<br>
NMOS를 써서 만들면 Source Follower 구조가 된다.<br>
<br>
Low-Dropout이 중요하지 않은 경우엔느 NMOS가 Pass Device로 쓰일 수 있다.<br>
Gate와 Source 사이에 전압 차이가 필요하긴 한데, Rout이 작아서(아마 NMOS PMOS의 $$\mu$$차이 이야기)<br>
Compensation이 더 쉽다.<br>
NMOS를 쓰면 follower configuration이 된다.<br>
<br>
근데 이렇게 만들면, NMOS의 gate에 들어오는 ripple이 그대로 souce(출력 노드)로 전해진다.<br>
그래서 NMOS를 쓸거면 Amp에서 Ripple이 거의 안들어오게 해야 한다.<br>
<br>
![alt text](/public/img/LDOamp1.png)<br>
<br>
Low Voltage Operation이 중요할때는 PMOS를 쓴다.<br>
PMOS는 Source에서 Drain으로의 Gain이든, Gate에서 Drain으로의 gain이든 모두 $$g_m r_{ds}$$다.<br>
<br>
그래서, Power line에서 ripple이 들어올 경우, Amp에서도 같은 ripple을 출력해줘야 PMOS 전류가 안흔들린다.<br>
<br>
그래서 NMOS에 쓰이는 AMP는 power line의 ripple을 다 없애야 하고,<br>
PMOS에 쓰이는 amp는 power line의 ripple을 그대로 출력에 전달해야 한다.<br>
<br>
Ripple을 그대로 전달하는 구조:<br>
<br>
![alt text](/public/img/LDOamp2.png)<br>
<br>
이게 왜 ripple을 그대로 전달하는 구조인가?<br>
그건 이 모델의 small signal model을 봐야 한다.<br>
아니면 이렇게 만들어도 된다.<br>

<br>
![alt text](/public/img/LDOamp3.png)<br>
<br>

<br>
아니면 이렇게 만들어도 된다.<br>

<br>
![alt text](/public/img/LDOamp4.png)<br>
<br>



