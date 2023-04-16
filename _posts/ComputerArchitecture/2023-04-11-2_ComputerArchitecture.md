---
date: 2023-04-11 09:30
layout: single
title: "[컴퓨터 구조] L02.Number Representation"
categories:
  - ComputerArchitecture
  - CS
---

## Bits can be anything

- Data Input: Analog -> Digital
	- 현실 세계는 아날로그
	- 아날로그 정보를 가져오기 위해 다음 두가지가 필요하다.
		1. Sample: 일정 간격마다 어떤 값인지 알아야한다.
		2. Quantize
- 문자, 논리 변수, 색, 감정 등 모든 것에 비트 패턴을 갖게 해서 디지털화할 수 있다.


## Conversions

- Decimal(10진법)
	- 3271 = 3271<sub>10</sub> = (3x10<sup>3</sup>) + (2x10<sup>2</sup>) + (7x10<sup>1</sup>) + (1x10<sup>0</sup>) 
- Binary(2진)
	- 1101<sub>2</sub> = (1x2<sup>3</sup>) + (1x2<sup>2</sup>) + (0x2<sup>1</sup>) + (1x2<sup>0</sup>) = 13
- Hexadecimal(16진법)
	- 0, 1, 2, 3, 4, 5, ,6, 7, 8, 9, A, B, C, D, E, F
	- 0xA5 = A5<sub>16</sub> = (10x16<sup>1</sup>) + (5x16<sup>0</sup>) = 160 + 5 = 165
- 2진법과 16진법의 전환
	- 2진수 -> 16진수: 16진수 하나의 숫자는 4비트의 용량을 가진다. 만약 2진수의 자릿수가 4의 배수가 아니면 왼쪽에 0으로 padding을 채운다.
	- 16진수 -> 2진수: 왼쪽에 padding이 있으면 제거한다.
- 4Bits = 1 Nibble = 1 Hex Digit = 16개의 표현 가능
- 8Bits = 1 Byte = 2 Hex Digit = 256개의 표현 가능 
	- 색상의 표현에서 사용된다.(R:0~255, G:0~255, B: 0~255 -> <span sytle="color:red">D0</span>D0367F)