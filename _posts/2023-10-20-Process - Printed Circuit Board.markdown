---
layout: post
title:  "Printed Circuit Board"
date:   2023-10-04 19:31:29 +0900
categories: Process
order: 14
---

PCB(Printed Circuit Board)는 IC, 캐패시터, 저항 등 소자들을 부착할 수 있게 만들어진 기판이다.<br>
각 소자들은 PCB를 통해 전기적으로 연결되어 동작하게 된다.<br>
PCB 소재로는 FR-4 Fiber glass(유리섬유)가 많이 쓰인다.<br>
<br>
현재 쓰이는 PCB의 한계점을 해결하기 위해,<br>
Interposer와 유리기판이 연구되고 있다.<br>
<br>
<br>
Interposer:<br>
최근에는 IC의 pin 갯수가 크게 늘어나 PCB에서 모든 pin들을 연결하기 어려운 경우가 많다.<br>
연결할 pin 수가 늘어나면 PCB에 더욱 미세한 회로를 그려야 하는데, 이것이 PCB 공정상 어려운 것이다.<br>
이 경우에는 PCB 위에 interposer를 올려놓고, 그 위에 소자들을 올려 연결한다.<br>
<br>
유기물로 만들면 organic interposer,<br>
Silicon으로 만들면 Si interposer가 된다.<br>
<br>
Organic interposer:<br>
공정이 쉬워 Si interposer보다 훨씬 저렴하지만,<br>
쉽게 휘어지고 표면이 울퉁불퉁해 배선 간격을 좁게 하기 어렵다.<br>
<br>
Si interposer:<br>
성능은 좋지만, 제작 공정이 어려워 가격이 비싸고 설비투자가 필요하다.<br>
TSV(Through Silicon Via) 등 쉽게 구현할 수 없는 공정들이 쓰인다.<br>
TSV는 Silicon에 아주 좁고 깊은 구멍을 뚫는 기술이다.<br>
<br>
<br>
유리기판:<br>
유리로 PCB를 만들면, FR-4 PCB보다 훨씬 미세한 회로를 그려넣을 수 있다.<br>
<br>
유리기판은 열전도성이 높아 열 방출이 쉽고,<br>
열팽창 계수가 낮아 안정성이 더 높다.<br>
FR-4보다 수분을 덜 흡수해 수명이 더 길고,<br>
고주파에서 낮은 dielectric loss 특성을 보여 RF 분야에서 관심받고 있기도 하다.<br>
<br>
하지만 압력, 충격에 쉽게 깨져 수율이 낮다는 단점도 있으며<br>
FR-4 PCB에 비해 공급망, 기술 개발, 공정 최적화가 아직 많이 부족하다.<br>
<br>
유리기판 제작에는 TSV와 유사한 TGV(Through Silicon Via) 공정이 쓰인다.<br>
유리에 아주 좁고 깊은 구멍을 뚫는 공정이다.<br>
<br>
<br>
FPCB: Flexible PCB<br>