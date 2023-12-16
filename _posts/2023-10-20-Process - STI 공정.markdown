---
layout: post
title:  "STI 공정"
date:   2023-10-04 19:31:29 +0900
categories: Process
---

STI(Shallow Trench Isolation) Module:<br>
웨이퍼의 n-영역과 p-영역을 분리하는 isolation 역할을 한다.<br>
<br>
STI 공정을 쓰면 chip size를 작게 할 수 있다. 원래 PN junction을 분리하려면 거리가 필요했는데, STI로 isolation을 하면 거리 없이도 isolation을 할 수 있다. 결과적으로, 회로의 집적도를 높일 수 있다.<br>
<br>
옛날에는 P영역 N영역 사이에 SiO2를 대충 끼웠는데, bird’s beak 현상이 발생해서 STI 모양으로 바꿨다고 한다. Bird’s beak 현상은 SiO2가 양 옆을 밀어내며 gate electrode 아래까지 밀고 들어와 채널에 영향을 주는 현상이다.<br>
<br>
그래서 요즘은 trench 모양으로 만들긴 하지만, 그렇다고 SiO2가 양옆을 안밀어내는건 아니다. STI의 SiO2에 의해 반도체 영역이 stress를 받는걸 STI stress effect라 한다. 이 effect를 다른 회사들은 모델링 안하는데, 삼성전자 LF6S에서는 한다.<br>
<br>
STI Stress에 의한 영향을 방지하려면, active region을 꽉 채워놓거나 더미로라도 채워놓는다.<br>
<br>
옛날에 STI 대신 쓰던 Isolation 기술 이름은 LOCOS(Local Oxidation of Silicon)다.<br>
<br>
STI 말고 DTI(Deep Trench Isolation) 공정도 있다. DTI는 STI보다 훨씬 깊게 파는 공정인데, 옆 소자와 분리돼야 SNT이 증가하는 이미지 센서 등에 사용된다. 이미지 센서에서 Cell들을 분리하는 기술은 ‘ISOCELL’ 기술이라 불린다. Isolation + Cell<br>
<br>
STI Stress를 고려해서, layout시 바깥쪽에 source가 가도록 한다. 또는 양쫓 끝에 dummy transistor를 넣는다. Finger로 구성할 때 이야기고, N은 Vss 쪽으로, P는 VDD쪽으로 갈 가능성이 높아서 그렇다. 고 하는데 무슨 뜻인지는 알아봐야 한다.<br>
