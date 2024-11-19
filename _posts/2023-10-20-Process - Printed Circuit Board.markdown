---
layout: post
title:  "Printed Circuit Board"
date:   2023-10-04 19:31:29 +0900
categories: Process
order: 14
---

PCB(Printed Circuit Board)는 IC, 캐패시터, 저항 등 소자들을 부착할 수 있게 만들어진 기판이다.
각 소자들은 PCB 내에서 전기적으로 연결되어 동작하게 된다.
PCB 소재로는 FR-4 Fiber glass(유리섬유)가 많이 쓰인다.

PCB 기판은 생산이 용이하지만, 미세하고 복잡한 회로를 그려넣기에는 적합하지 않다.
소자들을 연결하기 위해, interposer를 사용하게 된다.
요즘은 칩의 pin 갯수가 엄청 늘어나서, 기판이 이 pin 수를 감당하지 못한다. 그래서 interposer가 필요하다.





반도체기판은 칩과 컴퓨터 메인보드를 연결하는 부품이다. 현재 플라스틱과 같은 유기소재가 널리 쓰인다. 여러 개의 칩이 하나의 반도체처럼 동작하는 이종집적을 위해선 칩과 유기기판 사이 인터포저(중간 기판)가 필요하다.

현재 interposer 기술에는 2가지가 있다.
Organic interposer, Si interposer

Organic interposer:
장점: Si interposer보다 훨씬 싸다.

단점: 쉽게 휘어지고, 표면이 울퉁불퉁해 배선 간격을 좁게 하기 어렵다.

Si interposer:
TSV를 여기서도 쓴다.
성능은 괜찮은데, 공정이 어려워서 너무 비싸다. 설비투자도 많이 필요하다.

그래서, interposer를 쓰면 가격과 성능 사이에서 타협해야 한다.
이걸 빠져나가기 위해 유리기판이라는게 제시됐다.

유리기판을 쓰면, interposer 없이 바로 PCB에 미세한 회로를 그릴 수 있다. 기존 기판은 그렇게 미세한 회로를 못그려서 interposer를 쓴 거였다.

유리기판이 지금 해결해야 할 문제로는, 층간 연결문제가 있다.





유리기판의 장점:
Thermal conductivity가 높아서, 열을 더 효율적으로 방출할 수 있다.
또한 열팽창 계수가 낮아서, 기판의 안정성이 더 높다.

유리는 FR-4보다 수분을 덜 흡수해 신뢰성이 높고 수명이 길다는 특징도 있으며,
고주파에서 낮은 dielectric loss를 가지기에 RF 분야에서 관심받고 있다.


유리기판의 단점:
압력, 충격에 쉽게 깨져 수율이 낮다.
유리기판 공급망, 기술 개발, 공정 최적화가 부족하다.

유리기판 공정에서 필요한 기술은 TGV(Through Glass Via) 기술이다.
Silicon에 구멍 뚫는 기술인 TSV(Through Silicon Via)와 유사하다.


수지다층기판?