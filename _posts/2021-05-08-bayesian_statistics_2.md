---
layout: single
title: "[Bayesian] 네이만-피어슨 통계와 베이즈 통계의 공통점과 차이점"
author_profile: true
excerpt: "추론, 최우원리"
categories:
    - Statistics
---

## 추론이란 무엇인가

추론이란 무엇일까? 사전적 정의는 '**이미 알려진 정보를 근거로 삼아 다른 판단을 이끌어 내는 것**' 이다. 여기서 이미 알려진 정보를 근거로 삼아 다른 판단을 이끌어 내는 데에는 2가지 방법이 있을 수 있다. 먼저는 전체를 알고 부분을 추론하는 방식의 **연역추론**이다. 예를들면, 사람은 죽는다. 나는 사람이다. 고로 나는 죽는다 라는 형태의 추론이다. 전체에 대한 것이라면 사람은 죽는다라는 것이고 사람인 나는 부분이 되는 것이다. 또 다른 방식은 **귀납적 추론**인데, 이것은 반대로 부분을 이용하여 전체를 추론하는 형태이다. 

그러면 여기서 연역적 추론과 귀납적 추론이 아닌 **확률적 추론**이란 무엇인가를 생각해보자. 추론이라는 것이 정보를 근거로 삼아 다른 판단을 이끌어 내는 것이라고 했다. 그러니까 그 이끌어 내는데 결론을 단정 짓는 것이 아니라, 어떠한 가능성을 나타내고 있다면 그것은 확률적 추론이다.

예를들면, A단지에 흰공 10개 , B단지에 검은공 10개가 들어 있다고 하자. 그러면 어느 장독대에서 꺼낸지는 모르지만 꺼낸 공이 흰공이라면 우리는 A단지에서 나왔을 것이라고 추론할 수 있다. 하지만 A단지에 흰공 8개 검은공 2개, B단지에 검은공 8개 흰공 2개가 있다고 생각해보자. 그러면 똑같이 꺼낸 공이 흰공이라면 우리는 A단지 라고 단정할 수 있겠는가? 아마도 우리는 "A단지일 **가능성**이 높다" 로 얘기할 것이다. 달리 표현하면 '**대체로** A단지 다.' 이렇게 가능성이 큰 쪽을 선택하는 것이 확률적 추론이다. 대부분의 현실문제가 이러한 확률적 추론을 해야하는 상황이지 않을까싶다.

## 네이만-피어슨 통계와 베이즈 통계의 차이

당연한 얘기겠지만 네이만-피어슨 통계 (표준통계학) 과 베이즈 통계는 확률적 추론이라는 점에서는 같다. 하지만 해석적인 부분에서 차이가 있는데, 표준통계학에서는 '대체로 A일 것이다.' 를 리스크는 있지만 A로 결론 짓자라는 의미로 사용된다. 하지만 베이즈 통계학에서는 'A, B 모두 가능하지만 A일 가능성이 훨씬 더 클 것이다' 라는 입장을 취한다. 책에서 언급한 표현인데, 사실 크게 와닿지는 않는다. 표준통계학에서 A의 선택보다 B를 선택함으로써 생기는 리스크가 더 크기 때문에 A라고 결론을 짓는 것인데 말이다.

두번 째 차이점이라고 하면, 표준통계학에서는 데이터가 최소한의 기준은 충족 되어야만 추정이 가능하다. **유의수준**이라는 것으로 리스크를 나타내는데,  0.05 또는 0.01 (과학적 근거는 없다고 함) 을 사용한다. 위의 예에서 A 단지 흰공 8개, 검은공 2개, B 단지에는 검은공 8개, 흰공 2개에서 꺼낸 공이 흰공이라고 했을 때, 대체로 A라고 추정한다고 했다. 그런데 **표준통계학 관점**에서 A라고 해서 틀렸을 가능성은 0.2 이기 때문에 유의수준을 훨씬 더 상회하는 리스크임으로 **추정을 할 수 없다**. 하지만 베이즈 통계는 사전확률이라는 '주관적'인 확률을 설정할 수 있기 때문에 유연하게 추정을 할 수 있다는 장점이 있다. 하지만 '주관적'이라는 자의성이 있기 때문에 그 책임은 통계가의 판단으로 남는다. 

## 최우원리에 근거한 베이즈 통계

최우원리란 '세상에서 일어나는 일은 일어날 확률이 큰 것이다'라는 원리이다.

예를들면 어떤 현상 X와 Y가 있다. 이를 일으키는 원인으로 A와 B가 있다. 원인 A로 인해서는 압도적으로 X 현상이 발생한다고 하자. (B는 그 반대라고 하자). 이 떄 현상 X가 관측이 되었다면 A와 B중 어떤 원인일까?

물론 양쪽의 가능성을 모두 생각할 수 있다. 하지만 어느 쪽이냐고 묻는다면 'A쪽이 원인일 것' 이라고 생각하는 편이 타당할 것이다. 이렇게 생각하는 발상이 최우원리이다.

### 네이만-피어슨 통계학도 최우원리에 근거

이 부분이 재밌었는데, 네이만-피어슨 통계학도 최우원리가 관계되어있다. 추정 그자체가 아니라 '**통계적 추정을 입증**' 하는데 도입하고 있다. 통계적 추정의 입증이란, 통계학에서 무언가에 대한 추정을 할 때 '왜 그렇게 생각하는가' , '그렇게 생각하는 것이 어떤 이점을 가져다 주는가'를 설명하는 것을 말한다. 

점추정을 예로들면, 하루에 일어나거나 혹은 일어나지 않는 어떤 현상이 있다고 하자. 손님 100명정도가 있고, 현상이 일어날 확률 p, 일어나지 않을 확률은 1-p가 된다. 관측결과 10일 중 4일간 일어났고 6일간은 발생하지 않았다. 이때 확률 p는 몇이라고 추정할 수 있을까?

실제 일어난 수치를 1로 나타내고, 일어나지 않은 일을 수치 0으로 나타내면, 관측치는 1이 4개, 0이 6개이다. 이를 전체 횟수인 10으로 나눈 평균은 0.4가 된다. 

여기서의 의문점은 왜 일어난 횟수의 평균치를 현상이 일어난 확률 p의 추정치로 잡는가이다. 잘 생각해보면 **'몇 번 중에 몇 번이 일어났다'는 사실과 '일어난 확률'이라는 것이 직접적으로 연결되어 있지는 않다.** 사실은 이를 입증하는데 최우원리가 사용된 것이다. 

여기서 일어난 확률이 p인 현상에 대해 '이 현상이 10회 중 딱 4회 일어날 확률' L을 p의 식으로 나타내보자. <수식삽입>

여기서 확률 p 값을 변화시켜갈 때 확률 L이 어떻게 변하는가를 그래프로 보면 아래와 같다. <그래프 삽입>

그래프를 보면 평균치인 0.4를 p로 설정한 경우에 관측된 결과(10회 중 4회 일어났다는 결과)의 확률 L이 가장 커지는 것이다. 이에 따라 통상 통계적 추정에서는 p=0.4라고 추정한다. 그리고 0.4를 **최우추정량**이라고 한다. N회 관측하여 x회 일어난 경우 최우추정량이 x/N 이 된다는 사실은 간단하게 증명할 수 있다. (미분법을 사용함) 즉, **최우원리는 평균치라는 통계량과 연결되어 있다**는 뜻이다.

### 유비추론(유추)에 대해서..

번외로 추론에 대해서 검색 중 유비추론(유추)에 대해서 생각해보게 되었다. 데이터를 분석하거나 무언가를 분석할 때 유추한다라는 표현을 많이 쓰게 된다. 유추의 사전저 의미를 한번 살펴보자.
'**하나의 현상과 다른 한 개 이상의 현상들이 기본 속성이나 관계, 구조, 기능 등에서 유사하거나 동형임을 들어 다른 요소들에 있어서도 유사하거나 동형일 것이라 추리하는 방법이다.**' 위 뜻을 보면서 드는 생각은 딥러닝을 하면서 서로 다른 도메인에 있는 데이터를 어떻게 하면 동일한 성능을 내게 할 수 있을까를 고민하게 된다. 결국은 모델이 '유추'를 할 수 있게 하고 싶은 것이다. 즉 다른 말로는 Generalization 이라고도 볼 수 있다. 딥러닝은 확률적 추론을 하고 있다. 하지만 이러한 유비추론이 함께 되었을 때 진정한 학습이 아닐까

## Reference
- 고지마 히로유키, 『세상에서 가장 쉬운 베이즈통계학 입문』, 지상사 (2017)