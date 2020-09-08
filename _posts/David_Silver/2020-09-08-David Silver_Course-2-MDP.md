---
title: "[RL]David Silver_RL-Course-2:MDP"
categories: "David_Silver"
tags: "Reinforcement_Learning"
permalink: /RL/David_Silver/2/
excerpt: "Course Review"
changefreq : day
use_math: true
---

## RL Course by David Silver : MDP

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-01.jpg){: width="90%" height="90%"}{: .align-center}

Category : [[Reinforcement Learning]](https://apexst77.github.io/categories/#reinforcement-learning) - RL Course:David Silver 

- [0] [UCL Course on RL](https://www.davidsilver.uk/teaching/)
- [1] [intro-RL](https://apexst77.github.io/RL/David_Silver/1/)
- [2] [Markov Decision Processes](https://apexst77.github.io/RL/David_Silver/2/) : **this post**
- [3] [Planning by Dynamic Programming](https://apexst77.github.io/RL/David_Silver/3/) 
- [4] [Model-Free Prediction](https://apexst77.github.io/RL/David_Silver/4/) 
- [5] [Model-Free Control](https://apexst77.github.io/RL/David_Silver/5/) 
- [6] [Value Function Approximation](https://apexst77.github.io/RL/David_Silver/6/) 
- [7] [Policy Gradient](https://apexst77.github.io/RL/David_Silver/7/) 
- [8] [Integrating Learning and Planning](https://apexst77.github.io/RL/David_Silver/8/) 
- [9] [Exploration and Exploitation](https://apexst77.github.io/RL/David_Silver/9/) 
- [10] [Classic Games](https://apexst77.github.io/RL/David_Silver/10/) 

***

중요 단어는 모두 영어로 기록할 예정입니다.

ppt의 출처는 모두 David Silver 교수님의 Lecture임을 밝힙니다.

------

**Lecture Contents**

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-02.jpg){: width="90%" height="90%"}{: .align-center}

------

### Introduction to MDPs

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-03.jpg){: width="90%" height="90%"}{: .align-center}

**MDP**: Markov Decision Process 

MDP는 일반적으로 Reinforcement Learning의 Environment를 묘사한다.

**Lecture_1 복습**

- MDP는 Environment가 fully observation한 상태
- Observation = Agent State = Environment State

------

### Markov Property

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-04.jpg){: width="90%" height="90%"}{: .align-center}

Lecture1 에서 **Markov State**의 개념과 동일

다음 State에 영향을 주는 것은 바로전 State 뿐이다

------

### State Transition Matrix

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-05.jpg){: width="90%" height="90%"}{: .align-center}

**State Transion Matrix** : Markov state s에서 s'으로 이동할 확률들의 테이블

기본적으로 Pss'으로 표현하며 Pss'이란 s에서 Agent가 s'으로 이동할 확률을 의미한다.

------

### Markov Process

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-06.jpg){: width="90%" height="90%"}{: .align-center}

**(중요)**

Markov Process는 **tuple <S,P>**에 의해 결정된다.

- **S**는 유한개의 State의 집합이며
- **P**는 S 집합에서의 State Transition Probabilities Matrix를 의미한다.

------

### Example: Student Markov Chain

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-07.jpg){: width="90%" height="90%"}{: .align-center}

예를 들어 생각해보자

Lecture1에서의 Student Markov Chain를 가져온 것이다.

다시한번 간단한 상황설명을 하자면 학생은 각각의 State에서 확률적으로 다음 State로 움직인다.

이때 이동할 State는 각각의 확률대로 결정된다.

즉 이전에 거친 State에 관계없이 현재의 State만으로 다음 State가 결정(=Markov State)

결과적으로 Agent가 Sleep State에 도달할 때까지 연쇄적으로 시행된다.

------

### Example: Student Markov Chain Episodes

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-08.jpg){: width="90%" height="90%"}{: .align-center}

Sample **episodes** (start : S1 = Class_1)

Sleep is Terminal State(종결 State)(상태를 유지할 확률이 1)

Sleep에 도달할 때까지 거쳐간 State의 Sequence 1개를 Sampling된 episode라고 한다.

Ex

- C1 C2 C3 Pass Sleep

------

### Example: Student Markov Chain Transition Matrix

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-09.jpg){: width="90%" height="90%"}{: .align-center}

위의 Markov Chain에서 State Transition Matrix는 다음과 같다. 

------

### Markov Reward Process

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-10.jpg){: width="90%" height="90%"}{: .align-center}

**(중요)**

Markov Reward State는 **tuple <S,P,R,γ>**에 의해 결정된다.

- **S**는 유한개의 State의 집합이며
- **P**는 State Transition Probabilities Matrix를 의미한다.
- **R**은 Reward function이며, 각각의 State 도달했을 때 받게되는 Reward의 집합이다.
- **γ**는 discounted factor로 Dicounted Reward를 구할 때 사용되며 [0,1] 범위안의 수이다.

**Markov Process와의 차이를 중심으로 이해**

- R, γ가 추가되어 Discounted Reward의 개념을 도입 - Value Function의 평가가 가능해짐

------

### Example: Student MRP

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-11.jpg){: width="90%" height="90%"}{: .align-center}

Student MP와 큰차이는 없지만 각 State에 도달할때 받는 Reward값이 추가되었다.

------

### Return

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-12.jpg){: width="90%" height="90%"}{: .align-center}

discounted factor에 의해 discounted된 Reward의 합

실질적으로 강화학습의 Goal은 Reward합의 Maximize가 아닌 **Return의 Maximize**이다.

Step t에서 Return값은 위와 같이 계산된다. 

t+1 step 이후에 받는 보상은 **1step마다 γ가 곱해져 discounted**된다.

이때

- γ가 0에 가까울수록 myopic(근시적)이며
- γ가 1에 가까울수록 far-sighted(원시적)이다.

------

### Why discount?

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-13.jpg){: width="90%" height="90%"}{: .align-center}

**Why?**

- 수학적으로 convenient(편리)하다 : **수렴성을 증명**하기 편하다
- 순환적 Markov Processes에서 infinite return을 피할 수 있다.
- 미래에 대한 불확실성이 충분히 표현되지 않을 수 있다.
- Reward가 재정적이라면 **즉각적인 보상은 지연된 보상보다 더 많은 이자를 얻을 수 있다**.
- **동물과 사람의 행동은 즉각적인 보상을 선호**함을 보여준다.
- 만약 모든 sampling 된 episode가 terminate하다면 : **terminal state로 이동함이 보장된다면 : γ = 1(undiscounted)도 가능**하다

------

### Value Function

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-14.jpg){: width="90%" height="90%"}{: .align-center}

MRP에서의 value function은 **Return의 기댓값**으로 표현된다. 

------

### Example: Student MRP Returns

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-15.jpg){: width="90%" height="90%"}{: .align-center}

**γ = 0.5**일때 각각의 Episode에 대한 Return의 계산값이다

다음의 **기댓값이 Value Function이 된다.**

------

### Example: State-Value Function for Student MRP

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-16.jpg){: width="90%" height="90%"}{: .align-center}

**γ = 0**일때 각 State의 Value Function

Delayed Reward 0

Immediate Reward 1

------

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-17.jpg){: width="90%" height="90%"}{: .align-center}

**γ = 0.9**일때 각 State의 Value Function

Delayed Reward 0.9

Immediate Reward 0.1

------

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-18.jpg){: width="90%" height="90%"}{: .align-center}

**γ = 1**일때 각 State의 Value Function

Delayed Reward 1

Immediate Reward 0

------

### Bellman Equeation for MRPs

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-19.jpg){: width="90%" height="90%"}{: .align-center}

**value function**은 다음 두가지로 나눌 수 있다.

- 즉각적인 보상 
- discounted된 보상 γv($S_{t+1}$)

위의 PPT의 순으로 증명된다.

------

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-20.jpg){: width="90%" height="90%"}{: .align-center}

결과적으로 v(s)의 경우 다음 State로 이동할 경우 받는 R(t+1)과

그후에 받을 discounted된 보상 γv(S(t+1))을 더하여 구할 수 있다.

이때 v(S(t+1))는 이동 가능한 모든 State에 대하여 (이동할 확률 * 각각의 State에서의 V(s') 값)을 더하여 기댓값으로 구해진다.

------

### Example: Bellman Equation for Student MRP

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-21.jpg){: width="90%" height="90%"}{: .align-center}

앞의 식을 그대로 적용하여 $4.3 = -2 + 0.6 * 10 +  0.4 * 0.8$

------

### Bellman Equation in Matrix Form

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-22.jpg){: width="90%" height="90%"}{: .align-center}

다음과 같은 **행렬식**으로 표현가능하다.

------

### Solving the Bellman Equation

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-23.jpg){: width="90%" height="90%"}{: .align-center}

다음과 같이 v에 대해 정리가 가능하다.

시간복잡도가 $O(n^3)$ : 즉 small MRP에서만 can be solved directly

따라서 Big MRP를 해결하기 위해서 많은 상호적 방법이 존재한다.

- **DP**(Dynamic Programing)
- **MC**(Monte-Carlo)
- **TD**(Temperate-Difference)

------

### Markov Decision Process

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-24.jpg){: width="90%" height="90%"}{: .align-center}

Markov Decision Process(MDP)는 **tuple <S,A,P,R,γ>**에 의해 결정된다.

- **S**는 유한한 State의 집합이다
- **A**는 유한한 Action의 집합이다.
- **P**는 State Transition Transition Matrix를 의미한다
  - 단 $P_{ss'}^{a}$ 가 의미하는 것은 State s에서 a의 Action을 Agent가 하였을 때 State s'으로 전이될 확률이다.
- **R**은 Reward function이다.
  - 단 $R_s^a$ 가 의미하는 것은 State s에서 Policy(정책)에 의해 Action a가 결정되었을 때 받는 Reward이다.
- **γ**는 discounted factor로 Dicounted Reward를 구할 때 사용되며 [0,1] 범위안의 수이다.

**Markov Reward Process와의 차이를 중심으로 이해**

- Action의 개념이 도입됨에 따라 Policy의 개념 또한 도입됨
- P의 정의가 State s에서 s'으로 이동할 확률에서 State s에서 Action a를 하였을 때 s'으로 이동할 확률로 정의됨(즉 같은 Action이라도 다른 State로 이동할 수 있음) 
-  R의 정의가 s에 도달할 때 받는 Reward에서 s에서 Action a를 할 때 받는 Reward로 바뀜

------

### Example: Student MDP

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-25.jpg){: width="90%" height="90%"}{: .align-center}

**Student MP**와 **Student MRP**와의 차이점을 중점적으로 살펴보면

- Reward가 State가 아닌 Action에 따라 주어짐을 알 수 있다.
- Pub이라는 Action을 하더라도 **항상 같은 State가 아닌 3개의 State중 확률적으로 전이**된다.
- 각 State로 이동할 확률이 사라졌다.(MDP에서는 **Policy를 기반**으로 Agent가 움직인다)

------

### Policies

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-26.jpg){: width="90%" height="90%"}{: .align-center}

정책 Policy는 다음과 같이 정의된다 : State s에서 Action a를 Agent가 행할 확률을 pi(a\|s)라고 한다

MDP에서의 Policy는 정의에 의해 **History가 아닌 현재 State에 의존**하여 결정된다.

Policy는 **시간에 비의존적**이다

- 쉽게 말해서 **몇번째 step에 State s에 도달**하든 그때의 Policy는 동일하다.

------

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-27.jpg){: width="90%" height="90%"}{: .align-center}

MDP에서 **tuple <S,A,P,R,γ>**와 **정책 Policy**가 주어진다면

State Sequence는 **Markov process <S,$P^{\pi\}$>**에 의해 결정되고

Reward Sequence의 경우는 **Markov reward process <S,$P^{\pi\}$,$R^{\pi\}$,γ>**에 의해 결정된다. 

다음 두식이 성립하는 조건하에

- 첫번째 식의 경우 간단히 이해가 가능하다. 
  - 정책 $\pi\$에 의해 State s에서 s'으로 이동할 확률은 s에서 실행가능한 모든 Action a에 대하여 
  - **[Action이 선택될 확률(정책) * $P_{ss'}^a$(=s에서 Agent가 Action a를 행하여 s'으로 전이될 확률)]**의 합과 같다.
- 두번째 식의 경우도 마찬가지다
  - State s에서 정책에 의해 Action이 시행되어 받을 보상은 s에서 실행가능한 모든 Action a에 대하여 
  - **[Action이 선택될 확률(정책) * $R_{s}^a$(=state s에서 Action a를 행할 때 받는 보상)]**의 합과 같다.

------

### Value Function

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-28.jpg){: width="90%" height="90%"}{: .align-center}

**MDP**에서

- **state-value function**
  - State s에서 정책 $\pi\$를 따라 움직일 때 $G_t$의 Expectation(기댓값)
- **action-value function**
  - State s에서 Action a를 시행한 후 정책 $\pi\$를 따라 움직일 때 $G_t$의 Expectation(기댓값)
- 두 **value function**의 가장 큰 차이점은 **state-value function**은 각 state마다 평가되고 **action-value function**은 각 Action마다 평가된다.

------

### Example: State-Value for Student MDP

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-29.jpg){: width="90%" height="90%"}{: .align-center}

다음은 **state-value function**의 예시이다.

상황 조건 : Policy는 각 Action을 할 확률이 0.5 , γ = 1

------

### Bellman Expectation Equation

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-30.jpg){: width="90%" height="90%"}{: .align-center}

**state-value function**은 다시 immediate(즉각적인) 보상과 discounted된 value의 합의 Expectation 값으로 나눌 수 있다.

**action-value function**도 마찬가지이다. 

------

### Bellman Expectation Equation for $V_*$

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-31.jpg){: width="90%" height="90%"}{: .align-center}

**state-value function을 action-value function을 통해 표현**하면 다음과 같다.(=식 a)

------

### Bellman Expectation Equation for $Q_*$

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-32.jpg){: width="90%" height="90%"}{: .align-center}

**action-value function을 state-value function을 통해 표현**하면 다음과 같다.(=식 b)

------

### Bellman Expectation Equation for $V_*$ (2)

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-33.jpg){: width="90%" height="90%"}{: .align-center}

**a 식에 b 식을 대입**하면 다음과 같은 식을 얻을 수 있다. 

------

### Bellman Expectation Equation for $Q_*$ (2)

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-34.jpg){: width="90%" height="90%"}{: .align-center}

**b 식에 a 식을 대입**하면 다음과 같은 식을 얻을 수 있다. 

------

### Example: Bellman Expectation Equation in Student MDP

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-35.jpg){: width="90%" height="90%"}{: .align-center}

위의 식을 직접 적용해보면 비슷한 값을 얻을 수 있음을 알 수 있다.

**위의 예시는 State-value function** 적용

단 각 Action은 Policy에 의해  0.5 확률로 선택되며 γ = 1인 상황이다. 

------

### Bellman Expectation Equation (Matrix Form)

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-36.jpg){: width="90%" height="90%"}{: .align-center}

Bellman Expectation Equation을 **행렬**로 표현하면 다음과 같이 표현된다.

------

### Optimal Value Function

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-37.jpg){: width="90%" height="90%"}{: .align-center}

**Optimal Value function은 $v_*$로 표현**된다.

**$v_*$**는 여러개의 **정책 $\pi\$** 에 대하여 최대(max)의 **state_value function** 이며

**$q_*$**는 여러개의 **정책 $\pi\$** 에 대하여 최대(max)의 **action_value function** 이다.

------

### Example: Optimal Value Function for Student MDP

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-38.jpg){: width="90%" height="90%"}{: .align-center}

**Student MDP**에서 최적의 정책에 대하여 **$v_*$**를 표현한 것이다.

당연하게도 **$v_*$가 커지는 State(최적의 정책)**를 따라갈시 계속해서 공부하여 시험에 패스하는 것이 최적의 정책이다.

------

### Example: Optimal Action-Value Function for Student MDP

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-39.jpg){: width="90%" height="90%"}{: .align-center}

**Student MDP**에서 최적의 정책에 대하여 **$q_*$**를 표현한 것이다.

당연하게도 **$q_*$가 가장 큰 Action(최적의 정책)**을 따라갈시 계속해서 공부하여 시험에 패스하는 것이 최적의 정책이다.

------

### Optimal Policy

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-40.jpg){: width="90%" height="90%"}{: .align-center}

정책 사이의 **부분 순서**를 다음과 같이 정의하자

- 만약 정책 $\pi\$ 와 $\pi\'$에 대하여 각 Agent가 정책을 따라갈 때

- **모든 State에 대하여 $V_{\pi\}(s) >= V_{\pi\'}(s)$ 가 성립할 경우 $\pi\ >= \pi\'$ 가 성립**한다.

또한 **최적의 정책 $\pi\_*$**에 대해 다음과 같이 정의하자.

- 다른 모든 정책에 대해 각 State의 state-value function이 항상 더 클 경우 이 정책을 **optimal policy**라고 정의하자.

**중요)** 이때 다음 이론이 성립한다.(증명되었다)

- For any MDP(**모든 MDP**에 대하여)
- **최적의 정책** $\pi_{*}$은 언제나 존재한다.
- 최적의 정책 $\pi_\*{(s,a)}$에 의한 state-value function은 언제나 $V_*(s)$와 같다.
-  최적의 정책 $\pi_\*{(s,a)}$에 의한 action-value function은 언제나 $q_*(s,a)$와 같다.

------

### Finding an Optimal Policy

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-41.jpg){: width="90%" height="90%"}{: .align-center}

만약 **$q_*(s,a)$**를 알고 있다면 반대로 **optimal policy**가 결정된다.

**최적의 정책**은 언제나 **$q_{*}(s,a)$**가 가장 큰 **Action**을 선택함으로써 구할 수 있다.

------

### Example: Optimal Policy for Student MDP

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-42.jpg){: width="90%" height="90%"}{: .align-center}

**$q_*(s,a)$**가 가장 큰 **Action**을 선택하면 다음과 같은 **빨간색 경로(optimal policy)**가 구해지게 된다.

------

### Bellman Optimality Equation for $V_*$

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-43.jpg){: width="90%" height="90%"}{: .align-center}

$V_\*(s)$는 모든 Action에 대하여 $q_\*(s,a)$의 최대와 같다. (식 -1)

------

### Bellman Optimality Equation for $Q_*$

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-44.jpg){: width="90%" height="90%"}{: .align-center}

$q_\*(s,a)$는 **immediate Reward**와 **Action에 의해 파생 가능한 모든 State s'에 대하여 $v_\*(s')$의 기대값**의 합으로 표현 가능하다. (식 -2)

------

### Bellman Optimality Equation for $V_*$ (2)

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-45.jpg){: width="90%" height="90%"}{: .align-center}

식-1에 식-2를 대입하면 다음과 같다.

------

### Bellman Optimality Equation for $Q_*$ (2)

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-46.jpg){: width="90%" height="90%"}{: .align-center}

식-2에 식-1를 대입하면 다음과 같다.

------

### Example: Bellman Optimality Equation in Student MDP

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-47.jpg){: width="90%" height="90%"}{: .align-center}

 다음의 **Student MDP**에서 다음 식이 성립함을 확인할 수 있다.

- 6은 (-2+8)과 (-1+6) 중 큰 값을 고른것이다.

------

### Solving the Bellman Optimality Equation

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-48.jpg){: width="90%" height="90%"}{: .align-center}

Bellman Optimality Equation은 linear(선형적)이지 않다.

- 식에 **max함수**가 들어가 있기 때문이다.
- 따라서 closed form 방법이 존재X(일반적인 경우에는)
- 이것을 해결하기 위한 다양한 방법이 존재한다.

------

**아래부터는 추후 공부 예정**

---

### Extensions to MDPs

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-49.jpg){: width="90%" height="90%"}{: .align-center}

------

### Infinite MDPs

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-50.jpg){: width="90%" height="90%"}{: .align-center}

------

### POMDPs

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-51.jpg){: width="90%" height="90%"}{: .align-center}

------

### Belief States 

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-52.jpg){: width="90%" height="90%"}{: .align-center}

------

### Reductions of POMDPs

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-53.jpg){: width="90%" height="90%"}{: .align-center}

------

### Ergodic Markov Process

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-54.jpg){: width="90%" height="90%"}{: .align-center}

------

### Ergodic MDP

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-55.jpg){: width="90%" height="90%"}{: .align-center}

------

### Average Reward Value Function

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-56.jpg){: width="90%" height="90%"}{: .align-center}

------

### Question

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-57.jpg){: width="90%" height="90%"}{: .align-center}

------

질문 및 피드백은 환영합니다

***End***