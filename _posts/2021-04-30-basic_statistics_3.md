---
layout: single
title: "[Basic Statistics] 표본평균"
author_profile: true
excerpt: "랜덤샘플링, 표본평균"
categories:
    - Statistics
---

## 모집단, 랜덤샘플링

표본평균을 살펴보기 전에 먼저 모집단은 무엇일까? 모집단은 우리가 알 수 없는 세계의 전체를 의미한다. 예를들면, 이 세상에 존재하는 새의 날개의 길이는 우리가 모두 측정할 수 없다. 그래서 우리는 필연적으로 부분적으로 관측된 데이터(표본)를 이용해서 전체(모집단)를 추론할 수 밖에 없는 상황인 것이다. 

이때 모집단에 대해서 랜덤하게 샘플링을 하게 되면, 모집단의 분포 즉, 가장 나오기 쉬운 값들이 자주 나오게 되는 것을 쉽게 생각해볼 수 있다. 정규분포라고 하면 평균에 가까운 값들이 샘플링 했을 때 나오기 쉬운 값이 된다. (랜덤 샘플링의 가정)

그렇다면 데이터 하나의 값 x를 관측한 경우를 생각해보자. 이 데이터는 모집단의 평균에 가깝다고 생각할 수 있을까? 다른 값들에 비해서 평균일 가능성이 가장 큰 것이다. 즉 **모평균은 이 관측된 x값에 가까울 것이라는** 정도의 추정은 할 수 있다.

## 표본평균을 왜 구하나?

### 하나의 표본보다 여러 개의 표본의 평균이 모집단의 평균과 가까워진다.

우리가 평균을 구하는 이유를 한 번 생각해보면, 우연히 생긴 데이터를 없애고 실제의 값에 가까운 값을 만들어 내고 싶기 때문에 평균을 구하는 것이다. 그래서 표본평균은 여러 개의 표본을 구하여 평균을 내면 그것이 모집단의 평균에 가까워 지기 때문에 사용하는 것이다. 당연히 관측한 샘플이 많을 수록 모집단의 분포와 유사해진다는 랜덤샘플링의 가정을 생각한다면 직감적으로도 충분히 알 수 있는 부분이다. 

조금더 구체적으로 이해를 돕기위해 주사위 던지기 예를 생각해보자.

주사위 던지기를 무한히 했을 때, 즉 모집단의 평균은 3.5가 나오는 것은 알 수 있다.

**<수식 넣기>** 

그리고 주사위를 두 번 던지게 되었을 때, 표본들이 있을 것이다. 즉 주사위를 2번을 던졌을 때 나오는 2개의 값의 평균이 1개의 표본이 된다. 6x6으로 36개의 표본이 관측되는 상황이다. 이 표본 전체의 분포는 어떻게 될까? **<도표넣기>** 예상한 것처럼 모집단의 평균인 3.5를 중심으로 퍼져있는 분포가 나온다. 즉 표본평균이 모집단의 평균과 일치한다. 

### 관측된 데이터가 많을 수록 예언 구간은 좁아진다.

위의 주사위 예제를 살펴보았다. 그런데 주사위를 무한히 던졌을 때 나오는 모집단은 균일분포이다. (모든 숫자의 확률이 1/6) 그러나 그 표본평균의 분포는 가운데가 볼록한 형태의 분포를 하고 있다. 즉 일반적인 모집단의 분포를 알고 있다고 하더라도, 표본평균의 분포는 모집단의 분포와 달라진다. 하지만 모집단의 분포와 표본평균의 분포가 일치하는 것이 있는데,  바로 정규분포이다.

**<수식넣기>**  표준편차는 루트 n분의 1 작아짐..

**<도표넣기>**

이때 우리는 표본평균의 분포를 이용해서 모집단을 추정해볼 수가 있다. 계산 해보면 나오겠지만 표본의 개수가 많아질 수록 동일한 신뢰구간(예언구간)에서 예측했을 때, 그 구간이 좁아진다. 

## Reference
- 고지마 히로유키, 『세상에서 가장 쉬운 통계학입문』, 지상사(2009)