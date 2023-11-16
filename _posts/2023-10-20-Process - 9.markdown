---
layout: post
title:  "웨이퍼 종류"
date:   2023-10-04 19:31:29 +0900
categories: Circuits
---

웨이퍼에는 3가지가 있다.<br>
1\. Bulk Polished Wafer<br>
2\. Epi Silicon Wafer,<br>
3\. SOI Wafer<br>
Bulk polished silicon wafer는 비정질(Amorphous, 원자들 사이 거리에 특별한 규칙이 없음) 고체라서, 전자 이동 속도가 결정질(Crystalline)에 비해 느리다. 그래서 빠르게 작동해야 하는 CMOS등에는 사용하지 않고, DRAM이나 NAND Flash같은 메모리반도체에 쓰인다.<br>
<br>
Epi Silicon wafer는 bulk wafer 위에 crystalline silicon으로 되어 있는 epitaxial layer가 있는 구조다. Crystalline 구조가 있기 때문에 전자 이동속도가 bulk wafer보다 빠르다. 그래서 CMOS 이미지센서 등 속도가 빨라야 하는 분야에 쓰인다. 대신, 가격은 bulk wafer보다 비싸다.<br>
<br>
SOI wafer의 SOI는 Silicon on Insulator의 약자다. 말 그대로 bulk wafer 위에 insulator가 있고, 그 위에 다시 silicon이 있는 형태다. 이 구조는 parasitic capacitance를 줄이고 switching speed를 올려서 leakage current를 줄여야 하는 회로나 switching speed가 빨라야 하는 회로, 또는 parasitic capacitance가 적어야 하는 RF 회로 등에 쓰인다. 가격은 얘가 제일 비싸다.<br>
<br>
IC 회로에서는 Latch-up이라는 현상이 생길 때가 있다. 웨이퍼 안에 박힌 p,n 접합들이 PNP 또는 NPN 트랜지스터처럼 동작하는 PNPN구조, 즉 사이리스터 구조를 만들어 전압이 이상하게 걸리면 short가 되어버리는 현상이다.<br>
<br>
Bulk wafer가 아닌 epi, soi wafer를 쓰는게 latch-up 방지에도 도움이 된다.<br>
<br>
앞에 적었던 대로, 웨이퍼 직경은 8인치(200mm) 아니면 12인치(300mm)다. SK실트론 사이트 가보면 200mm Epi wafer로는 Analog PMIC, Power discrete, CMOS Image Sensor를 만들고, 300mm Epi wafer로는 MPU, CMOS Image Sensor, Logic(Driver IC)을 만든다.<br>
<br>
MPU는 CPU를 소형화한건고, MCU는 컴퓨터를 소형화한거다.<br>
MPU: Micro Processing Unit,<br>
MCU: Micro Controller Unit<br>
<br>
CMOS Image Sensor는 CIS라고 많이들 적는다.<br>
<br>
원래 Silicon Wafer의 두께는 600um~900um인데, 패키징할때 백그라인딩이라 해서 두께 100um 수준까지 갈아놓는다. 근데 너무 얇아지면 기계적 stress로 인해 휘어지다가 전기적 특성이 바뀔 수 있다. 그래서 너무 깎아버리면 안된다.<br>



