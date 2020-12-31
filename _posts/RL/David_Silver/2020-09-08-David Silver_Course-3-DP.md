---
title: "[RL]David Silver_RL-Course-3:DP"
categories: "Reinforcement_Learning"
tags: "David_Silver"
permalink: /RL/David_Silver/3/
excerpt: "Course Review"
changefreq : day
use_math: true
---

## RL Course by David Silver : intro-RL

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-01.jpg){: width="90%" height="90%"}{: .align-center}

Category : [[Reinforcement Learning]](https://apexst77.github.io/categories/#reinforcement-learning) - RL Course:David Silver 

- [0] [UCL Course on RL](https://www.davidsilver.uk/teaching/)
- [1] [intro-RL](https://apexst77.github.io/RL/David_Silver/1/)
- [2] [Markov Decision Processes](https://apexst77.github.io/RL/David_Silver/2/) 
- [3] [Planning by Dynamic Programming](https://apexst77.github.io/RL/David_Silver/3/) : **this post** 
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

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-02.jpg){: width="90%" height="90%"}{: .align-center}

***

### What is Dynamic Programming?

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-03.jpg){: width="90%" height="90%"}{: .align-center}

**Dynamic Programming** : 

- complex problem을 해결하는 method(방법론)중 하나
- complex probelm을 여러 문제로 나누어 해결한다

***

### Requirements for Dynamic Programming

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-04.jpg){: width="90%" height="90%"}{: .align-center}

Dynamic Programming은 **2가지 조건**이 성립할 때 굉장히 보편적인 해결법이다.

1. **Optimal substructure** : complex problem이 작은 문제로 나눌 수 있어야 한다.
2. **Overlapping subproblems** : 하나의 subproblem에 대한 solution이 reused될 수 있어야 한다.

**MDP**의 경우 위 두 조건을 모두 만족하기에 Big MDP의 경우 **Dynamoc Programming**을 통해 해결할 수 있다.

- **Bellman Equationn**의 식은 reculsive decomposition(재귀적인 분해)를 보여준다 : **Optimal substructure**
- **Value Function**는 Solution이 stores(저장)돠고 reuses(재사용)된다 : **Overlapping subproblems**

***

### Planning by Dynamic Programming

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-05.jpg){: width="90%" height="90%"}{: .align-center}

**Dynamic Programming**은 MDP에 대해 **full knowledge**(모든 것을 알고있다)라고 가정한다

즉 **DP(Dynamic Programming)**은 MDP의 **Planning**을 위해 이용된다: (Lecture_1 참고)

**For Prediction**(policy가 주어지고 Value Function을 구한다):

- **Input**으로 MDP가 주어지고 Policy가 주어진다.
- 혹은 Policy에 대한 MRP가 주어진다.(Lecture _2 참고)
- **Output**은 Value function $v_{\pi}$

**For control**(MDP에 대해 최적의 Policy를 찾는다.):

- **Input**으로 MDP가 주어진다.
- **Output**은  $v_{\*}$ 와  ${\pi}_{\*}$ 

***

### Other Applications of Dynamic Programming

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-06.jpg){: width="90%" height="90%"}{: .align-center}

**Dynamic Programming**은 **Planning 뿐만 아니라** 그외 많은 문제의 해결에 쓰인다.

***

### lterative Policy Evaluation

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-07.jpg){: width="90%" height="90%"}{: .align-center}

**Problem** : 주어진 **Policy $\pi$**를 평가한다.

**Solution** : **Bellman Expectation**을 반복적으로 backup

시작은 모든 Value Function을 **무작위로 초기화**한다

그 후 다음 과정을 **반복**한다

Using **synchronous backups**:

- k+1번의 **모든 단계 각각**에서(:why synchronous)
- 모든 State에 대해서
- **$v_{k}(s')$**로 부터 **$v_{k+1}(s)$**를 업데이트 한다
- s'은 s에서 Action에 의해 파생가능한 다음 State이다

위의 과정을 계속 반복할시 결과적으로 **$v_{\pi}$**에 수렴한다

***

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-08.jpg){: width="90%" height="90%"}{: .align-center}

다음 식의 의미를 살펴보면:

- **Step k, State s**에서
- **모든 Action**에 대하여
- State s에서 **정책 $\pi$에 의해 Action a가 선택될 확률**과
- [**immediate Reward** + Action에 의해 파생되는 모든 **State s'에 대하여** **discounted factor에 의해 가감된 Value Function의 기댓값**] 의 곱을 더한다.
- 즉 State s에서 Policy에 대하여 [**immediate Reward** + Action에 의해 파생되는 모든 **State s'에 대하여** **discounted factor에 의해 가감된 Value Function의 기댓값**]의 기댓값을 구한다.
- 즉 State s에서 Policy에 대하여 [각각의 Action에 대한 **Bellman식**]의 기댓값을 구한다.

이러한 과정을 **반복**할 시 **임의로 초기화된 Value Function이 점점 $v_{\pi}$에 수렴**하게 된다.

***

### Evaluating a Random Policy in the Small Gridworld

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-09.jpg){: width="90%" height="90%"}{: .align-center}

**Prediction Problem**

- **MDP**:
  - 14개의 nonterminal State
  - Terminal State(2개의 검은 칸 but 2개가 동일 State)
  - 1 step마다 Reward는 -1
- **Policy**
  - **좌(n),우(e),위(s),아래(w)** 각각 **0.25확률**
- **Value Function을 구해야한다**

***

### Iterative Policy Evaluation in Small Gridworld

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-10.jpg){: width="90%" height="90%"}{: .align-center}

**k = 0**

- 초기화는 모든 State의 Value Function을 0으로

**k = 1**

- 모든 칸에 대하여 1회 backup
- 식을 대입해 보면 **terminal state 빼고 전부 -1**이 되는 이유를 알 수 있음
  - **immediate Reward**만 -1 나머지는 전부 0
  - **terminal State**의 경우는 가능한 Action이 없기에 0

**k = 2**

- 왼쪽 아래를 원점으로 하고 **(1,3) 지점이 -1.75(=-1.7)**가 되는 이유를 생각하여 보자
- **$v_{k+1}(s)$**를 구하는 식에 넣어보면 **모든 Action(좌우,우,위,아래 4가지)**에 대하여 각각 0.25 확률로 시행
- immediate Reward는 모두 -1
- **discounted factor(γ)**는 1, 따라서 **s'의 value function**은 각각 위: -1, 아래 : -1, 좌: 0, 우: -1
- 위가 -1인 이유는 제자리에 멈추기 때문이다.(제자리의 value가 -1)
- 따라서 식은 $0.25\*\{(-1+1\*1\*-1)+(-1+1\*1\*-1)+(-1+1\*1\*0)+(-1+1\*1\*-1))\} = -1.75$

***

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-11.jpg){: width="90%" height="90%"}{: .align-center}

**k=3**

- k=2의 과정을 한번더 거친 상태이다
- 소수점 1자리까지 표현했다는 것에 유의하자
- 이미 Value Function을 통해 optimal policy를 확인할 수 있게 되었다.
  - value에 대하여 greedy하게 움직이면 optimal policy를 얻을 수 있다.

**k=10**

- 학습이 더욱 진행된 모습이다
- Terminal state에서 멀리 떨어진 State일수록 Value Function이 작아짐을 확인할 수 있다

**k=∞**

- 최종적으로 각 State가 $v_{\pi}$를 나타내고 있다.

***

### How to Improve a Policy

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-12.jpg){: width="90%" height="90%"}{: .align-center}

임의의 **policy $\pi$**가 주어졌을 때

- policy $\pi$를 평가한다
- 평가된 value function에 대하여 greedy하게 움직이는 새로운 policy ${\pi}'$을 구한다

Small Gridworld에서는 위과정에서 **policy ${\pi}'$**은 **policy ${\pi}^{\*}$**에 수렴한다

하지만 **일반적인 경우**는 두과정의 **반복을 여러번** 거쳐야한다

하지만 결과적으로는 **policy ${\pi}^{\*}$**에 수렴한다

***

### Policy Iteration

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-13.jpg){: width="90%" height="90%"}{: .align-center}

**Policy evaluation**:

- 주어진 **policy**에 대해 **${v}^{\*}$**를 구한다

**Policy Improvement**:

- 주어진 **value function**에 대해 **${\pi}{\'}$**를 구한다

위 두과정을 반복할시 결과적으로:

-  **${v}^{\*}$**는 **${v}^{\pi_{\*}}$**로 수렴하며
-  **${\pi}^{\'}$**은 **${\pi}^{\*}$**로 수렴하게된다
- 이 과정을 **Policy Iteration**이라고 한다.

***

### Jack's Car Rental

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-14.jpg){: width="90%" height="90%"}{: .align-center}

**State** : 2개의 위치가 있고 각 위치에는 최대 20개의 차가 있을 수 있다

- 1지점에는 푸아송 분포에 따라 빌리는 손님이 평균 3명오고 반납하는 사람 또한 평균 3명이다
- 2지점에서는  푸아송 분포에 따라 빌리는 손님이 평균 4명오고 반납하는 사람은 평균 2명이다
- **????**
  - 문제 이해가 어려울 수 있는데 간단히 설명하자면 1, 2를 KT렌터카 지점이라 생각하자
  - 1지점에서 빌린차를 1지점에 반납할 수도 있고 그 반대도 가능하며 위 문제에서 1, 2 지점만을 State에 두었지만 나가는 차가 들어오는 차보다 많은 것을 보아 3지점, 4지점, 등 더 많은 지점이 있을 것이다
  - 위 문제는 상황으로만 보면 결과적으로 1,2 지점의 차는 모두 사라지겠지만 그 때까지 가장 많은 돈을 벌 수 있는 Policy를 물어보는 듯 하다 
  - 문제의 **조건이 부족**한 것 같다

**Action** : 최대 5개의 차를 저녁(운영을 안하는 시간)동안 한지점에서 다른지점으로 옮긴다

**Reward** : 차 한번 빌려주면 10$를 번다 / 반납은 영향 X

***

### Policy Iteration in Jack's Car Rental

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-15.jpg){: width="90%" height="90%"}{: .align-center}

**그림설명**:

- 다음 그림은 Policy를 20 x 20 격자로 나타낸 것이다(f(x,y)함수이다)
- x축은 2번째 지점의 차의 수 y축은 1번째 지점의 차의 수를 나타낸다
- 다음 격자에서 차의 수를 대입했을 때 나오는 숫자 만큼 1지점에서 2지점으로 차를 옮긴다(만약 음수일 경우 반대로 2지점에서 1지점으로 차를 옮긴다) 

초기 **Policy ${\pi}_0$**는 **아무것도 안옮기는** 방법을 택한다

-  **${\pi}_0$**를 그림으로 표현하면 아래와 같다
- **${\pi}_0$**의 value function을 **Improve**하여 **${\pi}_1$**을 구하였다

두번째 Policy **${\pi}_2$** 또한 마찬가지이다

- **${\pi}_1$**를 **Evaluate**한 value function을 **Improve**하여 **${\pi}_2$**을 구하였다

**결과적으로**:

- **$V_4$(=${\pi}_1$를 Evaluate한 value function)** 그림을 보자
- 20, 20 일때 value가 가장 큰 것을 확인할 수 있다
- 20, 20 인 State는 규칙에 의해 점차 왼쪽으로 이동할 것이다(2지점은 나가는 양이 들어오는 양보다 많으니 평균적으로 차의 수가 감소하게 된다)(1지점은 유지)
- 왼쪽으로 이동한다면 Policy에 의해 1지점의 차를 2지점으로 보내게 된다(y축 감소 x축 증가)
- 지속적으로 x축이 감소하다 Action에 의해 y축이 감소하고 x축이 증가한다
- 결과적으로 0,0 지점으로 이동함

***

### Policy Improvement

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-16.jpg){: width="90%" height="90%"}{: .align-center}

**Policy Improvement**에 의해 **Policy**를 구하면 과연 더 좋은 **Policy**가 구해지는가?

**$a = {\pi}(s)$**라는 **deterministic policy(결정적 정책)**을 한가지 고려해보자

우리는 **${\pi}$**를 **Evaluate**한 **$q_{\pi}(s,a)$**에 대하여 **greedy하게 acting**하여 **${\pi}'$**을 구하여 Policy를 Improve 할 수 있음을 보일 것이다

q는 acting_value function이며 v는 state_value function이다 

- 이때 정의에 의해 **$q_{\pi}(s,{\pi}(s))$**는 state s에서 정책에 따라 구해진 행동을 했을 때의 value임으로 **$v_{\pi}$**와 같다
- 또한 위에서 **${\pi}'$**의 정의를 **$q_{\pi}(s,a)$**에 대하여 **greedy하게 acting**하는 방법이라고 정의 하였음으로 State S에서 가능한 모든 Action에 대해서 **$q_{\pi}(s,a)$**의 최대값은 **$q_{\pi}(s,{\pi}'(s))$**와 같다
- 이때 **{\pi}(s)**은 최적의 Action이 아님으로 **$q_{\pi}(s,a)$**의 최대값(max)은 **$q_{\pi}(s,{\pi}(s))$** 보다 크다
- 따라서 **$q_{\pi}(s,{\pi\'}(s))$**는 **$v_{\pi}$**보다 크다는 것을 알 수 있다(1)

이를 통해 **$v_{\pi\'}$**은 **$v_{\pi}$**보다 크거나 같다는 것을 보이자

- **$q_{\pi}(s,{\pi}'(s))$**는 **$v_{\pi}$**보다 크다(by 1)
- **$q_{\pi}(s,{\pi\'}(s))$**는 State s에서 [**${\pi}'$**에 의해 움직였을 때 받는 immediate reward]와 [dicounted factor x $v_{\pi}(S_{t+1})$]의 합의 기대값과 같다(2)
- 이때 [dicounted factor x $v_{\pi}(S_{t+1})$]보다 [dicounted factor x $q_{\pi}(S_{t+1},{\pi}'(S_{t+1}))$] 가 더 크다(1과 같은 논리)
- 위의 과정을 계속해서 반복 가능하다
- 결과적으로 **$v_{\pi}$**는 policy **${\pi}'$**에 대한 **$R_{t+1}$**부터 **$R_{∞}$**까지 합보다 작다
- 이때 policy **${\pi}'$**에 대한 **$R_{t+1}$**부터 **$R_{∞}$**까지 합은 **$v_{\pi\'}$**와 같다

결과적으로 **$v_{\pi\'}$**은 **$v_{\pi}$**보다 크거나 같다

***

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-17.jpg){: width="90%" height="90%"}{: .align-center}

**if improvements stop**(policy가 더이상 improve하지 않는다면)

결과적으로 **$v_{\pi}$**는 모든 State에서 **$v_{\*}$** 와 같아진다

따라서 **policy $\pi$** 는 optimal policy이다

**+**

***

### Modified Policy Iteration

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-18.jpg){: width="90%" height="90%"}{: .align-center}

반드시 policy evaluation을 **$v_{\pi}$**까지 근사시켜야 할까?

- No, 적당한 value function을 통해 policy를 improve시켜도 된다

적당한 정지 조건을 도입해야될까, 혹은 k(ex.3)번째 반복에서 멈춰도 될까?

**결론: 모두 합리적인 방법이다**

***

### Generalised Policy Iteration

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-19.jpg){: width="90%" height="90%"}{: .align-center}

policy iteration을 **일반화**하면 policy evaluation과 policy improvement가 가능한 다른 알고리즘이 존재한다면 이 경우에도 Policy Iteration이 가능하다	

***

### Principle of Optimality

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-20.jpg){: width="90%" height="90%"}{: .align-center}

**optimal policy**는 다음 두 요소로 나뉜다:

- optimal한 first Action **$A_{\*}$**
- 그리고 first Action 이후 State s'부터 따라야 할 **optimal policy**

**Principle of Optimality**

다음 두 명제는 **if and only if(필요충분조건)**이다:

- Policy **${\pi}(a\|s)$**는 State s에서 optimal value를 얻는다
- **$v_{\pi}(s) = v_{\*}(s)$**를 만족한다

즉 **$v_{\pi}(s) = v_{\*}(s)$**이면 **${\pi}(a\|s)$**는 State s에서 optimal value를 얻고 

**${\pi}(a\|s)$**가 State s에서 optimal value를 얻었다면 **$v_{\pi}(s) = v_{\*}(s)$**인 것이다

**Pf**:

- **+**

***

### Deterministic Value Iteration

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-21.jpg){: width="90%" height="90%"}{: .align-center}

**$v_{\*}(s')$**를 안다고 가정할 때 1step 앞 State s의 **$v_{\*}(s)$**는 2장의 Bellman Optimality Equation을 통해 구할 수 있다

s를 통해 또한 s 이전 step State의 **$v_{\*}$**를 구할 수 있다

이떄 **$v_{\*}$**에 대해 수렴함은 증명되었다;

***

### Example: Shortest Path

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-22.jpg){: width="90%" height="90%"}{: .align-center}

다음은 

***

### Iterative Policy Evaluation in Small Gridworld

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-23.jpg){: width="90%" height="90%"}{: .align-center}



***

### Iterative Policy Evaluation in Small Gridworld

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-20.jpg){: width="90%" height="90%"}{: .align-center}



***

### Iterative Policy Evaluation in Small Gridworld

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-20.jpg){: width="90%" height="90%"}{: .align-center}



***

### Iterative Policy Evaluation in Small Gridworld

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-20.jpg){: width="90%" height="90%"}{: .align-center}



***

### Iterative Policy Evaluation in Small Gridworld

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-20.jpg){: width="90%" height="90%"}{: .align-center}



***

### Iterative Policy Evaluation in Small Gridworld

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-20.jpg){: width="90%" height="90%"}{: .align-center}



***

### Iterative Policy Evaluation in Small Gridworld

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-20.jpg){: width="90%" height="90%"}{: .align-center}



***

### Iterative Policy Evaluation in Small Gridworld

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-20.jpg){: width="90%" height="90%"}{: .align-center}



***

### Iterative Policy Evaluation in Small Gridworld

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-20.jpg){: width="90%" height="90%"}{: .align-center}



***

### Iterative Policy Evaluation in Small Gridworld

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-20.jpg){: width="90%" height="90%"}{: .align-center}



***

### Iterative Policy Evaluation in Small Gridworld

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-20.jpg){: width="90%" height="90%"}{: .align-center}



***

### Iterative Policy Evaluation in Small Gridworld

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-20.jpg){: width="90%" height="90%"}{: .align-center}



***

### Iterative Policy Evaluation in Small Gridworld

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-20.jpg){: width="90%" height="90%"}{: .align-center}



***

### Iterative Policy Evaluation in Small Gridworld

![T]({{ site.url }}{{ site.baseurl }}/assets/images/David_Silver/3/DP-20.jpg){: width="90%" height="90%"}{: .align-center}