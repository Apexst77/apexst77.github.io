---
title: "[RL]Reinforcement Learning-1"
categories: "Reinforcement_Learning"
tags: "Reinforcement_Learning"
toc_sticky: False
permalink: /RL/Reinforcement/1/
excerpt: "Introduction"
changefreq : day
use_math: true
---

# Chapter 1: Introduction

------

**Category :** [[Reinforcement Learning]](https://apexst77.github.io/categories/#reinforcement_learning) - Reinforcement Learning by Barto and Sutton

- [0] [Introduction](https://apexst77.github.io/RL/Reinforcement/1/)  : **this post**
- [1] [Multi-armed Bandits](https://apexst77.github.io/RL/Reinforcement/2/) 

------

**Lecture Contents**

- 1.1. Reinforcement Learning
- 1.2. Example
- 1.3. Elements of Reinforcement Learning
- 1.4. Limitations and Scope
- 1.5.  An Extended Example: Tic-Tac-Toe
- 1.6. Summary
- 1.7. Early History of Reinforcement Learning


-------

### **1.1. Reinforcement Learning**

#### 1. feature

Reinforcement Learning(강화학습)은 특정 상황에서 어떤 Action(행동)을 취할지를 학습하는 것을 의미한다.

Reinforcement Learning은 Environment(환경)과 Agent(학습자)의 상호작용을 통해 이루어지며 이를 **trial-and-error(시행착오)**라고 한다.

Environment는 Agent의 Action에 대하여 Reward(보상)를 전달한다. 

Reinforcement Learning의 또 하나의 특징으로는 **Delayed reward(지연된 보상)**이 있다.

Agent의 Action이 그 다음의 상황에 연속적으로 영향을 주게되는 상황이다.

이러한 두가지 특징이 Reinforcement Learning의 중요한 2가지 특성이다.

#### 2. meaning

Reinforcement Learning은 하나의 문제이기도 하며 그 문제를 해결할 방법이기도 하고 이 두가지를 연구하는 분야를 의미하기도 한다.

**세가지 개념모두 한가지 단어를 사용**하므로 구분에 주의를 가져야 한다.

#### 3. differentiator

Reinforcement Learning은 **Supervised Learning(지도 학습)**과는 다르다.

정답을 알려주는 Label(지침)이 존재하지 않기 때문이다

Reinforcement Learning은 **Unsupervised Learning(비지도 학습)**과는 다르다.

Unsupervised learning은 Label 없는 Data에서 숨겨진 구조를 찾는다.

이에 반해 Reinforcement Learning은 구조를 찾으려 하지 않는다.

#### 4. exploitation and exploration

**Exploitation(활용) and Exploration(탐험)**은 강화학습만이 가지는 어려운 문제다.

좋은 Action을 발견했을때 보상을 위해 이 Action을 계속 Exploitaion할 것인지

혹은 더 좋은 Reward의 Action을 찾기 위해 Exploration할 것인지 Agent는 선택해야 한다.

 

------

## 공부하며 참고한 내용

[**Reinforcement Learning**](http://incompleteideas.net/book/the-book-2nd.html)

[**단단한 강화학습 by JPub**] : 위 원서의 번역본입니다