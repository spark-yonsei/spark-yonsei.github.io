---
layout: post
title:  "Cascode"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 4
---

folded cascode의 장점:
더 큰 voltage swing 가능 -> Common mode input의 범위 증가

저전압 설계가 쉬움
traditional cascode는 headroom이 부족하니까

improved input-output isolation
coupling이 없으니 원하지 않는 feedback같은게 안생긴다

reduced Miller effect
input/output 사이 capacitive coupling이 없으니,
Capacitance가 없어 Miller effect가 줄어든다. 따라서 BW가 넓어진다

folded cascode의 input TR에는 전류가 덜 흐르기에,
flicker/thermal noise가 더 작다



folded cascode의 단점:
Rout이 traditional cascode보다 작아서 gain이 작다
power 소비가 더 많다
설계가 더 복잡하다
면적을 더 많이 먹는다

