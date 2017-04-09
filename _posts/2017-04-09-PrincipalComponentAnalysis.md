---
layout: post
title: Principal Component Analysis
description: "Principal Component Analysis"
headline: "Principal Component Analysis"
categories: MACHINELEARNING
tags: 
  - Machine Learning
  - PCA
comments: false
mathjax: true
featured: true
published: true
---

## Principal Component Analysis

- PCA는 기본적으로 특징추출 기법이다.
- 정보 손실을 최소화 하면서  M차원 데이터를 m차원으로 차원 축소하는 것
- 실제 단계
	1. 각 feature의 평균이 0, 표준편차가 1이 되도록 feature normalization
	2. feature의 공분산 행렬 구하기
	3. Singular Vector Decomposition을 통해 공분산의 Eigenvectors와 Eigenvalue 구하기 
		- Orthogonal Eigenvectors * Diagonal Eigenvalues * Orthogonal Eigenvectors로 분해됨
	4. Eigenvalue값이 큰 Eigenvector순으로 제 1주성분, 제2주성분,...순서가 매겨짐
	5. 몇 개의 주성분을 선택할지는 Scree plot을 그려서 판단한다.
		- x축 Eigenvector (PC1, PC2, PC3, ..)
		- y축 각 주성분에 대응하는 Eigenvalue
		- Elbow point 지점까지의 주성분 개수 선택 
	6. 선택된 주성분을 축으로 span하는 공간에 데이터를 projection

## PCA vs Linear Regression
- PCA
	- Unsupervised
	- 모델-데이터 간 수직 거리 최소화

- Linear Regression
	- Supervised
	- 종속변수-모델 간 거리 최소화
	- 최소화하는 대상이 PCA와 다르기 때문에 Least Squared 방법으로 구한 리그레션 모델은 항상 PC1보다 기울기가 낮다. 


<p align="right"> Yeonjung Hong <p>
