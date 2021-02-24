---
title: Inception Score
---

## Name
### [[Inception Score]]
## Type
### #PermanentNote
##
---
## Temporary notes 临时笔记
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
###
#
---
# 大段文字描述，不进行引用
# 联想
## 这条笔记的意义，作用
## 与其他笔记的联系和区别，大量引用
## 溯源，从哪里产生的想法
# 入档
## 加合适的标签（归入对应的卡片盒）
## #EvaluationMethod #MachineLearning #GAN
# 索引
## 信息来源，如参考文献，书籍，论文，网络文章
## [Inception Score原理及其代码实现](https://zhuanlan.zhihu.com/p/263652288)
##
