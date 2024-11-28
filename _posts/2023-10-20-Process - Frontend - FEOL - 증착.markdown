---
layout: post
title:  "Frontend - FEOL - Deposition"
date:   2023-10-04 19:31:29 +0900
categories: Process
order: 5
---

증착 공정(Deposition)<br>
반도체 칩 하나에는 엄청나게 많은 층(layer)들이 존재한다. 웨이퍼 위에 박막(thin film)을 만들어서 층을 만들어주는 과정이 증착(deposition)과정이다.<br>
<br>
증착 방식에는 2가지가 있다. PVD(Physical Vapor Decomposition), CVD(Chemical Vapor Decomposition)이 있다.<br>
PVD는 source material을 기체로 만들어 웨이퍼 위에 박막이 생기도록 한다.<br>
CVD는 열 CVD, 광 CVD, 플라즈마 CVD 등이 있고, 플라즈마 CVD가 가장 많이 사용되고 있다.<br>
<br>
PVD는 아르곤 원자를 쓰기 때문에, Ar 수 조절로 웨이퍼에 원자 몇 개를 붙일지 결정할 수 있다.<br>
하지만 CVD는 PVD만큼 정확한 원자 수 조절이 어렵다.<br>
<br>
그래서 CVD는 PID제어를 통해 박막으로 만들 원자 수를 조절한다. PID 제어라는게 원래 화학 분야에서 기체 섞다가 나온 제어 방식이다.<br>
<br>
박막을 깔기 전에, 도핑을 통해 source와 drain을 만드는 공정도 증착 공정으로 분류된다.<br>
산화 공정때 도핑해서 만들었던건 n-well과 p-well이고, 여기서 만드는건 source와 drain이라 다른거다.<br>
<br>
Frontend process와 backend process로 반도체 공정을 나눌 때가 많은데, 그 경우 증착 공정까지가 frontend process, 그 이후가 backend process다.<br>


핵심 사업은 박막형성용 핵심 소재인 전구체 생산이다. 반도체 공정에서 반응기 내 여러 종류의 반응기체를 유입해 화학 반응을 일으키는데 이때 원하는 물질의 박막을 웨이퍼에 증착하는 데 사용하는 재료가 전구체다.

반도체의 미세화, 고용량화에 중요한 기능을 한다. 주요 제품은 Si-프리커서, Ti-프리커서, Zr-프리커서, Hf-프리커서 등이다.

Deposition Precursors:
