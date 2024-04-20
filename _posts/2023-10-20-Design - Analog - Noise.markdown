---
layout: post
title:  "Analog - Noise"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 3
---

7번 data summation을 하는데, 매번 8code noise가 있다면:
summation한 data의 noise는 8sqrt7 = 21code. 8 7개를 rms한거다.
모두 양수였으면 그냥 평균냈겠지만, 음수 양수 섞이면 rms해야 한다.

물론, 각 noise에 correlation이 없다는걸 가정했기에 rms로 구한거다.