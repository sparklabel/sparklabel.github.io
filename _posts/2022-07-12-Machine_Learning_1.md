---
title:  "[ML/DL] 인공지능 개요"
excerpt: "Intro. of Artificail Inteligence"

use_math: true                    # latex 적용

toc: true                         # 목차
toc_sticky: true                  # 목차 사이드바 고정
  
published: true                   # 배포 여부

categories:
  - ML_DL
tags:
  - AI
  - Machine Learning
  - Deep Learning
last_modified_at: 2022-07-15T10:30:00+09:00
sitemap:
  changefreq: daily
  priority: 0.8
---

## 인공지능(AI) 
- ML/DL 의 과거이자 미래
- AI > ML > DL

>Source: [Nvidia](https://blogs.nvidia.com/blog/2016/07/29/whats-difference-artificial-intelligence-machine-learning-deep-learning-ai/)  

<center>
<img src="https://blogs.nvidia.com/wp-content/uploads/2016/07/Deep_Learning_Icons_R5_PNG.jpg.png" width="70%">
</center>
- 인공지능의 적용: 데이터 활용 -> 모델 생성 -> 기능 구현



## Model, Learning
- 데이터에 맞는 설명 방법을 찾는 과정 = Model Fitting => Learning 학습
- 모델의 종류: 선형/비선형/확률 분포 함수, Neural Network의 architecture/parameter set 등

### How?
1. 가설을 세우고 데이터를 넣어봄
2. 결과 평가 - 예측이나 분류의 정확도 등 ex) MSE, F1 score, etc...
3. 개선을 위한 모델 수정 - parameter 수정, 모델 변겅 등

### Which parameter?
- simple model:
$$
\begin{equation}
\begin{aligned}
y=ax+b
\end{aligned}
\end{equation}
$$  

&emsp;&emsp;&emsp;&emsp;$y$ = 예측 결과값(estimation/prediction),  <br>
&emsp;&emsp;&emsp;&emsp;$x$ = 데이터(고정값),  <br>
&emsp;&emsp;&emsp;&emsp;$a$ = 기울기(slope),  <br>
&emsp;&emsp;&emsp;&emsp;$b$ = y절편(bias) <br> 

- slope($a$)와 bias($b$)의 변화에 따른 그래프 비교  
>* Source: [Lumenlearning](https://courses.lumenlearning.com/intermediatealgebra/chapter/read-transform-linear-functions/)  

<center>
<p><img src ="https://s3-us-west-2.amazonaws.com/courses-images-archive-read-only/wp-content/uploads/sites/924/2015/11/25201051/CNX_Precalc_Figure_02_02_0052.jpg" width="60%"></p>
<p><img src ="https://s3-us-west-2.amazonaws.com/courses-images-archive-read-only/wp-content/uploads/sites/924/2015/11/25201052/CNX_Precalc_Figure_02_02_0062.jpg" width="60%"></p>
</center>

&emsp;&emsp;- $a$와$b$는 parameter $\theta$로써 변경을 통해 가장 좋은 결과값을 찾음

### Which Model?
- 어떤 모델(함수 또는 알고리즘)을 사용할지 하나씩 돌려보는 것이 AutoML
- 비슷한 애들... AutoAI, Auto KERAS, Auto-SKLearn, etc...

> 학습 = 실제 확인된 답과 예측치 간의 오차(Error, Loss, Cost)를 줄여나가는 최적화 과정

## Data

### Stuctured Data
- Relational DB
- Spread Sheet  

### Semi-structured Data
- System logs
- Sensor data
- HTML  

### Unstructured Data
- Image/Video
- Sound
- Document

## Overfitting, Generalization
- Higher Model's capacity -> Overfitting -> more Generalization Error -> worse model for new(unseen) data
- 새로운 데이터에도 좋은 성능을 내기 위한 방법들... 

### Cross Validation
- Dividing data to 3 groups (Train, Valid, Test)
- Train data for learning, Valid data for optimizing/tuning, Test data for evaluating(no more tune)  

### Others
- K-Fold Cross Validation: 후보 모델 간 비교 선택
- L1 / L2 Regularization
- Drop-out & Batch Normalization
- Data / Test time augmentation  

> 클래스 불균형 대처 방안 => Weight Balancing & Focal Loss / Over & Under Sampling / SMOTE
