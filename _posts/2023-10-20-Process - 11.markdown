---
layout: post
title:  "Salicide, CMP, WPE"
date:   2023-10-04 19:31:29 +0900
categories: Process
---

금속 대신 Polysilicon을 쓰는 이유: 고온에 잘 버텨서 공정이 쉽다. 그래도 저항이 더 작은건 금속이기 때문에, 어떻게든 금속을 쓸 때도 있다.<br>
<br>
금속 배선 공정에서 가장 먼저 실시하는 salicide는 self-alignment와 silicide의 합성어다. Silicide는 metal layer와 silicon layer의 contact 저항을 줄이기 위해 사용되는 물질이고, TI, Co, Ni, W 등이 사용된다. Contact 저항 줄여야 하는 이유는 Schottky contact, ohmic contact를 보면 안다.<br>
<br>
이거 관련 얘기는 그림 있어야될것같아서, 나중에 그림 넣으면서 같이<br>
<br>
이 얘기를 왜 했냐면, Metal이랑 Silicon을 그냥 붙여놓으면 Schottky contact가 되기 때문이다. 그래서 만나는 접합 부분에 저항이 낮은 물질을 끼워서 ohmic contact를 만들어줘야 한다.<br>
<br>
그 저항 낮은 물질이 silicide인데, 보통 Ti를 쓴다. Ti는 Si랑은 반응 잘 하는데 STI에 쓰이는 SiO2랑은 반응을 안한다는 장점이 있다.<br>
<br>
그래서 이 Ti를 어떻게 Si 위에 올릴 것인가? 처음부터 Ti와 Si를 반응시켜 TiSi를 만들고 이걸 웨이퍼 위에 증착하는 방법도 있지만, 그렇게 하면 또 마스크, 포토공정, 식각공정을 다 해야 한다. 웨이퍼 전체에 뿌리는게 아니고 특정 부분에만 올려놔야 하니까.<br>
<br>
그래서 증착 대신 사용하는 공정이 salicide 공정이다. 그냥 Si 위에 Ti를 올려놓고 Annealing(가열)해주면 Ti가 Si 속으로 들어간다. 그래서 웨이퍼에 먼저 Polysilicon을 올려놓고 silicide를 씌운다.<br>
Annealing 온도는 500~900도고, 가열할때 RTA Annealing이라 해서 레이저로 가열하는 방식을 쓴다. RTA: Rapid Thermal Annealing
어쨌든 이렇게 Salicide 공정을 통해 저항을 줄일 수 있다.<br>
<br>
Sheet 저항도 그림 있어야 할 것 같아서 나중에 넣는다.<br>
<br>
그 다음에는 웨이퍼 위에 PMD(Pre Metal Dielectric)라는 metal과 polysilicon 사이 절연막으로 사용되는 물질을 올릴건데, 그 전에 일단 질화막을 한번 깔고 올린다. 이 질화막은 나중에 etch stop layer로 쓰일 것이다.<br>
<br>
그 뒤에는 PMD에 포토공정을 해서 contact 박을 곳들 다 날려버린다. 날리는 깊이는 etch stop layer 까지다. 뚫어놓은 contact용 구멍에는 일단 sputtering 방식으로 Ti를 얇게 증착시키고, 그 뒤 텅스텐으로 채운다. 그 다음엔 CMP(Chemical Mechanical Polishing) 공정을 통해 위를 평평하게 만든다.<br>
<br>
이 위에다가 IMD1(Intra_Metal Dielectric 1)을 올리고, 또 via 1 만들 곳 구멍내고, 또 텅스텐 넣고 또 평평하게 만든다. 이때 contact 바로 위에 또 via 1을 만드는건 보통 하지 않는다. Contact와 via든, via 끼리든 하지 않는다.<br>
<br>
Contact : 웨이퍼와 metal1 연결<br>
Via N: Metal N과 Metal N+1 연결<br>
<br>
이렇게 Metal을 계속 쌓기 때문에, CMP 공정으로 각 층을 평평하게 해주지 않으면 그 위로 metal을 쌓을 때 난장판이 된다.<br>
<br>
옛날에는 Metal 2~3 정도가 최대였지만, 요즘은 심하면 Metal 9까지도 가기 때문에 CMP 공정이 아주 중요하다. 옛날에는 이런거 안해서 못쌓았다.<br>
<br>
Well Proximity Effect:<br>
앞에서 말했던 내용들 중 웨이퍼에 well을 만드는 내용이 있었다. Substrate 위에 well을 만들 곳을 정해놓고, 그 외 영역을 photoresist로 덮어버린 후 이온을 쏴서 도핑하는 방식이었다.<br>
<br>
근데 이러면 문제가, 끄트머리에서 튕겨나온 이온들 때문에 well의 가장자리는 원래 의도했던 수치보다 더 높게 도핑된다.<br>
<br>
그래서 well 끄트머리에 설치된 MOSFET과 안쪽에 설치된 MOSFET은 다르게 동작할 수 있다. Well의 Doping 농도가 다르기 때문이다.<br>
<br>
이 문제를 해결하기 위해, layout 만들때 Well 영역을 일부러 조금 더 길게 잡을수도 있고, Dummy Transistor를 가장자리에 끼워서 해당 효과를 피할 수도 있다.<br>
<br>
근데, 그냥 중요한 MOSFET이면 가장자리에서 멀리 떼어놓는게 좋다.<br>
