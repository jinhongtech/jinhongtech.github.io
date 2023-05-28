---
date: 2023-04-11 08:35
layout: single
title: "[컴퓨터 구조] L01.Course Introduction"
categories:
  - ComputerArchitecture
  - CS
tags:
  - cs61c_"Great Ideas in Computer Architecture"
---

## Great Ideas in Computer Architecture

1.  Abstraction (Layers of Representation/Interpretation)
    -   복잡한 자료, 모듈, 시스템 등에서 핵심적인 개념 또는 기능을 간추려 내는 것
    -   High level language인 C언어의 간단한 코드를 몇 줄 적으면 자동으로 컴퓨터는 많은 양의 assembly code를 생성해주는데 우리는 이를 배제하고 생각할 수 있다.
2.  Moore’s Law
    -   반도체 안의 트랜지스터 수는 2년마다 2배로 증가한다.
    -   시간에 지남에 따라 증가하는 속도는 줄어들었지만 여전히 계속되고 있다.
3.  Principle of Locality/Memory Hierarchy
    -   데이터로부터 멀어질수록 데이터를 찾는 시간이 오래가 걸린다.
    -   Processor chip, Dram chip, SSD, HDD 순서대로 왼쪽으로 갈수록 읽는 속도는 빨라지지만 가격이 높아지고 적은 용량을 가진다.
4.  Parallelism(병렬성)
    -   병렬처리를 해서 무조건적인 성능이 향상되는 것이 아니다.
    -   암달의 법칙: 성능(프로세스 완료 시간)은 CPU 코어와 비례적으로 증가하는 것이 아니라 순차적으로 수행되어야 하는 프로그램의 비율에 따라 제한적으로 증가한다.
5.  Performance Measurement & Improvement
    -   어플리케이션을 하드웨어에 맞게 조정하기 위해 지역성, 병렬처리와 하드웨어의 특징을 사용
    -   Latency: 문제 설정 시간, 프로그램 수행 시간 등 작업 완료 시간을 고려한다.
6.  Dependability via Redundancy
    -   하나의 프로그램 오류가 시스템 전체의 오류로 이어지진 않는다.
    -   예를 들어 데이터 센터 중 하나가 고장나도 다른 독립적인 데이터 센터에 의해 서비스는 여전히 유지될 수 있다.




