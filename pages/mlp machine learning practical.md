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
##### 把我们的模型丢去ImageNet训练，生成它的图片，然后跑Inception Score和FID
##### 原因
######
#+BEGIN_QUOTE
不能在一个数据集上训练分类模型，用来评估另一个数据集上训练的生成模型
#+END_QUOTE
###### Inception V3 是在 ImageNet 上训练的判别模型
###### 我们的模型是在F2T数据集上训练的生成模型
###### 数据集不同，把我们生成的图像放进Inception V3是没有意义的
#### 方案二
##### 把预训练的Inception V3拿过来，在我们的数据集上fine tuning一下（Text2FaceGAN在CelebA上微调），再评估。这样就是直接评估我们的数据集生成的图片。
###### **问题**是我们的数据集太小了，微调需要足够的数据集，Text2FaceGAN说要50M，网上则说每类至少100张
#### 问题
##### 要用tensorflow的还是pytorch的
##### 要用gpu吗，看github，两个都可以用gpu
####
