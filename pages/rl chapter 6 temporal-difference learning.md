---
title: RL Chapter 6 Temporal-Difference Learning
---

- TD的V更新公式，只需要一个时刻后立刻计算。而蒙特卡罗要在t时刻后
  TD 更新
	-
	  $$V(S_t)=V(S_t)+\alpha [R_{t+1}+\gamma V(S_{t+1})-V(S_t)]$$
- TD 误差
	-
	  $$\delta_t=R_{t+1}+\gamma V(S_{t+1})-V(S_t)$$
- off-policy的版本
	-
	  $$V(S_t)=V(S_t)+\alpha [\rho_{t:t}R_{t+1}+\rho_{t:t}V(S_{t+1})-V(S_t)]$$
- Sarsa，on-policy TD 控制，估计Q
- on-policy的动作值增量更新公式
	-
	  $$Q(S_t,A_t)=Q(S_t,A_t)+\alpha [R_{t+1}+\gamma Q(S_{t+1},A_{t+1})-Q(S_t,A_t)]$$
- Q-learning，off-policy TD 控制算法
	-
	  $$Q(S_t,A_t)=Q(S_t,A_t)+\alpha [R_{t+1}+\gamma \max_a Q(S_{t+1},a)-Q(S_t,A_t)]$$
- 期望Sarsa
	-
	  $$Q(S_t,A_t)=Q(S_t,A_t)+\alpha [R_{t+1}+\gamma \sum_a\pi(a|S_{t+1})Q(S_{t+1},a)-Q(S_t,A_t)]$$
- TD 更新
  later:: 1614611635616
-
  $$V(S_t)=V(S_t)+\alpha [R_{t+1}+\gamma V(S_{t+1})-V(S_t)]$$
- TD 误差
-
  $$\delta_t=R_{t+1}+\gamma V(S_{t+1})-V(S_t)$$
- off-policy的版本
-
  $$V(S_t)=V(S_t)+\alpha [\rho_{t:t}R_{t+1}+\rho_{t:t}V(S_{t+1})-V(S_t)]$$
- Sarsa，on-policy TD 控制，估计Q
-
  $$V(S_t)=V(S_t)+\alpha [R_{t+1}+\gamma V(S_{t+1})-V(S_t)]$$
- TD 误差
-
  $$\delta_t=R_{t+1}+\gamma V(S_{t+1})-V(S_t)$$
- off-policy的版本
-
  $$V(S_t)=V(S_t)+\alpha [\rho_{t:t}R_{t+1}+\rho_{t:t}V(S_{t+1})-V(S_t)]$$
- Sarsa，on-policy TD 控制，估计Q
- on-policy的动作值增量更新公式
  $$Q(S_t,A_t)=Q(S_t,A_t)+\alpha [R_{t+1}+\gamma Q(S_{t+1},A_{t+1})-Q(S_t,A_t)]$$
  Q-learning，off-policy TD 控制算法
  $$Q(S_t,A_t)=Q(S_t,A_t)+\alpha [R_{t+1}+\gamma \max_a Q(S_{t+1},a)-Q(S_t,A_t)]$$
  期望Sarsa
  $$Q(S_t,A_t)=Q(S_t,A_t)+\alpha [R_{t+1}+\gamma \sum_a\pi(a|S_{t+1})Q(S_{t+1},a)-Q(S_t,A_t)]$$