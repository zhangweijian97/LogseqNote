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
##### 4.4 Maximum Likelihood Estimation
###### 4.4.1 The likelihood
###### 4.4.2 The Infomax Principle
###### 4.4.3 Connection to mutual information
#### 4.5 ICA and Projection Pursuit
### 5 Preprocessing for ICA
:PROPERTIES:
:id: 6042449e-bd98-4391-a091-c6acdf5fe12f
:END:
#### 5.1 Centering
#### 5.2 Whitening
#### 5.3 Further preprocessing
### 6 The FastICA Algorithm
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
#### {{embed ((604243f6-e77d-4f41-8a56-b08d7d19688d)) }}
#### {{embed ((60424416-cf37-42be-affc-be3604879aae)) }}
### Method
#### {{embed ((6042449e-bd98-4391-a091-c6acdf5fe12f))}}
### Experiment
####
### Contribution
#### {{embed ((604244c7-e45c-403b-8301-37e98700d873)) }}
## 在神经网络研究以及许多其他学科中，一个基本问题是找到多元数据（即随机向量）的合适表示形式。由于计算和概念上的简单性，通常将表示形式视为原始数据的线性变换。换句话说，表示的每个组成部分都是原始变量的线性组合。众所周知的线性变换方法包括主成分分析，因子分析和投影追踪。独立成分分析（ICA）是最近开发的一种方法，其目的是找到非高斯数据的线性表示，以使成分在统计上独立或尽可能独立。这样的表示似乎捕获了许多应用程序中数据的基本结构，包括特征提取和信号分离。在本文中，我们介绍了ICA的基本理论和应用，以及我们在该主题上的最新工作。