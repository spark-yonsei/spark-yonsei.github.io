---
layout: post
title:  "Electromagnetics - Field Quantities"
date:   2023-10-24 19:31:29 +0900
categories: Physics
order: 2
---

전자기학에서는 다양한 field들을 다룬다.<br>
<br>
Field Quantities:<br>
$$ \bar{E} $$ : Electric field intensity [$$V/m$$]<br>
$$ \bar{H} $$ : Magnetic field intensity [$$A/m$$]<br>
$$ \bar{D} $$ : Electric flux density [$$C/m^2$$]<br>
$$ \bar{B} $$ : Magnetic flux density [$$Wb$$]<br>
$$ \bar{J} $$ : Electric current density [$$A/m^2$$]<br>
$$ \rho $$ : Electric charge density [$$C/m^3$$]<br>
<br>
$$ \bar{E} $$는 Electric field, $$ \bar{H} $$는 Magnetic field라고 자주 불리지만, 엄밀한 명칭은 intensity까지 붙인 것이다.<br>
<br>
이 물리량들은 모두 시간과 공간에 대한 함수다.<br>
그렇기에 원래는 $$ \bar{E}(x,y,z,t) $$ 형태지만, 편의를 위해 $$(x,y,z,t)$$를 생략하는 경우가 많다.<br>
<br>
이 중 $$ \rho $$는 scalar field, 나머지 field들은 vector field다.<br>
$$ \rho $$는 $$(x,y,z,t)$$에 의해 그 위치, 시간에서의 scalar 값이 결정되고,<br>
$$ \bar{E}, \bar{H} $$ 등 다른 field들은 $$(x,y,z,t)$$에 의해 그 위치, 시간에서의 vector가 결정되는 것이다.<br>
<br>
<br>

Faraday's Law:<br>
어떤 closed contour c에 대해,
<br>

![alt text](/public/img/EM2.png)<br>

<br>
이때 S는 평면일 필요는 없고, Boundary가 폐곡선 c인 임의의 곡면이면 된다.<br>
<br>
$$ \oint_{c}^{}\bar{E}\cdot d\bar{l} $$을 계산할 때는?<br>
$$ \bar{E} $$랑 각 $$ d\bar{l} $$들 dot product해서 더한게 $$ \oint_{c}^{}\bar{E}\cdot d\bar{l} $$다.<br>
$$ \bar{E} $$의 단위가 [V/m], $$ d\bar{l} $$의 단위가 [m]이라 $$ \oint_{c}^{}\bar{E}\cdot d\bar{l} $$의 단위는 [V]다.<br>
<br>
Maxwell-Ampère's Law:<br>
<br>

![alt text](/public/img/EM3.png)<br>

<br>
우변 두번째 항이 중요하다. 이게 없으면 Ampère's Law, 있으면 Maxwell-Ampère's Law다.<br>
이 항이 표현하는건 'displacement current'다. 왜 displacement냐면, 이 곳이 아닌 다른 곳에서 전류가 생긴다는 뜻으로 생각하면 된다.<br>



<br>
Charge Conservation Equation / Continuity Equation:<br>
Charge Conservation Equation(전하량 보존법칙)이라고도 부르고, Continuity Equation이라고도 부른다.<br>
<br>

![alt text](/public/img/EM4.png)<br>
여기서 봐야 할 것은, charge가 안움직이면 전류가 생기지 않는다는 점이다.


Stokes' Theorem, Divergence Theorem
![alt text](/public/img/EM5.png)<br>


Faraday's equation, Maxwell-Ampere's law에 Stokes' theorem을 적용해서 두 수식을 'differential form'이라는 형태로 표현할 수 있다.

![alt text](/public/img/EM6.png)<br>