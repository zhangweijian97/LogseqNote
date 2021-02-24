---
title: DME Data Mining and Exploration
---

## 1 First Steps in Exploratory Data Analysis
### 1.1 Numerical Data Description
#### 1.1.1 Location
##### mean，公式略
###### 积分版
###### 向量版
##### median，公式略
##### 公式1.7是上面两个的混合
##### mode
#### 1.1.2 Scale
##### 方差，公式略
###### 积分版
##### MAD，公式1.10
##### IQR，Q3-Q1
#### 1.1.3 Shape
##### skewness，1.13
##### Galton’s measure of skewness，1.14
##### kurtosis，1.15
##### robust kurtosis，1.16
#### 1.1.4 Multivariate Measures
##### 协方差，1.17和1.18
##### Pearson’s correlation coefficient，1.19
##### 标准差
##### sample covariance matrix，1.28
###### $\Sigma=\frac{1}{n}XX^T$
###### eigenvalue decomposition
####### $\Sigma = U\Lambda U^T$
###### trace, 1.43
###### 性质，做线性变化之后
#######
$$
\begin{aligned}
\operatorname{Cov}[\boldsymbol{A} \boldsymbol{x}+\boldsymbol{b}] &=\boldsymbol{A} \operatorname{Cov}[\boldsymbol{x}] \boldsymbol{A}^{\top}
\end{aligned}
$$
##### sample correlation matrix，1.41
######
$$
\rho(\boldsymbol{x})=\operatorname{diag}\left(\frac{1}{\operatorname{std}(\boldsymbol{x})}\right) \operatorname{cov}(\boldsymbol{x}) \operatorname{diag}\left(\frac{1}{\operatorname{std}(\boldsymbol{x})}\right)
$$
##### non linear relationship，1.42
##### Kendall’s $\tau$，1.43
######
$$
\tau(x, y)=\frac{n_{c}(x, y)-n_{d}(x, y)}{n(n-1) / 2}
$$
### 1.2 Data Visualisation
#### 这节看lab，研究一下参数变化
#### 1.2.1 Bar Plot
#### 1.2.2 Box Plot
#### 1.2.3 Scatter Plot
#### 1.2.4 Histogram
#### 1.2.5 Kernel Density Plot
##### kernel density estimate，1.47
#### 1.2.6 Violin Plot
### 1.3 Data Pre-Processing
#### 1.3.1 Standardisation
##### 注意这一节中$x$表示没有中心化的，$\tilde x$表示中心化的，和PCA那边的不一样
##### certring matrix
######
$$
\boldsymbol{C}_{n}=\boldsymbol{I}_{n}-\frac{1}{n} \mathbf{1}_{n} \mathbf{1}_{n}^{\top}
$$
###### 左列右行
##### sample covarice matrix with certring matrix，1.66
###### $\Sigma=\frac{1}{n}XC_nX^T$
#### 1.3.2 Outlier Detection and Removal
##### Tukey’s fences，1.68
###### $Q_1-k\text{IQR(x)}), Q_3+k\text{IQR(x)}]$
###### common $k=1.5$
## 2 Principal Component Analysis
### 2.1 PCA by Variance Maximisation
#### 2.1.1 First Principal Component Direction
##### optimisation problem, 2.2
######
$$\begin{array}{cl}
\underset{w_{1}}{\operatorname{maximise}} & w_{1}^{\top} \mathbf{\Sigma} w_{1} \\
\text { subject to } & \left\|w_{1}\right\|=1
\end{array}$$
###### 解法在2.3到2.7
#### 2.1.2 Subsequent Principal Component Directions，
##### 证明主成分是不相关的 The principal components are uncorrelated 2.16到2.22
##### m-th principal component direction 2.23
######
$$\begin{array}{ll}
\underset{\boldsymbol{w}_{m}}{\operatorname{maximise}} & \boldsymbol{w}_{m}^{\top} \boldsymbol{\Sigma} \boldsymbol{w}_{m} \\
\text { subject to } & \left\|\boldsymbol{w}_{m}\right\|=1 \\
& \boldsymbol{w}_{m}^{\top} \boldsymbol{w}_{i}=0 \quad i=1, \ldots, m-1
\end{array}$$
###### variance explained，2.24
#######
$$\sum_{m=1}^k\lambda_m$$
###### fraction of variance explained,2.26
#######
$$\cfrac{\sum_{m=1}^k\lambda_m}{\sum_{m=1}^d\lambda_m}$$
#### 2.1.3 Simultaneous Variance Maximisation
##### 公式 2.27
### 2.2 PCA by Minimisation of Approximation Error
#### 下面的W也是U
#### Projection Matrix，公式2.28
#####
$$
\boldsymbol{P}=\sum_{i=1}^{k} \boldsymbol{w}_{i} \boldsymbol{w}_{i}^{\top}=\boldsymbol{W}_{k} \boldsymbol{W}_{k}^{\top}, \quad \boldsymbol{W}_{k}=\left(\boldsymbol{w}_{1}, \ldots, \boldsymbol{w}_{k}\right)
$$
#### 投影的x，$\hat x = Px = \sum_{i=1}^{k} \boldsymbol{w}_{i} \boldsymbol{w}_{i}^{\top}x =\boldsymbol{W}_{k} \boldsymbol{W}_{k}^{\top}x = \sum_{i=1}^k\boldsymbol{w}_{i}z_i$
#### 优化问题，公式2.29
#### smallest expected approximation error，公式2.36
#####
$$\sum_{i=k+1}^d\lambda_i$$
### 2.3 PCA by Low Rank Matrix Approximation
#### 2.3.1 Approximating the Data Matrix
#### 2.3.2 Approximating the Sample Covariance Matrix
#### 2.3.3 Approximating the Gram Matrix
### 2.4 Probabilistic PCA..
#### 2.4.1 Probabilistic Model ...
#### 2.4.2 Joint, Conditional and Observation Distributions
#### 2.4.3 Maximum Likelihood
#### 2.4.4 Relation to PCA
## 3 Dimensionality Reduction
### 3.1 Linear Dimensionality Reduction
#### 3.1.1 From Data Points
#### 3.1.2 From Inner Products
#### 3.1.3 From Distances
#### 3.1.4 Example
### 3.2 Dimensionality Reduction by Kernel PCA
#### 3.2.1 Idea ..
#### 3.2.2 Kernel Trick
#### 3.2.3 Example. .
### 3.3 Multidimensional Scaling
#### 3.3.1 Metric MDS
##### 优化问题
######
$$
\operatorname{minimise}_{z_{1}, \ldots, z_{n}} \sum_{i<j} w_{i j}\left(\left\|z_{i}-z_{j}\right\|-\delta_{i j}\right)^{2}
$$
##### solution
######
$$
w_{i j}=1 / \delta_{i j}
$$
#####
#### 3.3.2 Nonmetric MDS
#### 3.3.3 Classical MDS
#### 3.3.4 Example
### 3.4 Isomap
### 3.5 UMAP
## 4 Predictive Modelling and Generalisation
### 4.1 Prediction and Training Loss
#### 4.1.1 Prediction Loss
#### 4.1.2 Training Loss
#### 4.1.3 Example
### 4.2 Generalisation Performance
#### 4.2.1 Generalisation for Prediction Functions and Algorithms
#### 4.2.2 Overfitting and Underfitting
#### 4.2.3 Example
### 4.3 Estimating the Generalisation Performance
#### 4.3.1 Methods for Estimating the Generalisation Performance
#### 4.3.2 Hyperparameter Selection and Performance Evaluation
### 4.4 Loss Functions in Predictive Modelling
#### 4.4.1 Loss Functions in Regression
#### 4.4.2 Loss Functions in Classification
## [[DME past paper]]
##
## Reference
### DME lecture notes
