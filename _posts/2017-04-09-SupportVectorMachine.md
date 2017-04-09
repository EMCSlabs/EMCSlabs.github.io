---
layout: post
title: Support Vector Machine
description: "Support Vector Machine"
headline: "Support Vector Machine"
categories: MACHINELEARNING
tags: 
  - Machine Learning
  - SVM
comments: false
mathjax: true
featured: false
published: true
---

## Support Vector Machine as Maximum Margin Classifier


- SVM은 기본적으로 선형 2-클래스 분류기이다.

- 일반적인 선형 모델과는 다르게 단순히 오류를 최소화 하는데 그치는 것이 아니라 그 중에서도 가장 일반화 능력이 좋은 분류 모델을 찾아준다.

- Posterior Probability를 알려주지 않고 클래스 분류만 해준다.

- How?
	- Decision Boundary로부터 그와 가장 가까운 데이터 포인트 (=support vectors) 간의 수직 거리(=margin)가 최대가 되도록 한다.
	- 이는 다음과 같은 목적함수로 표현된다. <br>

		- 조건<br>
y_i(\mathbf{w}\cdot\mathbf{x_i} - b) \ge 1,\text{ for all } 1 \le i \le n.<br>

		- 목적함수<br>
\arg\min_{(\mathbf{w},b)}\frac{1}{2}\|\mathbf{w}\|^2 <br>


		- Lagrange Multipliers 도입하여 하나의 조건부 최적화 문제로 표현<br>
\arg\min_{\mathbf{w},b } \max_{\boldsymbol{\alpha}\geq 0 } \left\{ \frac{1}{2}\|\mathbf{w}\|^2 - \sum_{i=1}^{n}{\alpha_i[y_i(\mathbf{w}\cdot \mathbf{x_i} - b)-1]} \right\} <br>

- 조건부 최적화 문제를 푸는 방법: Karush-Kuhn-Tucker 조건 이용

## Linearly nonseparable SVM
- 2차원 상에서 온전한 선형 분리가 불가능하지만 여전히 선형 분리 방법을 사용하고자 할 때
- Trade-off 관계를 지니는 다음 두 조건을 만족하도록 식을 세운다.
	- Margin을 최대화
	- Margin 내부에 속하거나 아예 결정 경계를 넘어가는 데이터의 수를 최소화 (경계도 지키면서 Margin 밖에 있는 데이터가 좋은 데이터)
- 두 조건의 적용 비중을 매개변수를 통해 설정할 수 있다.

## Nonlinear SVM

- 데이터가 2차원 상에서 선형 분리가 불가능하더라도, 고차원 특징 공간에서는 선형분리 가능하다는 점을 활용
	- 시각화는 2차원 혹은 3차원에 한정되기 때문에 비선형 분리가 된 것처럼 표현되더라도 실제로는 보다 고차원 공간에서 선형 분리가 일어난 것.

- 선형 분리가 가능한 고차원으로 데이터를 매핑하는 것이 바로 Kernel 함수
	- 특징 벡터들 간의 내적은 어느 차원이나 동일하다는 사실 덕분에 다른 차원으로의 매핑 가능
	- 주로 쓰이는 커널: Polynomial, Radial Basis Funciton, tanh

- M-class SVM
	- 1 vs 1 
		- M(M-1)/2개의 SVM
		- 느림
	- 1 vs M-1
		- M개의 SVM
		- 불균형적이지만 너무 느린 1 vs 1 방법보다 선호



<p align="right"> Yeonjung Hong <p>
