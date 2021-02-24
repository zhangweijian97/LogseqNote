---
title: Inception Score
---

## Name
### [[Inception Score]]
## Type
### #PermanentNote
## 笔记
### 两个标准来衡量GAN的性能
#### quality of the generated images
##### $p(y|x)$具有低熵 [[Entropy]]，高预测性
#### diversity of the generated images
##### $p(y)$ 具有高熵，分布均匀，图像多样
### 公式
####
$$
\mathbf{I S}(G)=\exp \left(\mathbb{E}_{\mathbf{x} \sim p_{g}} D_{K L}(p(y \mid \mathbf{x}) \| p(y))\right)
$$
### 计算
#### 生成N个图片
#### 输入到Inception V3
#### 输出的向量（1000维）即图片属于各个类别的概率分布$p(y|x)$
#### 求平均得到边缘分布 $p(y)$
#####
$$
\hat{p}(y)=\frac{1}{N} \sum_{i=1}^{N} p\left(y \mid \mathbf{x}^{(i)}\right)
$$
#### 计算KL散度
#####
$$
D_{K L}(P \| Q)=\sum_{i} P(i) \log \frac{P(i)}{Q(i)}
$$
#### 上面公式的期望用 求和然后平均 来替代
### 缺点
#### 略
## 联想
### 这条笔记的意义，作用
### 与其他笔记的联系和区别，大量引用
### 溯源，从哪里产生的想法
# 入档
## #EvaluationMethod #MachineLearning #GAN
# 索引
## 博客文章 [Inception Score原理及其代码实现](https://zhuanlan.zhihu.com/p/263652288)
## Github Repo [Inception Score Pytorch](https://github.com/sbarratt/inception-score-pytorch)
## Arxiv [Improved Techniques for Training GANs](https://arxiv.org/abs/1606.03498)
##
