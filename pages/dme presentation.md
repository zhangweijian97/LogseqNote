---
title: DME Presentation
---

## {{embed ((603a5b96-196e-4dca-92ff-a2169fb0b786)) }} 

## {{embed ((603a5e9b-b946-41ee-9a71-940f862daeac)) }}
:PROPERTIES:
:now: 1614438097297
:later: 1614438094793
:END:
## Presentation Details
### For the presentations, we expect that
#### each team submits (only once) a single video file
##### the video should be in MP4 format, and should be at a decent resolution (at least VGA)
##### not too large—the submission form stipulates a 100Mb file size limit
#### the video should be at most 8 minutes long
#### the video should be in “normal” speed; i.e not sped up to fit time limit
#### the first slide of your presentation should list
##### paper title
##### team ID (from the paper assignments)
##### UUN and names of the team members no specific constraints on formatting or any other info you wish to include
#### each team member should present as part of the video.
##### We suggest splitting into contribution, background, methods, and experiments.
### upload to [presentation slides form](https://forms.office.com/Pages/ResponsePage.aspx?id=sAafLmkWiUWHiRCgaTTcYRf8UZzTD55LtoM4GyB39n5UQTAxVDk4WFU2WEcwUktCT1hZOUtBNEdCViQlQCN0PWcu)
### record tool recommendation
#### using Open Broadcaster Studio (OBS)
#### screen record with ffmpeg or similar command line tools
#### using Office365 (Slide Show -> Record Slide Show)
#### using Zoom or BBCollab
#### any other method of choice (e.g. Jitsi+Dropbox)
## Marking
### 3 parts
#### presentation,
#### performance at the Q&A session, and
#### (weighted) audience feedback
:PROPERTIES:
:later: 1614954227731
:END:
### marking criteria
#### style: fluency, coherence within team, and audience engagement
understanding: characterise the paper faithfully and in an accessible way
slide design: structure, key points, figures, and legibility
### engagement
#### indicate their choice of paper and provide **a brief 1-paragraph summary **along with **a brief list (2-3) of questions** about it, using the [Engagement (Pre) form](https://forms.office.com/Pages/ResponsePage.aspx?id=sAafLmkWiUWHiRCgaTTcYW0VF5r2yGtKrh0Evy9IFfZUNFlQWVk4OUpHTEZFTkFJSDM5QTNJVVBSOC4u).
#### attend the presentation of the paper (by the concomitant group) to subsequently provide feedback on that presentation using the [Engagement (Post) form](https://forms.office.com/Pages/ResponsePage.aspx?id=sAafLmkWiUWHiRCgaTTcYW0VF5r2yGtKrh0Evy9IFfZURjM0VlFPSjNVWThVSTZQQzRPSjFBMVE2Mi4u).
## outline
### 1 Motivation
:PROPERTIES:
:id: 60424562-b12a-4885-8cc4-af68644402c6
:END:
### 2 Independent Component Analysis
:PROPERTIES:
:id: 604243f6-e77d-4f41-8a56-b08d7d19688d
:END:
#### 2.1 Definition of ICA
#### 2.2 Ambiguties of ICA
#### 2.3 Illustration of ICA
### 3 What is independence?
:PROPERTIES:
:id: 60424416-cf37-42be-affc-be3604879aae
:END:
#### 3.1 Definition and Fundamental properties
#### 3.2 Uncorrelated variables are only partly independent
#### 3.3 Why Gaussian variables are forbidden
### 4 Principles of ICA estimation
:PROPERTIES:
:id: 60424453-a852-4e6c-9532-efd9111a44ed
:END:
#### 4.1 “Nongaussian is independent”
#### 4.2 Measures of nongaussianity
##### 4.2.1 Kurtosis
##### 4.2.2 Negentropy
##### 4.2.3 Approximations of negentropy
#### 4.3 Minimization of Mutual Information
##### 4.3.1 Mutual Information
##### 4.3.2 Deﬁning ICA by Mutual Information
#### 4.4 Maximum Likelihood Estimation
##### 4.4.1 The likelihood
##### 4.4.2 The Infomax Principle
##### 4.4.3 Connection to mutual information
#### 4.5 ICA and Projection Pursuit
### 5 Preprocessing for ICA
:PROPERTIES:
:id: 6042449e-bd98-4391-a091-c6acdf5fe12f
:END:
#### 5.1 Centering
#### 5.2 Whitening
#### 5.3 Further preprocessing
### 6 The FastICA Algorithm
:PROPERTIES:
:id: 604244b0-168e-439b-b6dc-e00e4d97f8cb
:END:
#### 6.1 FastICA for one unit
#### 6.2 FastICA for several units
#### 6.3 FastICA and maximum likelihood
#### 6.4 Properties of the FastICA Algorithm
### 7 Applications of ICA
:PROPERTIES:
:id: 604244c7-e45c-403b-8301-37e98700d873
:END:
#### 7.1 Separation of Artifacts in MEG Data
#### 7.2 Finding Hidden Factors in Financial Data
#### 7.3 Reducing Noise in Natural Images
#### 7.4 Telecommunications
### 8 Conclusion
## PPT outline
### Background
#### {{embed ((60424562-b12a-4885-8cc4-af68644402c6))}}
#### {{embed ((604243f6-e77d-4f41-8a56-b08d7d19688d)) }}
#### {{embed ((60424416-cf37-42be-affc-be3604879aae)) }}
### Method
#### {{embed ((60424453-a852-4e6c-9532-efd9111a44ed))}}
#### {{embed ((6042449e-bd98-4391-a091-c6acdf5fe12f))}}
### Experiment
#### {{embed ((604244b0-168e-439b-b6dc-e00e4d97f8cb))}}
### Contribution
#### {{embed ((604244c7-e45c-403b-8301-37e98700d873)) }}
## 中文翻译
### [详解独立成分分析](https://j.mp/3bloY8M)
### 第一遍，收集要素
#### 本部分关键在于目标函数。
#### 前情理解
##### 动机，问题举例
###### 前面的部分，首先引出了动机，描述了一个有两个演讲者，两个麦克风的情况下，麦克风记录的信号表示为x1和x2，演讲者的说话信号记为s1和s2。这里已知x1和x2，但是不知道s1和s2。x和s的关系，x是s的加权和，表示为：
#######
$$
\begin{array}{l}
x_{1}(t)=a_{11} s_{1}+a_{12} s_{2} \\
x_{2}(t)=a_{21} s_{1}+a_{22} s_{2}
\end{array}
$$
####### a是各种影响录音的参数。
###### 所以在这个情况下，如果能用x来估计出s，是非常有用的技术。也就是还原了声道。
###### 已知参数a，可以很方便地用传统方法求出s。 但是如果不知道参数，就不能用传统方法了
###### 所以，引出了本文的方法，[[ICA Independent Component Analysis]] 独立成分分析
###### ICA假设了信号s互相之间是统计独立的。正符合上述情况。ICA能够估计出参数a，继而能够从x中分离出 s
##### 定义，模型，参数解释
###### 统计因变量模型 statistical “latent variables”
####### n个独立成分s，n个线性混合信号x
####### 
$$
x_{j}=a_{j 1} s_{1}+a_{j 2} s_{2}+\ldots+a_{j n} s_{n}, \text { for all } j
$$
####### 每个x和s都是随机变量，观测值 $$x_{j}(t)$$ 是样本值。
####### 假设混合变量和独立分量都具有零均值（也可以先中心化）
####### 将上式用矩阵表示 $$\mathbf{x}=\mathbf{A} \mathbf{s}$$
####### 或者用列向量表示 $$\mathbf{x}=\sum_{i=1}^{n} \mathbf{a}_{i} s_{i}$$
####### 上面几个公式就称为独立成分分析或ICA模型
####### ICA模型是生成模型，描述了观测数据是如何通过混合元素s_{i}生成的
####### 独立成分是隐变量，不能被直接观测
####### 混合矩阵$$\mathbf{A}$$，假设是未知的
####### 只能观察到x，用x估计A和s
###### ICA假设
####### 成分$$s_{i}$$是统计独立的。而且还假设独立成分是**非高斯分布**的。
######## 第四章就要重点讲非高斯分布
####### s的分布未知
####### A是方阵，其逆矩阵是W，所以
#######
$$
\mathbf{s}=\mathbf{W} \mathbf{x}
$$
###### ICA的不确定性
####### 不能确定独立成分的方差
######## 所以直接假设方差是1
######## 
$$
E\left\{s_{i}^{2}\right\}=1
$$
####### 不能确定独立成分的顺序
######## 公式中s的顺序可以随意换
###### 图解，略
####### 给了个简单的例子，两个x两个s，观察两个x，确定一个s，得到另一个s
##### 独立性
###### 如果关于y_{1}值的信息没有给出关于y_{2}值的任何信息，则变量y_{1}和y_{2}被认为是独立的
###### 公式
####### 
$$
p\left(y_{1} y_{2}\right)=p_{1}\left(y_{1}\right) p_{2}\left(y_{2}\right)
$$
####### 其中
######## 
$$
p_{1}\left(y_{1}\right)=\int p\left(y_{1}, y_{2}\right) d y_{2}
$$
######## y2同理
###### 推导之后得到
#######
$$
E\left\{h_{1}\left(y_{1}\right) h_{2}\left(y_{2}\right)\right\}=E\left\{h_{1}\left(y_{1}\right)\right\} E\left\{h_{2}\left(y_{2}\right)\right\}
$$
####### 后面用到
###### 独立independent和不相关Uncorrelated
#######
