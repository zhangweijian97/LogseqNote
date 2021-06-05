---
title: RL Chapter 7 n-step Bootstrapping
---

- 完全回报
	-
	  $$G_t = R_{t+1}+\gamma R_{t+2}+\cdots$$
- 一步回报
	-
	  $$G_{t:t+1} = R_{t+1}+\gamma V_t(S_{t+1})$$
- n步回报
	-
	  $$G_{t:t+1} = R_{t+1}+\gamma R_{t+2} + \cdots + \gamma^n V_{t-n-1}(S_{t+n})$$
- 使用n步回报的状态值更新公式
	-
	  $$V_{t+n}(S_t)=V_{t+n-1}(S_t)+\alpha [G_{t:t+n}-V_{t+n-1}(S_t)]$$
-