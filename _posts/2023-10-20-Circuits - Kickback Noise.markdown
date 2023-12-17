---
layout: post
title:  "Kickback Noise"
date:   2023-10-04 19:31:29 +0900
categories: Circuits
order: 2
---

Kickback noise:<br>
Kickback noise는 Latch에서 발생하는 noise다. Latched comparator는 latch 구조를 포함하는 comparator인데, positive feedback 구조라서 analog signal을 digital signal로 바꾼다.<br>
<br>
예를 들어, input이 Vref보다 아주 조금 커도 그 차이가 positive feedback에 의해 증폭돼서 출력이 VDD가 되고, input이 Vref보다 아주 조금 작아도 Output은 VSS가 된다. Positive feedback은 차이가 커지는 방향으로 작용하기 때문이다.<br>
<br>
이 positive feedback 때문에, input 전압은 조금만 변해도 output 전압은 크게 변할 수 있다. 이 경우 latch 안 노드들의 dv/dt가 상당히 크다. 이 커다란 dv/dt가 parasitic capacitance에 Cdv/dt만큼 전류가 흐르게 만든다.<br>
<br>
Input 전압을 인가해주는 회로의 Rout이 0이라면 전류가 흘러들어와도 input 전압에 영향이 있지 않았겠지만, Rout이 0이 아니면 이 전류에 의해 input 전압이 달라진다. 이 현상이 kickback noise다.<br>
빠르고 전력 효율이 좋은 comparator일수록 kickback noise가 크게 생긴다.<br>
<br>
Kickback noise 해결방법:<br>
1\. Preamplifier를 comparator 앞에 붙인다.<br>
근데 이러면 preamplifier가 power를 먹어 전력효율이 떨어진다.<br>
2\. Differential pair의 drain들에 스위치를 달고, latch 전압이 바뀌는 동안 스위치를 열어서 전압 변화가 캐패시턴스에 전달 안되게 한다<br>.
이때는 스위치 열면 IDS=0이 되어 MOSFET들이 Triode region에 처박힌다. 그리고 Drain 전압이 어디에도 연결되지 않아서 맘대로 날뛸 수 있다.<br>
3\. Differential Pair의 gate들에 스위치를 달아서 input을 sampling해 넣ㄴ느다. 이러면 input에 의한 dV/dt가 전류를 만들 때 스위치가 열려있어 영향이 없다.<br>
하지만 스위치 닫히는게 어차피 input에 영향을 준다.<br>
<br>
몇가지 방법이 더 있다고는 하는데, 일단 kickback noise가 뭔지는 확인했으니 다음에 더 알아보자. 내용출처는 ‘Kickback noise reduction techniques for CMOS latched comparators’<br>
