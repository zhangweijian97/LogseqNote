---
title: DME Presentation
---

## [[DME presentation information]]
:PROPERTIES:
:id: 603a5e9b-b946-41ee-9a71-940f862daeac
:END:
## DME presentation team information
### s2119299-weijian zhang
### s2018229-xi zhao
### s2093718-yunbo liu
### s2060292-shifeng xu
## [[DME presentation paper outline]]
## 文章分配 分割
### Background
#### 123
### Method
#### 45
### Experiment
#### 6
### Contribution
#### 7
## 资源
### 中文博客 [详解独立成分分析](https://j.mp/3bloY8M)
## [[DME Presentation 第一遍 理解内容 收集要素]]
## [[DME Presentation 第二遍 删繁就简]]
## 演讲稿
### Now we have the ICA model that represents the observed variable x and unknow independent component s. Next, we need an objective function to find out the solutions of the independent components.
### The Objective function is to maximise non-gaussianity. 
As we know, the central limit theorem is that the distribution of a sum of independent random variables tends to be a Gaussian distribution.
Let's define a variable y, which is a linear combination of x. As you can see, y is also a linear combination of s. 
The central limit theorem tells us y is more gaussian than any of s. And if y equals one of the s, it is least gaussian. 
Therefore, if we find all the parameters that maximize the non-gaussianity of this equation, we do find the independent components.
Here arise another question, that is, how to measure the non-gaussianity?
### We have following measurements
#### The first is to maximize the kurtosis.
A gaussian random variable has 0 kurtosis, while for most nongaussian random variables, kurtosis is nonzero.
Using this property, we can measure the non-gaussianity by the absolute value of kurtosis.
#### The second is to maximize neg-entropy
A fundamental result of information theory tells us a gaussian variable has the largest entropy among all random variables of equal variance.
Therefore, we could first preprocess our data to make them be equal variance, then apply this equation to find out the solutions.
As this equation is hard to compute, in practice, we use these two equations to approximate it.
#### The third one is to minimize the mutual information of y
![2021_03_07_image.png](https://cdn.logseq.com/%2Fd86993cf-c7b9-4bba-9ff6-fe2074f1857cd2932e67-81a8-4337-af27-2e3e406469e62021_03_07_image.png?Expires=4768750914&Signature=c49Q~iZgjFyQqMuALZMLxBDYfkk7oHPWJ-74jzvBSxapzihVh~fvjEOjFvMBlAPAYDffstqgEiJnLJDCcpSYSTqNFjJoIKhnLN36LQ~45h2U7hDzWjo6ZdO14NtcVeBPNlKOYqDt64pB2g0ll0Qiw6qOJ7mTpKHhJI6-RLfQCjby~LUdHrRWRLF3M6wYMoMd6d-rvL5-XD97E4TPwNF~O6honIbIC0KOkUI7d2q6IB9JWUxBYk24J3bE3XKBUsLlvH2S6W~SxJugl6pcSN~YfOkhq2qQp-xTScRV-g-kIPVat2XYsW1EsBVo-6L0okSN9HAOaLN~8zoKjFSvda2yjQ__&Key-Pair-Id=APKAJE5CCD6X7MP6PTEA) This equation measure the
讲
###
##
�够简化计算
###
##
