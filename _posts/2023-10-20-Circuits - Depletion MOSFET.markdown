---
layout: post
title:  "Depletion MOSFET"
date:   2023-10-04 19:31:29 +0900
categories: Circuits
order: 5
---

MOSFET에 대해 이미 배우긴 했지만, MOSFET에는 Enhancement mode MOSFET과 Depletion mode MOSFET이 있다.<br>
Enhancement mode MOSFET이 우리가 원래 아는 MOSFET이고,<br>
Depletion mode MOSFET은 channel이 생겨날 위치에 n-type dopant implant를 박아서 channel을 미리 만들어놓은 MOSFET이다.<br>
<br>
그래서 Vgs=0일 때, Enhancement MOSFET이면 당연히 MOSFET이 꺼져있다. Vgs가 Vth보다 작아서 채널이 안생기니까.<br>
근데 depletion mode MOSFET이면 Vgs를 마이너스로 걸어야 겨우겨우 채널이 사라져 MOSFET이 꺼진다. 즉, Vth가 마이너스다. 그래서 NMOS긴 한데 Vth가 마이너스인 NMOS가 된다.<br>
<br>
Native MOSFET이라는 것도 있다. Native면 특성이 Enhancement와 Depletion 사이라서, Vth~=0인 MOSFET을 말한다.<br>
우리가 아는 NMOS는 P-well 위에 fabricate하는데, Native NMOS는 약하게 도핑된 p-type silicon 위에 fabricate한다. 당연히, 비교하자면 p-well의 농도가 더 높을 것이다.<br>
<br>
그래서, p-type silicon위에 fabricate할때는 bulk에 상대적으로 hole이 적은 상태가 된다. 그래서 채널이 훨씬 쉽게 생긴다! 결국 Vth가 낮다고 말할 수 있다.<br>
이 방식으로 Vth~=0까지 가면 Native MOSFET이 된다.<br>
<br>
Vth 낮으면 좋은거 아닌가? Native MOSFET은 n-well이나 p-well 위에 만들어진 MOSFET들보다 conductivity가 낮다. 그래서 같은 conductivity를 얻으려고 해도, native MOSFET은 일반 MOSFET들보다 크기가 더 커야 한다.<br>
<br>
Depletion load NMOS Logic이라는게 있다. Logic gate들 만드는 방식 중 하나인건데, 이 방식은 depletion-mode NMOS를 Current Source로 만들어 쓴다. Depletion MOSFET은 다른 MOSFET들보다 더 우수한 current source로서 동작할 수 있기 때문이다.<br>
<br>
인텔이 HMOS라고 부르는 process가 depletion-load NMOS process다.<br>
