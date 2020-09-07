---
title: "[RL]David Silver_RL-Lecture-1:intro-RL"
categories: "David_Silver"
tags: "Reinforcement_Learning"
toc_sticky: False
permalink: /RL/David_Silver/1/
excerpt: "Course Review"
changefreq : day
use_math: true
---

## RL Course by David Silver : intro-RL

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-01.jpg){: width="90%" height="90%"}{: .align-center}

***
**Category :** [[Reinforcement Learning]](https://apexst77.github.io/categories/#reinforcement-learning) - RL Course:David Silver**

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

ppt의 출처는 모두 David Silver 교수님의 Lecture임을 밝힙니다.

------

**Lecture Contents**

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-02.jpg){: width="90%" height="90%"}{: .align-center}

------

### Machine Learning

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-06.jpg){: width="90%" height="90%"}{: .align-center}

------

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
  - i.i.d: 동일한 확률분포로 부터 뽑힌 확률 변수 / 각각은 서로에게 독립적이다. 
- **Agent's actions affect the subsequent data it receives**
  - Agent의 Action이 후의 데이터에 영향을 미친다.

------

### Rewards

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-13.jpg){: width="90%" height="90%"}{: .align-center} 

$R_t$는 Step t에서 얼마나 Agent가 잘 행동하고있는지를 나타낸다. Agent의 목적은 **Reward를 Maximize하는 것**이다.

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
  - **Action($A_t$)**을 하는 주체
  - $O_t$, $R_t$를 받아 $A_t$를 행동한다

- **Environment**

  - 다음 그림에서 외부의 환경(지구)을 의미한다
  - Agent에게 **Observation($O_t$)**과 **Reward($R_t$)**를 준다
  - $A_t$를 받아 $O_{t+1}$, $R_{t+1}$을 Agent에게 전달한다

------

### History and State

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-18.jpg){: width="90%" height="90%"}{: .align-center} 

**History**: 모든 Observation, Action, Reward의 sequence(순서가 Observation - Reward - Action)

**State**: 다음 Observation, Action, Reward를 결정하는데 이용하는 information이다.
- **State**는 **History**의 함수이다.

------

### Environment State

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-19.jpg){: width="90%" height="90%"}{: .align-center} 

**Environment State**: Step t에서 Environment가 $O_{t+1}$과 $R{t+1}$을 pick할 때 이용한다.

- Agent는 대부분 Environment State를 보지 못한다.
- Agent가 Environment State를 보더라도, irrelevant(관계없는) information를 포함하고 있다.
- 지구의 바람을 예시를 들면 지구의 현재기압, 기온, 수온, 등(굉장히 많은 요소)을 고려하여 바람(Observation과 Reward)이 형성될 것이다. 이때 지구의 현재기압, 기온, 수온, 등이 Environment가 참고하는 Environment State가 된다. 

------

### Agent State

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-20.jpg){: width="90%" height="90%"}{: .align-center} 

**Agent State**: Step t에서 Agent가 $A_t$을 pick할 때 이용한다.

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
    - $S_t$를 참고하여 $S_{t+1}$로 State가 전이될 확률은 S(1:t)까지 State를 참고하여 $S_{t+1}$로 State가 전이될 확률과 같다.
    - 즉 $S_t$가 S(1:t)를 대표할만큼 충분한 information을 포함한다는 의미이다.
  - 아래 수식이 의미하는 것은 다음과 같다.
    - Step t에 대하여 H(1:t)의 information을 $S_t$가 대표하며 Only $S_t$에 의존하여 (t+1) Step이후의 History가 모두 결정된다.

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

**Fully Obserable Environments**: Environment가 반환한 Observation이 Environment State 자체이고 Agent가 Environment State를 볼 수 있을 때의 Environment을 의미한다

즉 Agent State = Environment State = Observation 일 때

이러한 Process를 Markov decision process라고 하며 줄여서 MDP라고 부른다.

다음 Lecture에서 자세히 다룰 예정이다

------

### Partially Obsevable Environments

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-24.jpg){: width="90%" height="90%"}{: .align-center} 

**Partial Environments**: Agent가 Environment State를 전부 보지 못하고 일부만 본다.

- 예를 들어 탐사로봇은 시야(카메라)의 사각지대가 존재하여 Environment State를 전부 보지 못한다.
- 예를 들어 포커플레이어는 자신의 카드만 알고 상대의 카드를 알지 못한다.
- Agent State != Environment State

이러한 Process를 partially observable Markov decision process라고 하며 줄여서 POMDP라고 부른다.

POMDP에서는 위 PPT의 아랫내용과 같이 Agent State를 정하는 많은 방법이 있다.

------

### Major Component of an RL Agent

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-25.jpg){: width="90%" height="90%"}{: .align-center} 

Reinforcement Learning

- Policy(정책)
  - Agent가 행동을 결정하는 규칙
- Value
  - 지금의 State 혹은 Action이 얼마나 좋은지를 판단하는 척도
- Model
  - Model을 통해 Agent가 Environment를 예측한다.

------

### Policy

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-26.jpg){: width="90%" height="90%"}{: .align-center} 

**Peterministic Policy(결정적 정책)**: State가 주어지면 그에따라 Action이 1개로 결정

**Stochastic Policy(확률적 정책)**: State가 주어지면 그에따라 Action이 확률적으로 결정

------

### Value Function

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-27.jpg){: width="90%" height="90%"}{: .align-center} 

**Value Function**: 어떤 State로 이동하거나 Action을 할 때 **앞으로 받게될 총 보상**(Discounted Reward)의 기댓값

- 좋은 State/Action 을 판단하는 지표가된다.
- **Discounted Reward**: 하나의 Episode를 Sampling해보자.(Terminal State(종결)에 도달하기 까지 **Policy를 따라 움직인** 1개의 경로를 생각해보자) 이때 각 action마다의 보상이 존재할 것이다. 이러한 보상의 Sequence을 그대로 더할 수도 있겠지만 대부분의 RL에서는 현재의 보상이 미래의 보상보다 Valuable한 것으로 본다. 이를 위해 discount factor(γ)의 개념을 도입하였다.
  - discount factor(γ)을 적용하여 미래에 받을 보상보다 현재의 보상에 더욱 비중을 두었다.
  - step이 지날수록 받는 보상에 discount factor(γ)가 추가적으로 곱해진다(작아진다)
  - γ∈[0,1)
- Discounted Reward에 관해서는 다음 강의에서 자세히 알아볼 예정이다.
- **핵심!(오개념 주의)**
  - **앞으로 받게 될 총 보상**의 기댓값이라는 것에 유의하자
    - Discounted Reward는 1개의 Episode에 대하여 discount factor(γ)의 개념을 도입하여 Reward의 합을 구한것이다.
    - Value Function은 **이러한 합의 기댓값**이다.
  - Value Function은 policy의 확률적인 영향뿐만 아니라 Environment의 확률적인 영향도 받는다.
    - 배가 앞으로 이동할 때 바람이 이 배를 추가로 이동시켰다면 보상은 달라질 것이다. Value Function은 이러한 영향까지 모두 고려한 수치이다. 

------

### Model

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-29.jpg){: width="90%" height="90%"}{: .align-center} 

Model은 다음 Environment를 예측한다.

즉 다음과 같은 일을 수행한다.

- Environment의 $State_t$와 자신의 Action에 대한 다음 Environment의 $State_{t+1}$를 예측
- Environment의 $State_t$와 자신의 Action에 대한 Environment의 $Reward_t$를 예측

Model이 있는 RL을 Model-Based Learning이라 하고 

Model이 없는 RL을 Model-Free Learning이라 한다.

------

### Maze Example(Example of  Model)

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-30.jpg){: width="90%" height="90%"}{: .align-center} 

1 step 마다 N,E,S,W 중 1칸을 움직이는 Action을 한다.

1 step 마다 -1의 Reward를 받는다.

------

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-31.jpg){: width="90%" height="90%"}{: .align-center} 

각각의 State에 따라 policy를 표현한 것이다.(아마 optimal policy를 말하는 듯 하다)

------

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-32.jpg){: width="90%" height="90%"}{: .align-center} 

discount factor(γ) = 1인 상황 즉 Discounted Reward의 개념이 도입되지 않은 Value Function이다.

------

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-33.jpg){: width="90%" height="90%"}{: .align-center} 

**중요**

- 다음은 Maze에서 Learning한 Agent의 Model을 나타낸 것이다.
- **각 칸마다 -1이 쓰여있는 것을 볼 수 있다**: 1 step마다 보상을 -1로 예측하고 있다
- 위의 미로의 모습이 Model이 Maze(Environment State)를 예측한 것이다
  - **원래 미로의 모습과 다르다**: Agent가 가보지 않은 State는 Model에 포함되지 않는다. 즉 위의 그림이 Agent가 생각하는 Maze의 모습이다.

------

### Categorizing RL agents

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-34.jpg){: width="90%" height="90%"}{: .align-center} 

Agent의 구성에 따라 크게 3가지로 나눌 수 있다. 

- Value Based
  - No Policy, Only Value Function
  - Q. Policy가 없는 데 Value Function이 어떻게 정의되나요? Policy를 따라 움직인 경로에서 Reward의 합을 구해야 Value Function이 정의되는 것 아닌가요?
  - A. 대부분의 Value - Based RL은 Value Function을 Policy로써 사용합니다. 즉 Value Based를 통해 최적경로를 탐색합니다.
- Policy Based
  - No Value Function, Only Policy
- Actor Critic
  - Policy와 Value Function 둘다 존재

------

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-35.jpg){: width="90%" height="90%"}{: .align-center} 

- Model Free: Model 없음
- Model Based: Model 존재

------

### RL Agent Taxonomy

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-36.jpg){: width="90%" height="90%"}{: .align-center} 

------

### Learning and Planning

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-37.jpg){: width="90%" height="90%"}{: .align-center} 

**Reinforcement Learning**: Environment를 알지 못한채 학습

- Agent가 Environment와 interact(상호작용)하고 policy를 improves 시킴

**Planning**: Environment를 완벽히 알고 학습 / 모델이 완벽함

- 외적인 상호작용 없이 Model을 통해 Agent는 policy를 학습시킴
- 단어 그대로 "Planning"

------

### Atari Example

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-38.jpg){: width="90%" height="90%"}{: .align-center} 

**Reinforcement Learning**의 관점에서 Atari Game을 분석하며 지금까지 내용을 정리하자

**Atari Game**: Model 완벽 X

- Agent: 게임을 하는 사람
- Environment: 게임기
- Reward: 점수
- Observation: 게임기 화면
- Action: 조이스틱 움직임
- Agent State: 점수, 적들과의 거리, 적들의 수 등 (Agent가 정하기 나름)
- Environment State: 적들의 위치, 조이스틱의 움직임, 등 게임기의 모든 데이터
- Model: 적들의 위치 예측, 적에 따른 주는 점수 예측, 화면 밖으로 이동이 불가한걸 알음, 등 사람이 하는 다양한 예측이 모두 Model에 의한 예측임

------

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-39.jpg){: width="90%" height="90%"}{: .align-center} 

**Planning**의 관점에서 Atari Game을 분석하며 지금까지 내용을 정리하자

**Atari Game**: Model이 완벽

- 그럴리는 없겠지만 머리속으로 게임을 구동할 수 있는 사람이 있다고 가정하자
- 그 사람은 적들이 어디로 움직일지 화면이 어떻게 변할지 미리 완벽하게 예상할 수 있다.
- 이럴때는 다음과 같이 tree search로 학습이 가능하다.
  - 모든 경우에 대하여 받는 점수(Reward)를 완벽하게 예측이 가능하므로 가장 최적의 경로를 tree search로 찾는것이 가능한 것이다.

------

### Exploaration and Exploitation

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-40.jpg){: width="90%" height="90%"}{: .align-center} 

- Agent는 시행착오의 방법으로 good policy를 발견해야한다.
- Environment에서의 experience으로부터
- 너무 많은 reward를 잃지 않는 방법으로

------

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-41.jpg){: width="90%" height="90%"}{: .align-center} 

**Exploration**: 이미 있는 방법에 머물지 않고 지속적으로 더 좋은 방법을 찾음

**Exploitation**: 찾아낸 방법을 반복함으로써 Reward를 극대화 시킨다

Explore가 Exploit보다 대체적으로 중요하다

- Explore가 중요할 때가 많이 있지만 몇몇 상황에서는 Explore가 도움이 되지 않을 수 도 있다.

------

### Examples of Exploration and Exploitation

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-42.jpg){: width="90%" height="90%"}{: .align-center} 

------

### Prediction and Control

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-43.jpg){: width="90%" height="90%"}{: .align-center} 

**중요**

**Prediction**: 미래(Reward)를 평가 / Policy가 주어짐

**Prediction Problem**: Value Function을 학습시키는 문제

**Control**: 미래(Reward)를 최적화

**Control Problem**: best Policy를 찾음

------

### Gridworld Example: Prediction

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-44.jpg){: width="90%" height="90%"}{: .align-center} 

Prediction Problem이므로 Policy로부터 Value Function을 구해야 한다.

**상황설명** 

- Agent는 각 State에서 랜덤으로 움직인다
- Agent가 A에 도달하면 A'으로 이동하며 보상 +10을 얻는다
- Agent가 B에 도달하면 B'으로 이동하며 보상 +5를 얻는다
- Agent는 1 step마다 음의 reward를 받는다

이때 각각 Value Function은 다음과 같이 표현된다

**오개념 주의!**

- 다음의 Value Function을 Agent가 State에 도달할때 **받는** Reward로 생각하면 안된다.
- 바로 받는 Reward가 아니라 앞으로 받을 Reward의 Discounted 합의 기댓값이다.
- Value Function은 Discounted Reward의 Expection값임을 항상 기억하자.

------

### Gridworld Example: Control

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-45.jpg){: width="90%" height="90%"}{: .align-center} 

다음은 **Control Problem**이므로 최적의 Policy를 구해야 한다.

최적의 Policy는 가장 오른쪽 그림과 같다.

Optipma Policy, Optimal Value Function을 표현할 때에는 오른쪽 아래에 *를 붙인다.

Optimal Value Function의 표기가 약간 헷갈릴 수 있는데  V *라는 것은 Policy *에 대한 Value Function이라는 뜻이다.

------

### Course Outline

![-]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/1/intro_RL-46.jpg){: width="90%" height="90%"}{: .align-center} 

------

질문 및 피드백은 환영합니다

***End***

