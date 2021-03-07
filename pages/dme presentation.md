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
讲
###
##
�够简化计算
###
##
