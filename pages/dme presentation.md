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
Mutual information is a natural measure of the dependence between random variables.
It is always non-negative, and zero if and only if the variables are statistically independent.
Therefore, we can minimize this equation to find out the solution.
#### The forth one is to maximize likelihood.
Here is the formula of log likelihood and its expectation. 
You can see it is almost the same as the equation of mutual information. The missing entry is a constant. 
Therefore, these two methods are equivalent. 
Addionally, researchers proved that maximizing the output entropy of a neural network is equivalent to maximizing the log likelihood. 
This is called the Infomax Principle. You can also maximize this equation to find out the solution.
#### The last one is
讲
###
##
�够简化计算
###
##
