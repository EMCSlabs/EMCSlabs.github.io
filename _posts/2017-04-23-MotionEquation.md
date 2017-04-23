---
layout: post
title: Motion Equation
description: "Motion Equation"
headline: "Motion Equation"
categories: Math
tags: 
  - Math
comments: false
mathjax: true
featured: false
published: true
---

## Motion Equation

- Mass*x'' + Friction*x' + gravity*x=F
- 풀이: [mass, friction, gravity] * [x'' x' x]' = F
    <=> 질량, 마찰, 중력이 가속도, 속도, 거리와 이루는 내적 = 시스템
- 목적: 시스템 F를 설명할 수 있는 거리, 속도, 가속도를 구하기
- Ax = F형태의 선형 방정식 문제로 바꾸어 생각하면 푸는 과정은 다음과 같다. 
    1. homogeneous solution 구하기
        - Ax=F=0 (equilibrium 즉, 외부 힘이 가해지지 않은 상태)에서의 x를 구한다. 
        - A의 nullspace를 구하기?!
    2. particular solution 구하기
        - Ax=F의 particular solution 구하기
            - 적분 통해 구할 수는 있으나 너무 어려움
            - 차선책
                - 시스템 F가 A와 x로 decompose되어 있다는 점을 고려하면 결국 x도 F의 형태와 유사하게 닮아있을 것이라고 추측
                - 자연계에서 F의 양상은 sin, cos, e 등과 닮아있음. 
                - 무한히 존재하는 particular solution 중에 sin, cos, e 등이 분명 존재할 것
                - 적절한 것을 particular solution으로서 상정
    3. 1,2를 종합하여 complete solution 구함
            


<p align="right"> Yeonjung Hong <p>
