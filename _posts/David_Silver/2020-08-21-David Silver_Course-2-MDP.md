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

ppt의 출처는 David Silver 교수님의 Lecture입니다.

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

Markov Process는 tuple <S,P>에 의해 결정된다.

- S는 유한개의 State의 집합이며
- P는 S 집합에서의 State Transition Probabilities Matrix를 의미한다.

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

Sleep에 도달할 때까지 우리가 거쳐간 State의 Sequence 1개를 Sampling된 episode라고 한다.

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

Markov Reward State는 tuple <S,P,R,γ>에 의해 결정된다.

- S는 유한개의 State의 집합이며
- P는 S 집합에서의 State Transition Probabilities Matrix를 의미한다.
- R은 Reward function이며, 각각의 State 도달했을 때 받게되는 Reward의 집합이다.
- γ는 discounted factor로 Dicounted Reward를 구할 때 사용되며 [0,1] 범위안의 수이다.

**Markov Process와의 차이를 중심으로 이해**

------

### Example: Student MRP

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-11.jpg){: width="90%" height="90%"}{: .align-center}

Student MP와 큰차이는 없지만 각 State에 도달할때 받는 Reward값이 추가되었다.

------

### Return

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-12.jpg){: width="90%" height="90%"}{: .align-center}

discounted factor에 의해 discounted된 Reward의 합

실질적으로 강화학습의 Goal은 Reward합의 Maximize가 아닌 Return의 Maximize이다.

Step t에서 Return값은 위와 같이 계산된다. 

t+1 step 이후에 받는 보상은 1step마다 γ가 곱해져 discounted된다.

이때

- γ가 0에 가까울수록 myopic(근시적)이며
- γ가 1에 가까울수록 far-sighted(원시적)이다.

------

### Why discount?

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-13.jpg){: width="90%" height="90%"}{: .align-center}

**Why?**

- 수학적으로 convenient(편리)하다 : 수렴성을 증명하기 편하다
- 순환적 Markov Processes에서 infinite return을 피할 수 있다.
- 미래에 대한 불확실성이 충분히 표현되지 않을 수 있다.
- Reward가 재정적이라면 즉각적인 보상은 지연된 보상보다 더 많은 이자를 얻을 수 있다.
- 동물과 사람의 행동은 즉각적인 보상을 선호함을 보여준다.
- 만약 모든 sampling 된 episode가 terminate하다면 : terminal state로 이동함이 보장된다면 : γ = 1(undiscounted)도 가능하다

------

### Value Function

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-14.jpg){: width="90%" height="90%"}{: .align-center}

MRP에서의 value function은 Return의 기댓값으로 표현된다. 

------

### Example: Student MRP Returns

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-15.jpg){: width="90%" height="90%"}{: .align-center}

γ = 0.5일때 각각의 Episode에 대한 Return의 계산값이다

다음의 기댓값이 Value Function이 된다.

------

### Example: State-Value Function for Student MRP

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-16.jpg){: width="90%" height="90%"}{: .align-center}

γ = 0일때 각 State의 Value Function

Delayed Reward 0

Immediate Reward 1

------

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-17.jpg){: width="90%" height="90%"}{: .align-center}

γ = 0.9일때 각 State의 Value Function

Delayed Reward 0.9

Immediate Reward 0.1

------

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-18.jpg){: width="90%" height="90%"}{: .align-center}

γ = 1일때 각 State의 Value Function

Delayed Reward 1

Immediate Reward 0

------

### Bellman Equeation for MRPs

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-19.jpg){: width="90%" height="90%"}{: .align-center}

value function은 다음 두가지로 나눌 수 있다.

- 즉각적인 보상 R(t+1)
- discounted된 보상 γv(S(t+1))

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

다음과 같은 행렬식으로 표현가능하다.

------

### Solving the Bellman Equation

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-23.jpg){: width="90%" height="90%"}{: .align-center}

다음과 같이 v에 대해 정리가 가능하다.

시간복잡도가 $O(n^3)$ : 즉 small MRP에서만 can be solved directly

------

### Markov Decision Process

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-24.jpg){: width="90%" height="90%"}{: .align-center}



------

### Example: Student MDP

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-25.jpg){: width="90%" height="90%"}{: .align-center}



------

### Policies

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-26.jpg){: width="90%" height="90%"}{: .align-center}



------

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-27.jpg){: width="90%" height="90%"}{: .align-center}



------

### Value Function

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-28.jpg){: width="90%" height="90%"}{: .align-center}



------

### Example: State-Value for Student MDP

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-29.jpg){: width="90%" height="90%"}{: .align-center}



------

### Bellman Expectation Equation

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-30.jpg){: width="90%" height="90%"}{: .align-center}



------

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-31.jpg){: width="90%" height="90%"}{: .align-center}



------

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-32.jpg){: width="90%" height="90%"}{: .align-center}



------

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-33.jpg){: width="90%" height="90%"}{: .align-center}



------

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-34.jpg){: width="90%" height="90%"}{: .align-center}



------

### Example: Bellman Expectation Equation in Student MDP

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-35.jpg){: width="90%" height="90%"}{: .align-center}



------

### Bellman Expectation Equation (Matrix Form)

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-36.jpg){: width="90%" height="90%"}{: .align-center}



------

### Optimal Value Function

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-37.jpg){: width="90%" height="90%"}{: .align-center}



------

### Example: Optimal Value Function for Student MDP

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-38.jpg){: width="90%" height="90%"}{: .align-center}



------

### Example: Optimal Action-Value Function for Student MDP

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-39.jpg){: width="90%" height="90%"}{: .align-center}



------

### Optimal Policy

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-40.jpg){: width="90%" height="90%"}{: .align-center}



------

### Finding an Optimal Policy

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-41.jpg){: width="90%" height="90%"}{: .align-center}



------

### Example: Optimal Policy for Student MDP

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-42.jpg){: width="90%" height="90%"}{: .align-center}



------

### Bellman Optimality Equation

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-43.jpg){: width="90%" height="90%"}{: .align-center}



------

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-44.jpg){: width="90%" height="90%"}{: .align-center}



------

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-45.jpg){: width="90%" height="90%"}{: .align-center}



------

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-46.jpg){: width="90%" height="90%"}{: .align-center}



------

### Example: Bellman Optimality Equation in Student MDP

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-47.jpg){: width="90%" height="90%"}{: .align-center}



------

### Solving the Bellman Optimality Equation

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-48.jpg){: width="90%" height="90%"}{: .align-center}



------

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