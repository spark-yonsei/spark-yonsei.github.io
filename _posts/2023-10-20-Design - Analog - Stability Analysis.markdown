---
layout: post
title:  "Analog - Stability Analysis"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 3
---

Feedback이 있는 회로에서는, 출력에 비례하는 feedback이 입력에 들어오게 된다.<br>
이 feedback의 크기와 위상에 따라 시스템이 안정해질 수도 있고, 불안정해질 수도 있다.<br>
<br>
feedback이 입력을 상쇄하는 위상으로 돌아오면 회로가 안정하지만,<br>
feedback이 입력에 더해지는 위상으로 돌아오면 feedback의 크기를 확인해야 한다.<br>
<br>
feedback이 입력보다 작아져서 돌아온다면, 입력에 더해지는 위상으로 돌아와도 회로가 안정하다.<br>
하지만 입력보다 커져서 돌아오면서, 입력에 더해지는 위상으로 돌아온다면 회로가 불안정하다.<br>
feedback의 크기가 입력과 동일해도, 입력에 더해지는 위상으로 돌아온다면 회로가 불안정하다.<br>
<br>
불안정한 회로는 통제가 불가능하니, 회로 설계자 입장에서 불안정한 회로는 반드시 피해야 하는 상황이다.<br>
그래서 회로가 얼마나 안정한지 확인해야 하고, 여기에 쓰이는 지표가 Phase Margin과 Gain Margin이다.<br>
<br>
<br>
회로가 저항으로만 이루어져 있다면, 입력 주파수가 변해도 feedback의 크기와 위상이 변하지 않는다.<br>
하지만 회로 내의 L 또는 C 성분에 의해 feedback의 크기가 위상이 변해,<br>
어떤 주파수에서는 안정하던 회로가 다른 주파수에서는 불안정해질 수 있다.<br>
<br>
<br>
Phase Margin [deg]:
Feedback의 크기가 입력과 같아지는 주파수에서,<br>
Feedback의 위상이 입력과 어긋나 있는 정도를 뜻한다.<br>
<br>
Phase Margin이 180도면 입력과 feedback의 위상이 완전히 어긋나 있다는 뜻이다.<br>
따라서 회로가 안정하다.<br>
<br>
Phase Margin이 0도면 입력과 feedback의 위상이 완전히 일치한다는 뜻이다.<br>
따라서 회로가 불안정하다.<br>
<br>
Phase Margin이 너무 크면 회로 동작이 느리다는 뜻이고,<br>
Phase Margin이 너무 작으면 회로의 overshoot가 심각하다는 뜻이다.<br>
회로 설계시에는 회로가 그 사이 적절한 Phase Margin을 갖게 해야 한다.<br>
<br>
Gain Margin [dB]:<br>
Feedback의 위상이 입력의 위상과 완전히 일치하는 주파수에서,<br>
Feedback의 크기를 뜻한다.<br>
<br>
Gain Margin이 아주 큰 값이라면 입력에 아주 작은 feedback이 더해진다는 뜻이다.<br>
따라서 회로가 안정하다.<br>
<br>
Gain Margin이 0dB라면 입력에 입력과 같은 크기의 feedback이 더해진다는 뜻이다.<br>
따라서 회로가 불안정하다.<br>
<br>
<br>
Feedback이 없는 회로에서는 Stability Analysis를 할 필요가 없다.
