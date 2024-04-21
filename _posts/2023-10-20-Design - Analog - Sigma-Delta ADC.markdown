---
layout: post
title:  "Analog - Sigma-Delta ADC"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 4
---

Low oversampling에서는 ADC가 circuit imperfection에 엄청 민감해진다.
32~256정도를 쓰고, 4,8정도가 low oversampling이다.

ADC에서 사용하는 clock이 더 낮아야 interrupt가 덜 걸린다?
interrupt가 뭐지
interrupt map은 또 뭐지




Hard-working LNADC:
지금까지는 ADC 앞단에 많은 amplifier들이 쓰였고, 이 amplifier들이 power를 엄청나게 먹었다.
정작 ADC는 power를 거의 안먹었다.

여기서 amplifier를 안쓰면? 신호가 작으니 SNR이 아주 안좋게 들어올 것이다.
이때는 ADC가 먹는 power를 올려서 SNR을 개선해야 한다.

이러면 또 power가 그게 그거일 수도 있지만, 어쨌든 Amplifier 빼고 ADC만 쓰자는 이야기다.