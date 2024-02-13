---
layout: post
title:  "스마트폰 - ToF 센서"
date:   2023-10-04 19:31:29 +0900
categories: Market
order: 5
---

ToF(Time of Flight)는 3D 센싱의 한 방법이다.
3D 센싱에는 3가지 방식이 있다.<br>
1\. Stereo Vision: 카메라 2개면 거리 재기 가능<br>
2\. Structured Light: 패턴 있는 빛을 뿌려서 반사 패턴을 본다.<br>
3\. ToF<br>

다른 카메라들은 광원이 없는데, ToF 카메라는 광원에서 빛을 쏜다. 우리가 하는건 거기 들어가는 VCSEL(Vertical Cavity Surface Emitting Laser, 웨이퍼 수직 방향으로 레이저 쏘는 다이오드) 구동 장치다.<br>
<br>
ToF 카메라 결과로 amplitude, depth 정보가 나온다.<br>
ToF 스위칭 주파수가 100MHz라서 RF Radiation noise가 심하다.<br>

애플 안면인식은 ToF 센서로 3D 센싱을 하는 방식이다.<br>

이 중 ToF에 대해 알아볼건데, ToF에는 다시 2가지 방식이 있다.
dToF: 아이폰, 로봇청소기, 3D지도 만드는 차 위에 있는거<br>
iToF: 아이폰 외 모든 핸드폰<br>
<br>
<br>
iToF: 약하게 여러 개 point에 뿌린다. 멀리는 못가지만, 뿌리는 범위가 넓어서 해상도가 높다. 멀리 못간다는게, 5m도 못가는 수준이다. 삼성전자 iToF는 4500개 point를 뿌린다.<br>
<br>
dToF: 강하게 몇 개 point에 뿌린다. 멀리 갈 수 있지만, 중간에 비는 부분들은 알고리즘으로 채워넣어야 한다. 애플 dToF는 600개 point를 뿌린다.<br>
<br>



iToF, dToF 쏘는건 물총이랑 비슷하게 생각하면 된다. 분무기가 iToF, 물총이 dToF다.<br>
ToF에서 빈 곳 채우는 기술이 삼성이 많이 딸려서, ToF 파워는 삼성꺼가 더 센데도 애플꺼가 더 멀리간다.<br>
<br>
iToF 센서와 dToF 센서는 다르게 생겼는데, 이 중 dToF 센서는 작게 만들기 어렵다.<br>
dToF 센서는 소니에서 만드는데 애플과 독점 계약이 되어 있다.<br>
dToF 센서는 위에서 말했듯 빈칸을 채워야 해서 소프트웨어 처리가 많이 필요하다. 그래서 이게 되는 애플만 dToF, 나머지는 iToF를 쓴다.<br>
<br>
아까 iToF는 5m도 못간다고 했는데, AR, VR을 하고 싶다면 sensing 가능한 거리가 5m는 넘어야 할 것이다. 그래서 요즘은 많이들 dToF를 검토한다고 한다.<br>
<br>
옛날에, 5G 활성화되면 AR, VR 떡상한다는 얘기가 있었지만 아니었다. 그래서 삼성전자도 관심을 껐었는데, 아이폰 13프로부터 dToF센서가 들어가서 다시 관심을 갖고 있다고 한다. 그래도 일단 S24까지는 들어갈 계획 없다고 한다.<br>
<br>
<br>
dToF는 아이폰 외에도 형체 인식하는 곳에 쓰인다. 매장 들어가는 사람 세는 곳 등. 이러면 보안상 좋다. 형체만 보이고 사람은 안보이니까.<br>
<br>
라이다의 핵심 원리가 dToF다.<br>
<br>
dToF: direct Time-of-Flight, iToF: indirect Time-of-Flight<br>
<br>
카메라만 있어도 초점 잘 잡을 수 있지만, 시간이 조금 걸린다. 하지만 ToF센서가 있다면 거리를 알 수 있으니 바로 초점을 잡을 수 있다.<br>
<br>

삼성전자는 ToF 센서를 제품들에 잠시 넣다가 지금은 안넣는 상황인데, 애플을 따라가기 위해 곧 다시 넣을 것으로 보인다. 올해 6월에는 애플에서 VR 안경이 나온다.<br>

ToF 일본 제조사: Kokyo, Hokuyo, Jepico, Sick, Opex<br>