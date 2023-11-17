---
layout: post
title:  "Cadence 사람들"
date:   2023-10-04 19:31:29 +0900
categories: Miscellaneous
---

Cadence 사람들 왔을 때 얘기:<br>
ASIL: Automotive Safety Integrity Level. ASIL-A~D가 있는데, D가 가장 높은 단계다.<br>
자동차 안전 기준은 ISO 26262에 기반한다.<br>
USF: Unified Safety Format<br>
UPF: Unified Power Format<br>
<br>
RTL-> Netlist로 Synthsize할 때, 사고 위험 없이 안전하게 합성됐는지 확인하는 기준이 USF다. UPF는 Low power 설계에서 사용되는 기준이다.<br>
<br>
Cadence의 Legato에서는 회로가 안전한지 확인하기 위해, 회로 내의 모든 Connection을 한번씩 다 끊어본다. 돌리는 데에 연산력이 엄청나게 필요해서, CPU가 여러 개 있어도 시간이 엄청나게 걸린다.<br>
<br>
원래 .scs파일, 즉 netlist 파일은 매번 캐시메모리에 저장된다. 근데 여기서는 캐시메모리에 netlist 하나 박아놓고 fault만 달라지게 계속 돌린다.<br>
<br>
설마 이런 metal line들도 끊어지겠냐 싶은 line들도 있지만, 자동차는 정말 천만분의1도 놓치면 안돼서 이렇게까지 한다.<br>
근데, 돌릴때 조건을 conservative로 놓는건 조금 신중해야 한다. Conservative 고르면 회로가 만분의 일 오차까지(80dB) 보게 된다. 이러다보면 시간도 엄청 오래 걸리고, 잘 수렴도 안해서 conversion error가 날 수 있다. 캐패시터 전압이 +0.0001에서 -0.0001 사이를 진동한다든가.<br>
<br>
그리고, short보다 open이 들어간 회로가 시간이 더 많이 걸린다.<br>
Open ~= 커다란 저항 = 작은 전류라서 이 값으로 수렴하는 데에 시간이 오래 걸리기 때문이다.<br>
<br>
회로를 끊어보는 방식은 IEEE 2427을 따른다.<br>
<br>
Cadence에서 이 tool을 광고하는 근거는, 이 tool은 연산을 단순화하기 위해 여러가지 기술들이 적용되어 있다는 점이다.<br>
<br>
MOSFET aging에 대한 모델은 standard가 없어서, 회사마다 각자 모델을 갖고 있다. 케이던스도 나름의 모델이 있고, 삼성전자, TSMC도 각자의 모델이 있다.<br>
<br>