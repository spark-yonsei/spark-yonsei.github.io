---
layout: post
title:  "Vector Calculus"
date:   2023-10-24 19:31:29 +0900
categories: Electromagnetics
order: 1
---

Electromagnetics Theory에는 크게 2가지가 있다.<br>
<br>
Microscopic Electromagnetics: 슈뢰딩거 방정식으로 표현되며, 원자 또는 분자 수 개의 특성을 설명한다.<br>
Macroscopic Electromagnetics: 맥스웰 방정식으로 표현되며, 원자 또는 분자로 이루어진 물질의 통계적인 특성을 설명한다.<br>
<br>
Macroscopic Electromagnetics는 원자, 분자 수 개에 대해서는 적용할 수 없고,<br>
그 갯수가 아보가드로 수($$N_A \approx 6.02 \cdot 10^{23}$$) 수준이 되어야 적용할 수 있다.<br>
<br>
여기에서 설명하는 전자기학은 Macroscopic Electromagnetics다.<br>
<br>
<br>
전자기학에서는 3차원 공간을 표현하기 위해 3가지 좌표계(Cartesian, Cylindrical, Spherical)를 사용한다.<br>
<br>
좌표계 변환 - 위치:<br>
<br>
좌표계 변환 - 벡터:<br>
<br>
![alt text](/public/img/EM1.png)<br>
<br>
Vector와 Vector field의 차이<br>
<br>
Gradient가 무엇인가<br>

Gradient는 어떤 Scalar Field의 

<br>
좌표계별 Gradient:<br>
<br>
Curl이 무엇인가<br>
<br>
좌표계별 Curl:<br>
<br>



<br>
유럽은 Linguistic notation : Curl $$ \bar{E} $$<br>
미국은 Gibbs notation : $$ \triangledown  \times \bar{E} $$<br>



<br>
Stokes' Theorem:<br>
$$\oint_{c}\bar{F}\cdot d\bar{l}=\iint_{S}\triangledown \times \bar{F}\cdot \hat{n}dS$$<br>
<br>
Divergence Theorem:<br>
$$\oiint_{S}\bar{F}\cdot \hat{n}dS=\iiint_{V}\triangledown \cdot \bar{F}dV$$<br>
<br>
Div, Curl을 Gibbs notation으로 적을 때는 각각 $$\triangledown \cdot $$, $$\triangledown \times $$라고 적는다.<br>
이때, $$\triangledown \times \bar{F}$$를 $$\triangledown$$와 $$\bar{F}$$를 cross product하는 거라고 해석하는건 일반적으로 틀린 해석이다.<br>
그런 해석은 Cartesian coordinates에서만 맞는 이야기다. 일반적으로, $$\triangledown \cdot $$와 $$\triangledown \times $$는 그냥 그 자체로 하나로 봐야 한다.<br>




