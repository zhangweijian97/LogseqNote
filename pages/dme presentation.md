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
## 第二遍 删繁就简
### 第一部分
#### 标题
##### 优化问题：最大化非高斯性
#### 内容
##### 中心极限定理
###### 在一定条件下，独立随机变量之和的分布倾向于高斯分布。
##### 所以如果我们定义y是x的线性组合
###### 
$$
y=\mathbf{w}^{T} \mathbf{x}=\mathbf{w}^{T} \mathbf{A} \mathbf{s}=\mathbf{z}^{T} \mathbf{s}
$$
##### 如公式所示所以y也是s的线性组合
##### 一方面，y比s更接近高斯分布
##### 另一方面，当z只包含一个非零元素时，
###### 
$$\mathbf{z}=\left[ \begin{matrix} 0 \\ \vdots \\ \mathbf{z}_{i} \\ \vdots \\ 0\end{matrix} \right]$$
###### 
$$y= \mathbf{s}_i$$
##### 这时，y的非高斯性最大 nongaussianity is maximized
##### 所以我们得到一个优化问题：找到一个w，使得 $$y=\mathbf{w}^{T} \mathbf{x}$$ 的非高斯性最大
### 第二部分
#### 标题
##### 如何衡量非高斯性
#### 内容
##### 最大化峰度
####### 
$$
\operatorname{kurt}(y)=E\left\{y^{4}\right\}-3\left(E\left\{y^{2}\right\}\right)^{2}
$$
###### 高斯变量
####### 零峰度，图，高斯分布
###### 非高斯变量
####### 负峰度，图，均匀分布
####### 正峰度，图，拉普拉斯分布
###### 所以用峰度的绝对值（或平方）来衡量非高斯性，值越大，非高斯性越高
###### 缺点（可选）
##### 最大化负熵
###### 熵，公式
####### 
$$
H(Y)=-\sum_{i} P\left(Y=a_{i}\right) \log P\left(Y=a_{i}\right)
$$
####### 
$$
H(\mathbf{y})=-\int f(\mathbf{y}) \log (f(\mathbf{y})) d \mathbf{
########### 在信息论中有个基本的结论：在所有方差相等的随机变量中，高斯变量的熵最大。
###### 我们用负熵来衡量非高斯性，公式
####### 
$$
J(\mathbf{y})=H\left(\mathbf{y}_{\text {gauss }}\right)-H(\mathbf{y})
$$
###### 同样的，负熵越大，非高斯性越大
###### 因为上述分布很难得到，我们使用近似负熵
####### 高阶矩
######## 
$$
J(y) \approx \frac{1}{12} E\left\{y^{3}\right\}^{2}+\frac{1}{48} k u r t(y)^{2}
$$
####### 基于最大熵原理
######## 
$$
J(y) \approx \sum_{i=1}^{p} k_{i}\left[E\left\{G_{i}(y)\right\}-E\left\{G_{i}(v)\right\}\right]^{2}
$$
###### 优点（可选）
##### 最小化互信息
###### 公式
####### 
$$
I\left(y_{1}, y_{2}, \ldots, y_{m}\right)=\sum_{i=1}^{m} H\left(y_{i}\right)-H(\mathbf{y})
$$
###### 如果y_{i}是独立的，那么它们彼此之间就没有任何信息，计算结果是0
##### 最大化似然
###### log似然
#######
$$
L=\sum_{t=1}^{T} \sum_{i=1}^{n} \log f_{i}\left(\mathbf{w}_{i}^{\mathrm{T}} \mathbf{x}(t)\right)+T \log |\operatorname{det} \mathbf{W}|
$$
###### 神经网络输出熵 Infomax Principle
####### 
$$
L_{2}=H\left(\phi_{1}\left(\mathbf{w}_{1}^{T} \mathbf{x}\right), \ldots, \phi_{n}\left(\mathbf{w}_{n}^{T} \mathbf{x}\right)\right)
$$
 投影跟踪
###### 图片
##### 其中，负熵，互信息，似然都是理论上等价的
### �
### 第三部分
标题
##### 数据预处理
#### 内容
##### 中心化
##### 白化
##### 其他处理
##### 好处是能够简化计算
###
##
