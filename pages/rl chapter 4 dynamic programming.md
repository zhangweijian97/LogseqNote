---
title: RL Chapter 4 Dynamic Programming
---

- 回顾v的bellman方程（迭代计算方程）
-
  $$v_\pi(s) = \sum_a\pi(a|s)\sum_{s',r}p(s',r|s,a)[r+\gamma v_\pi(s')]$$
- 原来如此，上面的没有时刻因素，是理论上收敛之后不会再变动了的写法
- 引入时刻之后，用同一个方程，但是可以表示为用前一刻的v来迭代计算到下一刻的v，这才是真正的迭代计算方程，称为迭代策略评估：
-
  $$v_{k+1}(s) = \sum_a\pi(a|s)\sum_{s',r}p(s',r|s,a)[r+\gamma v_k(s')]$$
- 然后是q的迭代计算公式
-
  $$q_{k+1}(s,a) = \sum_{s',r}p(s',r|s,a)[r+\gamma \sum_{a'}\pi(a'|s')q_k(s',a')]$$
- 以上两个是策略迭代
- 另外有值迭代，是从最优方程组改过来的
-
  $$v_{k+1}(s) = \max_a\sum_{s',r}p(s',r|s,a)[r+\gamma v_k(s')]$$
-
  $$q_{k+1}(s,a) = \sum_{s',r}p(s',r|s,a)[r+\gamma \max_{a'} q_k(s',a')]$$
-