---
layout: post
title:  "Analog - Stability Analysis"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 3
---

Feedback이 있는 시스템에서는, 출력에 비례하는 feedback이 입력에 들어오게 된다.<br>
이 feedback의 크기와 위상에 따라 시스템이 안정해질 수도 있고, 불안정해질 수도 있다.<br>
<br>
회로 내의 L 또는 C 성분에 의해, feedback





시스템이 얼마나 안정한지 확인하는 Stability Analysis를 해야 한다.


Phase Margin:


Phase margin이 60도보다 작아지면 보통 peak가 생기고, 45도보다 작아지면 보통 overshoot 후 settle한다.
그래서 보통 설계할때는 45도 이상으로 phase margin이 나오게 한다.

Gain Margin:
phase가 180도 뒤집혀 feedback으로 들어오는 주파수에서의 Gain이다.