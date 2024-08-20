---
layout: post
title:  "Digital - Firmware"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 5
---

Firmware는 하드웨어에 내장되어, 하드웨어를 제어하는 소프트웨어다.<br>
Firmware가 손상됐다면, 하드웨어가 멀쩡하더라도 동작을 할 수가 없다.<br>
<br>
Firmware는 과거에는 ROM에 저장됐지만, 최근에는 EEPROM, Flash메모리 등에 저장되기에 업데이트 및 복구가 쉬워졌다.<br>
<br>
<br>
Firmware는 C언어 또는 어셈블리어로 제작한다.<br>
C언어를 컴파일러에 넣으면 어셈블리어가 되고, 어셈블리어를 어셈블러에 넣으면 기계어가 된다.<br>
기계어가 적힌 파일은 1과 0밖에 없는 binary file이다.<br>
<br>
이때, 같은 C언어 코드도 어떤 컴파일러와 어셈블러를 사용하느냐에 따라 다른 결과가 나온다.<br>
Firmware를 저장할 하드웨어에 맞는 컴파일러와 어셈블러를 사용해야 한다.<br>
<br>
개발자가 적은 C언어 또는 어셈블리어 코드 파일이 Source 파일이고,<br>
Source 파일에서 얻어지는 기계어 명령어 집합을 Firmware라 부른다.<br>
하드웨어는 Firmware를 읽고, 해석해서 동작을 행한다.<br>
<br>
<br>
유명한 펌웨어 규격:<br>
BIOS (Basic Input Output System): 16비트 기반 Firmware<br>
UEFI (Unified Extensible Firmware Interface): 64비트 기반 Firmware<br>