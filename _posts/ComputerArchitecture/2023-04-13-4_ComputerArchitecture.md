---
date: 2023-04-13 13:36
layout: single
title: "[컴퓨터 구조] L04. Introduction to C, Part 2"
categories:
  - ComputerArchitecture
  - CS
tags:
  - cs61c_"Great Ideas in Computer Architecture"
---
### Pointers
- 어떤 변수의 주소를 값으로 가지고 있는 변수
- pointer syntax

```c
int *p; // 컴파일러에게 변수 p는 어떤 정수의 주소값이라고 알려줌
 
p = &y; // 컴파일러에게 y의 주소를 p에게 할당하라고 함(&는 address operator)

z = *p; // 컴파일러에게 포인터 p가 가리키는 주소에 있는 값을 z에 할당하라고 함(dereference operator)

```