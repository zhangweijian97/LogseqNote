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
#### 前面的部分，首先引出了动机，描述了一个有两个演讲者，两个麦克风的情况下，麦克风记录的信号表示为x1和x2，演讲者的说话信号记为s1和s2。这里已知x1和x2，但是不知道s1和s2。x和s的关系，x是s的加权和，表示为：
#####
$$
\begin{array}{l}
x_{1}(t)=a_{11} s_{1}+a_{12} s_{2} \\
x_{2}(t)=a_{21} s_{1}+a_{22} s_{2}
\end{array}
$$
####
