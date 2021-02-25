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
######
:PROPERTIES:
:id: 60364900-cd28-4b19-87e1-40d3a4549ea9
:END:
$$\boldsymbol{\Sigma}=\frac{1}{n}\boldsymbol{X}\boldsymbol{X}^\top$$
###### eigenvalue decomposition
:PROPERTIES:
:id: 603648e7-1114-436c-8b9e-258da79f3fc9
:END:
#######
$$\operatorname{Cov}[\boldsymbol{x}]  = \boldsymbol{\Sigma} = \boldsymbol{U}\boldsymbol{\Lambda} \boldsymbol{U}^\top$$
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
:PROPERTIES:
:id: 60364b4a-32fb-4ab7-997b-fb38423e1061
:END:
######
$$
\boldsymbol{C}_{n}=\boldsymbol{I}_{n}-\frac{1}{n} \mathbf{1}_{n} \mathbf{1}_{n}^{\top}
$$
######
$$\boldsymbol{X}=\tilde\boldsymbol{X}\boldsymbol{C}_n$$
###### 左列右行
##### sample covarice matrix with certring matrix，1.66
######
$$\boldsymbol{\Sigma}=\frac{1}{n}\boldsymbol{X}\boldsymbol{C}_n\boldsymbol{X}^\top$$
#### 1.3.2 Outlier Detection and Removal
##### Tukey’s fences，1.68
######
$$[Q_1-k\text{IQR(x)}, Q_3+k\text{IQR(x)}]$$
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
##### Principal Component Scores
######
$$z_i = \boldsymbol{w}_i^\top\boldsymbol{x}$$
###### 上面这个是原公式，下面是我自己写的
######
$$z_{ij} = \boldsymbol{w}_i^\top\boldsymbol{x}_j$$
######
$$\boldsymbol{z}_i^\top = \boldsymbol{w}_i^\top\boldsymbol{X}$$
######
:PROPERTIES:
:id: 6036c287-de39-431b-9627-474b3ce79e80
:END:
$$\boldsymbol{z}_j = \boldsymbol{U}_k^\top\boldsymbol{x}_j$$
######
:PROPERTIES:
:id: 6036c30d-feb4-4f88-87c3-c257a5f75363
:END:
$$\boldsymbol{Z} = \boldsymbol{U}_k^\top\boldsymbol{X}$$
####### Z 的维度，k $\times$ n
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
#### 投影的x 公式2.30，$\hat x = Px = \sum_{i=1}^{k} \boldsymbol{w}_{i} \boldsymbol{w}_{i}^{\top}x =\boldsymbol{W}_{k} \boldsymbol{W}_{k}^{\top}x = \sum_{i=1}^k\boldsymbol{w}_{i}z_i$
:PROPERTIES:
:id: 6036bb2f-90a3-4763-8761-b3f704307e42
:END:
#### 优化问题，公式2.29
#### smallest expected approximation error，公式2.36
#####
$$\sum_{i=k+1}^d\lambda_i$$
### 2.3 PCA by Low Rank Matrix Approximation
#### 2.3.1 Approximating the Data Matrix
##### singular value decomposition, 公式2.39
######
$$\boldsymbol{X} = \boldsymbol{U}\boldsymbol{S}\boldsymbol{V}^\top$$
###### U, d $\times$ d; S, d $\times$ n; V, n $\times$ n; X, d $\times$ n
###### X又可以写作
#######
$$\boldsymbol{X}=\sum_{i=1}^r s_i \boldsymbol{u}_i\boldsymbol{v}_i^\top$$
##### optimisation problem，公式2.42
######
$$
\begin{array}{ll}
\underset{M}{\operatorname{minimise}} & \sum_{i j}\left((\boldsymbol{X})_{i j}-(\boldsymbol{M})_{i j}\right)^{2} \\
\text { subject to } & \operatorname{rank}(\boldsymbol{M})=k
\end{array}
$$
###### Frobenius norm
##### 公式2.43
######
$$\hat\boldsymbol{X}=\sum_{i=1}^k s_i \boldsymbol{u}_i\boldsymbol{v}_i^\top$$
##### approximation error，公式2.44
######
$$
\|\boldsymbol{X}-\hat{\boldsymbol{X}}\|_{F}=\sum_{i=k+1}^{r} s_{i}^{2}
$$
##### relate to principal component analysis
###### $\boldsymbol{u}_i$ 是 principal component directions
###### $s_i$ 和 $\lambda_i$ 公式2.45
#######
$$\lambda_i=\cfrac{s_i^2}{n}$$
###### principal component scores (**after scaling?**)，公式2.46
#######
$$\boldsymbol{z}_i^\top=\boldsymbol{u}_i^\top\boldsymbol{X}=s_i\boldsymbol{v}_i^\top$$
###### 公式2.47
#######
$$\hat\boldsymbol{X}=\sum_{i=1}^k \boldsymbol{u}_i\boldsymbol{z}_i^\top$$
###### 证明在公式2.48 到 2.50（这里似乎有一道旧卷题考到？）
#### 2.3.2 Approximating the Sample Covariance Matrix
##### optimisation problem 2.51
######
$$
\begin{array}{cl}
\underset{\boldsymbol{M}}{\operatorname{minimise}} & \|\boldsymbol{\Sigma}-\boldsymbol{M}\|_{F} \\
\text { subject to } & \operatorname{rank}(\boldsymbol{M})=k \\
& \boldsymbol{M}^{\top}=\boldsymbol{M}
\end{array}
$$
#### 2.3.3 Approximating the Gram Matrix
##### Gram matrix 2.52
######
:PROPERTIES:
:id: 6036c587-f200-48ec-9866-3189543f2c77
:END:
$$\boldsymbol{G} = \boldsymbol{X}^\top\boldsymbol{X}$$
####### n $\times$ n matrix
###### 用SVD得到G的EVD, 公式2.53
:PROPERTIES:
:id: 6036c5b3-1d6f-478d-8cc6-90251b30da71
:END:
#######
$$\boldsymbol{G} = \boldsymbol{V} \tilde\boldsymbol{\Lambda}\boldsymbol{V}^\top$$
#######
$$\tilde\boldsymbol{\Lambda}=\boldsymbol{S}^\top\boldsymbol{S}$$
##### best rank k approximation of the Gram matrix 公式2.54
######
$$\hat\boldsymbol{G}=\sum_{i=1}^k \boldsymbol{v}_i s_i^2\boldsymbol{v}_i^\top = \sum_{i=1}^k \boldsymbol{z}_i \boldsymbol{z}_i^\top$$
##### principal component scores, 公式2.57
:PROPERTIES:
:id: 6036c688-04a1-4c3b-ae7f-6293217ca49e
:END:
######
$$
\boldsymbol{Z}=\sqrt{\tilde{\boldsymbol{\Lambda}}_{k}} \boldsymbol{V}_{k}^{\top}
$$
###### k $\times$ n matrix
### 2.4 Probabilistic PCA
#### 2.4.1 Probabilistic Model
##### 随机变量 $\boldsymbol{z}$ 统计独立，标准正太分布 2.58
######
$$
p(\boldsymbol{z})=\mathcal{N}(\boldsymbol{z} \mid \mathbf{0}, \boldsymbol{I})
$$
##### 正太分布 2.59
######
$$
\mathcal{N}(\boldsymbol{x} \mid \boldsymbol{\mu}, \mathbf{\Sigma})=\frac{1}{\sqrt{(2 \pi)^{d}|\operatorname{det}(\mathbf{\Sigma})|}} \exp \left(-\frac{1}{2}(\boldsymbol{x}-\boldsymbol{\mu})^{\top} \boldsymbol{\Sigma}^{-1}(\boldsymbol{x}-\boldsymbol{\mu})\right)
$$
##### 数据 $\boldsymbol{x}$ 2.60
######
$$\boldsymbol{x} = \boldsymbol{W}\boldsymbol{z}+\boldsymbol{\mu}+\boldsymbol{\epsilon}$$
###### W, $d \times k$
###### $\mu$, $d$-dimension
###### $\epsilon$, $d$-dimension zero-mean Gaussian-distributed noise **variable**
#### 2.4.2 Joint, Conditional and Observation Distributions
##### 条件概率分布 公式2.61
######
$$
p(\boldsymbol{x}|\boldsymbol{z})=\mathcal{N}(\boldsymbol{x} \mid \boldsymbol{W}\boldsymbol{z}+\boldsymbol{\mu}, \sigma^2\boldsymbol{I})
$$
##### 联合概率分布 公式2.62
######
$$
p(\boldsymbol{z}, \boldsymbol{x})=\frac{1}{\text { const }} \exp \left(-\frac{1}{2}\left[(\boldsymbol{x}-\boldsymbol{W} \boldsymbol{z}-\boldsymbol{\mu})^{\top}\left(\frac{1}{\sigma^{2}} \boldsymbol{I}\right)(\boldsymbol{x}-\boldsymbol{W} \boldsymbol{z}-\boldsymbol{\mu})+\boldsymbol{z}^{\top} \boldsymbol{z}\right]\right)
$$
###### 协方差矩阵 covariance 公式2.68
#######
$$
\operatorname{Cov}\left[\left(\begin{array}{l}
\boldsymbol{z} \\
\boldsymbol{x}
\end{array}\right)\right]=\left(\begin{array}{cc}
\boldsymbol{I}+\boldsymbol{W}^{\top} \frac{1}{\sigma^{2}} \boldsymbol{W} & -\boldsymbol{W}^{\top} \frac{1}{\sigma^{2}} \\
-\frac{1}{\sigma^{2}} \boldsymbol{W} & \frac{1}{\sigma^{2}} \boldsymbol{I}
\end{array}\right)^{-1}=\left(\begin{array}{cc}
\boldsymbol{I} & \boldsymbol{W}^{\top} \\
\boldsymbol{W} & \boldsymbol{W} \boldsymbol{W}^{\top}+\sigma^{2} \boldsymbol{I}
\end{array}\right)
$$
###### 平均值 mean 公式2.70
#######
$$
\mathbb{E}\left[\left(\begin{array}{l}
\boldsymbol{z} \\
\boldsymbol{x}
\end{array}\right)\right]=\left(\begin{array}{cc}
\boldsymbol{I} & \boldsymbol{W}^{\top} \\
\boldsymbol{W} & \sigma^{2} \boldsymbol{I}+\boldsymbol{W} \boldsymbol{W}^{\top}
\end{array}\right)\left(\begin{array}{c}
-\boldsymbol{W}^{\top} \frac{1}{\sigma^{2}} \boldsymbol{\mu} \\
\frac{1}{\sigma^{2}} \boldsymbol{\mu}
\end{array}\right)=\left(\begin{array}{l}
\mathbf{0} \\
\boldsymbol{\mu}
\end{array}\right)
$$
##### 边缘概率分布 公式 2.71
######
$$
p(\boldsymbol{x})=\mathcal{N}\left(\boldsymbol{x} \mid \boldsymbol{\mu}, \boldsymbol{W} \boldsymbol{W}^{\top}+\sigma^{2} \boldsymbol{I}\right)
$$
#### 2.4.3 Maximum Likelihood
##### log-likelihood 公式 2.73 到 2.75
######
$$
\begin{aligned}
\log p\left(\boldsymbol{X} \mid \boldsymbol{W}, \sigma^{2}\right) &=\sum_{i=1}^{n} \log p\left(\boldsymbol{x}_{i} \mid \boldsymbol{\mu}, \boldsymbol{W}, \sigma^{2}\right) \\
&=\sum_{i=1}^{n} \log \mathcal{N}\left(\boldsymbol{x}_{i} \mid \boldsymbol{\mu}, \mathbf{\Sigma}\right)
\end{aligned}
$$
with $\boldsymbol{\mu}=\mathbf{0}$ and
$$
\boldsymbol{\Sigma}=\boldsymbol{W} \boldsymbol{W}^{\top}+\sigma^{2} \boldsymbol{I}
$$
##### 利用公式2.78 到 2.80，继续推导上式 2.81 到 2.84
######
$$
\begin{aligned}
\log p\left(\boldsymbol{X} \mid \boldsymbol{W}, \sigma^{2}\right) &=\sum_{i=1}^{n} \log \mathcal{N}\left(\boldsymbol{x}_{i} \mid \mathbf{0}, \boldsymbol{\Sigma}\right) \\
& \stackrel{(2.59)}{=} \sum_{i=1}^{n}\left[-\frac{1}{2} d \log (2 \pi)-\frac{1}{2} \log (|\operatorname{det}(\boldsymbol{\Sigma})|)-\frac{1}{2} \boldsymbol{x}_{i}^{\top} \boldsymbol{\Sigma}^{-1} \boldsymbol{x}_{i}\right] \\
&=-\frac{n}{2}[d \log (2 \pi)+\log (|\operatorname{det}(\boldsymbol{\Sigma})|)]-\frac{1}{2} \sum_{i=1}^{n} \boldsymbol{x}_{i}^{\top} \boldsymbol{\Sigma}^{-1} \boldsymbol{x}_{i} \\
& \stackrel{(2.79)}{=}-\frac{n}{2}\left[d \log (2 \pi)+\log (|\operatorname{det}(\boldsymbol{\Sigma})|)+\operatorname{trace}\left(\boldsymbol{\Sigma}^{-1} \hat{\boldsymbol{\Sigma}}\right)\right]
\end{aligned}
$$
######
$$\hat\boldsymbol{\Sigma}=\frac{1}{n}\boldsymbol{X}\boldsymbol{X}^\top$$
##### 最大化上式，解得 公式 2.85 和 公式 2.86
######
$$
\boldsymbol{W}_{\mathrm{ML}}=\boldsymbol{U}_{k}\left(\boldsymbol{\Lambda}_{k}-\sigma^{2} \boldsymbol{I}\right)^{1 / 2} \boldsymbol{R}
$$
####### 对$\hat\boldsymbol{\Sigma}$ 求EVD，得到 $\boldsymbol{U}_{k}$ 和 $\boldsymbol{\Lambda}_{k}$
####### R不唯一，可以取I
######
$$
\sigma_{\mathrm{ML}}^{2}=\frac{1}{d-k} \sum_{i=k+1}^{d} \lambda_{i}
$$
####### represents the average lost variance per residual dimension
#### 2.4.4 Relation to PCA
##### PCA计算 principal component scores
###### {{embed ((6036c287-de39-431b-9627-474b3ce79e80))}}
##### PPCA
###### 公式2.87是 p(z|x) 的协方差
###### 公式2.90是 p(z|x) 的均值
###### 公式2.91是 p(z|x) 的分布，可以用x来计算z
##### 上面的方法需要知道W
##### PCA 计算 x 的 projection
###### {{embed ((6036bb2f-90a3-4763-8761-b3f704307e42))}}
###### 公式2.93到2.99略，证明了PCA can be seen as a special case of probabilistic PCA when the noise variance σ2 is negligibly small
## 3 Dimensionality Reduction
### 3.1 Linear Dimensionality Reduction
#### 3.1.1 From Data Points
##### 已知未中心化的 $\tilde\boldsymbol{X}$
##### 先中心化
###### {{embed ((60364b4a-32fb-4ab7-997b-fb38423e1061))}}
##### 然后计算协方差
###### {{embed ((60364900-cd28-4b19-87e1-40d3a4549ea9))}}
##### 做EVD得到Uk
###### {{embed ((603648e7-1114-436c-8b9e-258da79f3fc9))}}
##### 计算scores
###### {{embed ((6036c30d-feb4-4f88-87c3-c257a5f75363))}}
##### 或者计算G
###### {{embed ((6036c587-f200-48ec-9866-3189543f2c77))}}
##### 做SVD的到A，V
###### {{embed ((6036c5b3-1d6f-478d-8cc6-90251b30da71))}}
##### 计算scores
###### {{embed ((((6036c688-04a1-4c3b-ae7f-6293217ca49e))))}}
#### 3.1.2 From Inner Products
:PROPERTIES:
:id: 6036458f-8df4-428c-b2b3-7ba60689e716
:END:
##### 已知未中心化的 $\tilde\boldsymbol{G}$
##### 先中心化，公式3.10
######
$$\boldsymbol{G} = \boldsymbol{C}_n\tilde\boldsymbol{G}\boldsymbol{C}_n$$
##### 重复前面
#### 3.1.3 From Distances
:PROPERTIES:
:id: 6036458f-c6f3-4d1d-b854-a86ee25e7d47
:END:
##### 已知未中心化的数据，之间的距离 $\delta_{ij}^2$, 或表示为$\boldsymbol{\Delta}$
##### 公式3.12到公式3.21一通推导，得到公式3.22，用$\boldsymbol{\Delta}$ 计算 G
######
$$\boldsymbol{G} = -\cfrac{1}{2} \boldsymbol{C}_n\boldsymbol{\Delta}\boldsymbol{C}_n$$
##### 重复前面
#### 3.1.4 Example
##### 无公式，跳过
### 3.2 Dimensionality Reduction by Kernel PCA
#### 3.2.1 Idea
##### 把x的feature混合得到更高dimension的特征，公式3.23
######
$$
\phi(\boldsymbol{x})=\left(x_{1}, \cdots, x_{d}, x_{1} x_{2}, \cdots, x_{1} x_{d}, \cdots, x_{d} x_{d}\right)^{\top}
$$
##### data matrix 公式3.24
######
$$\Phi = (\phi_1, \cdots, \phi_n)$$
#### 3.2.2 Kernel Trick
##### 公式 3.26
######
$$
(\tilde{\boldsymbol{G}})_{i j}=\boldsymbol{\phi}_{i}^{\top} \boldsymbol{\phi}_{j}=\phi\left(\boldsymbol{x}_{i}\right)^{\top} \phi\left(\boldsymbol{x}_{j}\right)=k\left(\boldsymbol{x}_{i}, \boldsymbol{x}_{j}\right)
$$
###### can be used to compute the (**uncentred**) Gram matrix of $\Phi$
##### 公式3.27是两个k的举例
##### 既然得到未中心化的$\tilde{\boldsymbol{G}}$，可以用 ((6036458f-8df4-428c-b2b3-7ba60689e716)) 的方法来计算Scores
#### 3.2.3 Example
##### 略
### 3.3 Multidimensional Scaling
#### 3.3.1 Metric MDS
##### 已知不相似矩阵
##### 优化问题 公式3.31
######
$$
\operatorname{minimise}_{z_{1}, \ldots, z_{n}} \sum_{i<j} w_{i j}\left(\left\|z_{i}-z_{j}\right\|-\delta_{i j}\right)^{2}
$$
##### solution，Sammon nonlinear mapping
######
$$
w_{i j}=1 / \delta_{i j}
$$
#### 3.3.2 Nonmetric MDS
##### 不相似矩阵未知，但是rank函数已知
##### 优化问题 公式3.33
######
$$
\underset{z_{1}, \ldots, z_{n}, f}{\operatorname{minimise}} \sum_{i<i} w_{i j}\left(\left\|z_{i}-z_{j}\right\|-f\left(\delta_{i j}\right)\right)^{2}
$$
##### 用回归的方法解，课本只给了论文链接 Izenman, 2008
###### Modern Multivariate Statistical Techniques: Regression, Classiﬁcation, and Manifold Learning
#### 3.3.3 Classical MDS
##### 数据的维数未知，数值也未知
##### 已知不相似矩阵，用 ((6036458f-c6f3-4d1d-b854-a86ee25e7d47)) 的方法可以计算Z
##### 优化问题
######
#### 3.3.4 Example
#####
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
