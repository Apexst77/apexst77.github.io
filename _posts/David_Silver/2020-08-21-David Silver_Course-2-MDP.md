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

Markov state s에서 s'으로 이동할 확률들의 테이블

기본적으로 Pss'으로 표현하며 Pss'이란 s에서 Agent가 s'으로 이동할 확률을 의미한다.

------

### Markov Process

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-06.jpg){: width="90%" height="90%"}{: .align-center}



------

### Example: Student Markov Chain

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-07.jpg){: width="90%" height="90%"}{: .align-center}



------

### Example: Student Markov Chain Episodes

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-03.jpg){: width="90%" height="90%"}{: .align-center}



------

### Example: Student Markov Chain Transition Matrix

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-03.jpg){: width="90%" height="90%"}{: .align-center}



------

### Example: Student MRP

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-03.jpg){: width="90%" height="90%"}{: .align-center}



------

### Return

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-03.jpg){: width="90%" height="90%"}{: .align-center}



------

### Why discount?

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-03.jpg){: width="90%" height="90%"}{: .align-center}



------

### Value Function

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-03.jpg){: width="90%" height="90%"}{: .align-center}



------

### Example: Student MRP Returns

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-03.jpg){: width="90%" height="90%"}{: .align-center}



------

### Example: State-Value Function for Student MRP

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-03.jpg){: width="90%" height="90%"}{: .align-center}



------

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-03.jpg){: width="90%" height="90%"}{: .align-center}



------

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-03.jpg){: width="90%" height="90%"}{: .align-center}



------

### Bellman Equeation for MRPs

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-03.jpg){: width="90%" height="90%"}{: .align-center}



------

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-03.jpg){: width="90%" height="90%"}{: .align-center}



------

### Example: Bellman Equation for Student MRP

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-03.jpg){: width="90%" height="90%"}{: .align-center}



------

### Bellman Equation in Matrix Form

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-03.jpg){: width="90%" height="90%"}{: .align-center}



------

### Solving the Bellman Equation

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-03.jpg){: width="90%" height="90%"}{: .align-center}



------

### Markov Decision Process

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-03.jpg){: width="90%" height="90%"}{: .align-center}



------

### Example: Student MDP

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/2/MDP-03.jpg){: width="90%" height="90%"}{: .align-center}



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