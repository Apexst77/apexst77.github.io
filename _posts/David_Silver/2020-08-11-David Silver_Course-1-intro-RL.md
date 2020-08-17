---
title: "[RL]David Silver_RL-Lecture-1:intro-RL"
categories: "David_Silver"
tags: "Reinforcement_Learning"
permalink: /RL/David_Silver/1/
excerpt: "Course Review"
changefreq : day
---

## RL Course by David Silver : intro-RL

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-01.jpg){: width="90%" height="90%"}{: .align-center}

***
**Contents : [[Reinforcement Learning]](https://apexst77.github.io/categories/#reinforcement-learning) - RL Course:David Silver**

- [0] [UCL Course on RL](https://www.davidsilver.uk/teaching/)
- [1] [intro-RL](https://apexst77.github.io/RL/David_Silver/1/) : **this post**
- [2] [Markov Decision Processes](https://apexst77.github.io/RL/David_Silver/2/) 
- [3] [Planning by Dynamic Programming](https://apexst77.github.io/RL/David_Silver/3/) 
- [4] [Model-Free Prediction](https://apexst77.github.io/RL/David_Silver/4/) 
- [5] [Model-Free Control](https://apexst77.github.io/RL/David_Silver/5/) 
- [6] [Value Function Approximation](https://apexst77.github.io/RL/David_Silver/6/) 
- [7] [Policy Gradient](https://apexst77.github.io/RL/David_Silver/7/) 
- [8] [Integrating Learning and Planning](https://apexst77.github.io/RL/David_Silver/8/) 
- [9] [Exploration and Exploitation](https://apexst77.github.io/RL/David_Silver/9/) 
- [10] [Classic Games](https://apexst77.github.io/RL/David_Silver/10/) 

***

강의를 통해 공부한 내용을 바탕으로 최대한 자세히 정리할 예정

중요 단어는 모두 영어로 기록할 예정입니다.

------

### Machine Learning

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-07.jpg){: width="90%" height="90%"}{: .align-center}

**Machine Learning**은 다음 세가지를 포함하는 개념이다.

- Supervised Learning(지도학습)
- Unsupervised Learning(비지도학습)
- Reinforcement Learning(강화학습)

기존의 Supervised Learning과 Reinforcement Learning은 서로 다른 Characteristics(특징)을 가진다.

------

### Characteristics of Reinforcement Learning

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-08.jpg){: width="90%" height="90%"}{: .align-center} 

**Reinforcement Learning**이 가지는 특징

- **There is no supervisor(감시자)** : 누구도 답(행동)을 알려주지 않음 
  - supervised learning과의 차이점
  - supervisor가 없으므로 optimal solution을 찾는 목적에 적합하다
- **Only a reward signal** : 오직 reward(보상) 신호만이 존재
  - Reinforcement Learning은 reward를 maximize(최대화)하는 목적을 가진다
- **Feedback is delayed, not instaneous** : Feedback이 즉각적이지 않고 지연될 수 있다.
  - Action(행동)이 당장의 결과가 아닌 미래의 결과에 영향을 줄 수 있다.
- **Time really matters**: 시간이 중요하다!
  - Sequential data: 순서와 시간이 중요한 데이터
  - non i.i.d data: independent identically distributed(독립 동일 분포)가 아니다.
  - i.i.d: 동일한 확률분포로 부터 뽑힌 확률 변수에 대하여 각각은 서로에게 독립적이다. 
- **Agent's actions affect the subsequent data it receives**
  - Agent의 Action이 후의 데이터에 영향을 미친다.

------

### Rewards

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-13.jpg){: width="90%" height="90%"}{: .align-center} 

R_t는 Step t에서 얼마나 Agent가 잘 행동하고있는지를 나타낸다. Agent의 목적은 **Reward를 Maximize하는 것**이다.

Reward는 반드시 **Scalar**값이어야 한다.(Vector인자는 학습이 불가하다)

**모든 Reinforcement Learning 은 Reward hypothesis에 근거한다**

**Reward hypothesis**: 강화학습의 모든 목적은 축적되는 Reward를 극대화하는 것으로 표현될 수 있다.

Q. Do you agree with this statement?(동의하는가?)

- Reward hypothesis는 **항상** 성립하는가?
  - 당연하게도 항상 성립하지 않는다! Reward hypothesis가 성립하는 문제가 강화학습을 적용하기 적합한 문제이다.
  - **복잡한 문제**들은 Reward hypothesis가 적용되지 않는 경우가 더 많다. 이럴경우 작은 문제들로 나누어 강화학습을 적용해야 한다.
- Vector Reward로 학습하고 싶다면 어떻게 할 수 있는가?
  - Vector를 분해하여 각각의 성분을 **적절하게 더하여 Scalar로 표현**하면 된다.
  - Ex. Reward_Vector = (a,b) / Reward_Scalar = 10*a + 6*b

------

### Example of Rewards

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-14.jpg){: width="90%" height="90%"}{: .align-center} 

다음과 같은 Reward의 **예시**가 존재한다.

------

### Sequential Decision Making(순차적 의사 결정)

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-15.jpg){: width="90%" height="90%"}{: .align-center} 

**Goal**: select action to maximise total future reward

Action은 장기적인(미래의 Reward의 극대화) 결과를 가져올 수 있다.

Reward는 **지연**될 수 있다: 지금의 Action이 바로 Reward에 영향을 주지는 않는다

즉 **미래의 보상을 위해 현재의 보상을 희생**하는 것이 이득을 가져올 수도 있다.

------

### Agent and Environment

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-17.jpg){: width="90%" height="90%"}{: .align-center} 

**강화학습의 핵심**

- **Agent**
- 다음 그림에서 뇌를 의미한다
  - **Action(A(t))**을 하는 주체
  - O(t), R(t)를 받아 A(t)를 행동한다
  
- **Environment**

  - 다음 그림에서 외부의 환경(지구)을 의미한다
  - Agent에게 **Observation(O(t))**과 **Reward(R(t))**를 준다
  - A(t)를 받아 O(t+1), R(t+1)을 Agent에게 전달한다

------

### History and State

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-18.jpg){: width="90%" height="90%"}{: .align-center} 

**History**: 모든 Observation, Action, Reward의 sequence(순서가 Observation - Reward - Action)

**State**: 다음 Observation, Action, Reward를 결정하는데 이용하는 information이다.
- **State**는 **History**의 함수이다.

------

### Environment State

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-19.jpg){: width="90%" height="90%"}{: .align-center} 

**Environment State**: Step t에서 Environment가 O(t+1)과 R(t+1)을 pick할 때 이용한다.

- Agent는 대부분 Environment State를 보지 못한다.
- Agent가 Environment State를 보더라도, irrelevant(관계없는) information를 포함하고 있다.
- 지구의 바람을 예시를 들면 지구의 현재기압, 기온, 수온, 등(굉장히 많은 요소)을 고려하여 바람(Observation과 Reward)이 형성될 것이다. 이때 지구의 현재기압, 기온, 수온, 등이 Environment가 참고하는 Environment State가 된다. 

------

### Agent State

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-20.jpg){: width="90%" height="90%"}{: .align-center} 

**Agent State**: Step t에서 Agent가 A(t)을 pick할 때 이용한다.

- Agent State는 History의 함수이다.
- Environment가 전달한 Observation의 일부 또는 전체가 Agent State에 포함된다.
- 배를 탄 선장을 Agent라고 가정해보자. 선장마다 배를 조종할 때 중요시하는 요소들이 다를 것이다. A선장이 바람과 태양의 세기를 중요시한다면 A선장의 Agent State는 바람과 태양의 세기가 되는 것이고 B선장이 바람과 파도를 중요시한다면 B선장의 Agent State는 바람과 파도가 되는 것이다.

------

### Information State(a.k.a. Markov state)

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-21.jpg){: width="90%" height="90%"}{: .align-center} 

다음의 조건을 만족하는 State를 Markov State라고 부른다.

- History의 함수이다.
- 다음 State의 결정은 바로 이전 State에만 의존한다.
  - 이게 의미하는 것은 위 PPT의 두 수식으로 이해할 수 있다.
  - Definition의  수식이 의미하는 것은 다음과 같다.
    - P[ ] 가 의미하는 것은 Probability(확률)이다
    - S(t)를 참고하여 S(t+1)로 State가 전이될 확률은 S(1:t)까지 State를 참고하여 S(t+1)로 State가 전이될 확률과 같다.
    - 즉 S(t)가 S(1:t)를 대표할만큼 충분한 information을 포함한다는 의미이다.
  - 아래 수식이 의미하는 것은 다음과 같다.
    - Step t에 대하여 H(1:t)의 information을 S(t)가 representation(대표)하며 Only S(t)에 의존하여 (t+1) Step이후의 History가 모두 결정된다.

Environment State와 History는 Definition에 의해 Markov State임이 자명하다.

- History는 모든 information의 Sequence임으로 이전 History를 참고할 필요가 없다.
- Environment State는 정의에 의해 Markov하다.

------

### Rat Example(Example of  Agent State)

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-22.jpg){: width="90%" height="90%"}{: .align-center} 

Signal은 총 3가지가 주어진다

- Light
- Lever
- Bell

Light, Light, Lever, Bell의 신호가 주어졌을 때 **전기자극(Punishment)**을 주었다.

Bell, Light, Lever, Lever의 신호가 주어졌을 때 **치즈(Reward)**를 주었다.

그렇다면 Lever, Light, Lever, Bell의 경우에는 어떤 결과가 예측되는가?

-  A생쥐의 경우 전기자극을 예측하였다. Agent State가 마지막 3개의 Signal이기 때문이다.
- B생쥐의 경우 치즈를 예측하였다. Agent State가  Lever, Light, Bell의 각각의 숫자이기 때문이다.

즉 Agent State은 Agent가 정하기 나름이다. 같은 data라도 다른 추측이 가능해진다.

------

### Fully Obsevable Environments

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-23.jpg){: width="90%" height="90%"}{: .align-center} 

Agent State는 주로 Observation과 Reward의 함수이다.

**Fully Obserable Environments**: Environment가 반환한 Observation이 Environment State 자체이고 Agent가 Environment State를 볼 수 있을 때(Agent State = Environment State = Observation 일 때) 이때의 Environment

이러한 Process를 Markov decision process라고 하며 줄여서 MDP라고 부른다.

다음 Lecture에서 자세히 다룰 예정이다

------

Partially Obsevable Environments

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-24.jpg){: width="90%" height="90%"}{: .align-center} 

**Partial Environments**: Agent가 Environment State를 전부 보지 못하고 일부만 본다.

- 예를 들어 탐사로봇은 시야(카메라)의 사각지대가 존재하여 Environment State를 전부 보지 못한다.
- 예를 들어 포커플레이어는 자신의 카드만 알고 상대의 카드를 알지 못한다.
- Agent State != Environment State

이러한 Process를 partially observable Markov decision process라고 하며 줄여서 POMDP라고 부른다.

POMDP에서는 위 PPT의 아랫내용과 같이 Agent State를 정하는 많은 방법이 있다.

------

Major Component of an RL Agent

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-25.jpg){: width="90%" height="90%"}{: .align-center} 

Reinforcement Learning

- Policy
  - Agent가 행동을 결정하는 규칙
  - A(t) = $${pie}$$(S(t)) 
- Value
- Model