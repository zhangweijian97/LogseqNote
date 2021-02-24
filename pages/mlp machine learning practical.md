---
title: MLP Machine Learning Practical
---

## MLP Project
:PROPERTIES:
:id: 6036865a-0182-4f5d-b3ed-7c4a243beefc
:END:
### 前略
### 评估方法
#### 两个方法
##### [[Inception Score]]
##### [[Fréchet Inception Distance]]
#### 方案一
##### 把我们的模型丢去Inception Net V3，然后直接跑Inception Score
##### 因为
#+BEGIN_QUOTE
不能在一个数据集上训练分类模型，用来评估另一个数据集上训练的生成模型
#+END_QUOTE
##### Inception V3 是在 ImageNet 上训练的
#### 方案二
#####
