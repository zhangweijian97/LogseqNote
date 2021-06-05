---
title: RL Chapter 3 Finite Markov Decision Processes
---

- 已知策略pi和动作值函数q，可以直接写出在t时刻，v关于q的公式，即做出动作的概率pi乘上动作的回报q的加和
-
  $$v_\pi(s) = \sum_a\pi(a|s)q_\pi(s,a)$$
- 利用v的定义公式，和Rt+1的期望公式，能写出v的迭代计算公式，也是bellman方程
-
  $$v_\pi(s) = \sum_a\pi(a|s)\sum_{s',r}p(s',r|s,a)[r+\gamma v_\pi(s')]$$
- 已知所有的v，能得到q关于v的公式，即做一个动作的期望回报，是做完这个动作可能到达的所有状态的概率乘上获得的回报和衰减后的状态值函数v的加和
-
  $$q_\pi(s,a) = \sum_{s',r}p(s',r|s,a)[r+\gamma v_\pi(s')]$$
- 已知q关于v的公式，带入最前面那个v关于q的公式，就能得到q的迭代计算公式，即q的bellman方程。
-
  $$q_\pi(s,a) = \sum_{s',r}p(s',r|s,a)[r+\gamma \sum_{a'}\pi(a'|s')q_\pi(s',a')]$$
- 最优状态值函数等于该状态下的最优动作值
-
  $$v_*(s) = \max_a\sum_{s',r}p(s',r|s,a)[r+\gamma v_*(s')]$$
- 最优动作值函数，把原来的动作值函数带入上面
-
  $$q_*(s,a) = \sum_{s',r}p(s',r|s,a)[r+\gamma \max_{a'} q_*(s',a')]$$
- 最优方程组：
-
  $$v_*(s) = \max_a(q_*(s,a))$$
-
  $$q_*(s,a) = \sum_{s',r}p(s',r|s,a)[r+\gamma v_*(s)]$$
-
  $$\pi_*(s) = \arg \max_a q_*(s,a)$$
-
  $$\pi_*(s) = \arg \max_a \sum_{s',r}p(s',r|s,a)[r+\gamma v_*(s)]$$
- 如果根据状态s和动作a有一个确定的奖励r，那就不用求和了，所以上面的一些公式改成：
-
  $$v_\pi(s) = \sum_a\pi(a|s)\sum_{s'}p(s'|s,a)[r(s,a)+\gamma v_\pi(s')]$$
-
  $$v_*(s) = \max_a\sum_{s'}p(s'|s,a)[r(s,a)+\gamma v_*(s')]$$
-
  $$q_\pi(s,a) = \sum_{s'}p(s'|s,a)[r(s,a)+\gamma \sum_{a'}\pi(a'|s')q_\pi(s',a')]$$
-
  $$q_*(s,a) = \sum_{s'}p(s'|s,a)[r(s,a)+\gamma \max_{a'} q_*(s',a')]$$
-