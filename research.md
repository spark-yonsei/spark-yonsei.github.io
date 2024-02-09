---
layout: page
title: Research
permalink: /research
---
<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>


I have research experience in signal processing, electromagnetics and circuit design.
<br>
I am looking for opportunties to design an IC.<br>

학부때는 이용식 교수님 연구실에서 RF쪽을 했다
고주파쪽에 관심이 있었고, 광학쪽에도 관심이 있었다
수학 등 신호처리, 통신도 좋아했다

신용준 교수님 연구실에서 시간주파수해석+광케이블 연구를 하게 됐다
그러나 fault modelling이 너무 어려워 논문을 내지 못했다

군대 문제를 해결해야 했기에 취업 준비를 시작했다
석사 전문연은 중소기업 위주인데, 광학, RF쪽 하는 중소기업이 많지 않았다

아날로그 회로면 RF와 사실상 같은 분야라고 생각해 아날로그 회로쪽으로 취업을 하게 됐다. 동운아나텍이다

<br>
### Time-Frequency Analysis
Traditional frequency analysis has its background in Fourier Transform.<br>
$$S(f) =\displaystyle \int_{-\infty}^{\infty}s(t) \, e^{-j2 \pi ft} \, dt$$<br>
<br>
하지만 주파수가 여러개인 신호에서는 어떤 주파수가 먼저 존재했는지 알 수가 없다.<br>
그래서, time domain에서 Window를 움직이며 Fourier Transform을 하는 STFT가 있다.<br>
Window의 위치가 시간을 말해줄 것이고, STFT의 결과가 그 시점의 주파수 성분을 알려줄 것이다.<br>
$$STFT_s(\tau,f) =\displaystyle \int_{-\infty}^{\infty}s(t) \, w(\tau - t) \, e^{-j2 \pi ft} \, dt$$<br>
<br>
근데 STFT에도 문제가 있다. Window의 영향이 STFT 결과에 나타나는 것이다.<br>
Window와 Signal이 Convolved되기 때문에 나타나는 문제다.<br>
<br>
Window에 의한 왜곡도 없으면서, 각 시간별로 주파수 성분을 보여줄 수 있는 방법으로 Wigner-Ville Distribution이 있다.<br>
$$WVD_s(t,f) =\displaystyle \int_{-\infty}^{\infty} s\left (t - \frac{\tau}{2}\right ) \, s^*\left (t + \frac{\tau}{2}\right ) \, e^{-j2 \pi f\tau} \, d\tau$$<br>
<br>
하지만 WVD는 Cross-term에 의해 또 문제가 생긴다.<br>
그래서 적절한 LPF(kernel)을 통해, auto-term을 보존하면서 cross-term을 제거한다.<br>
$$TFD_s(t,f) =\displaystyle \int_{-\infty}^{\infty} s\left (t - \frac{\tau}{2}\right ) \, s^*\left (t + \frac{\tau}{2}\right ) \, e^{-j2 \pi f\tau} \, d\tau$$<br>
<br>
kernel은 application specific이다. 상황에 맞는 kernel을 통해 최적의 time-frequency plot을 얻는다.<br>
<br>
### TFDR (Time-Frequency Domain Reflectometry)
test
### OTFDR (Optical Time-Frequency Domain Reflectometry)
test



이 뒤로는 회로, 코딩 이야기 해야 할듯