---
title: AttnGAN Xu 2018
---

## [[AttnGAN Xu 2018]]
### 介绍
#### 其他GAN的问题：conditioning GAN only on the global sentence vector lacks important ﬁne-grained information at the word level, and prevents the generation of high quality images.
#### AttnGAN的好处 allows attentiondriven, multi-stage reﬁnement for ﬁne-grained text-toimage generation.
#### 两个结构
##### attentional generative network
###### 子区域，单词
###### 全局句子向量
###### 单词向量
###### 用全局句子向量生成低精度图片
###### 图片向量，分区域，去query单词向量，生成单词背景向量
###### 结合区域图片向量和对应的单词背景向量，形成多模型背景向量
###### 生成高精度图片
##### Deep Attentional Multimodal Similarity Model (DAMSM).
###### 计算生成图片和句子的相似度
###### 作为training loss
### 相关工作
#### 深度生成模型
##### [[Conditional GANs Mirza 2014]]
###### Conditional generative adversarial nets
###### 
#+BEGIN_QUOTE
@article{DBLP:journals/corr/MirzaO14,
  author    = {Mehdi Mirza and
               Simon Osindero},
  title     = {Conditional Generative Adversarial Nets},
  journal   = {CoRR},
  volume    = {abs/1411.1784},
  year      = {2014},
  url       = {http://arxiv.org/abs/1411.1784},
  archivePrefix = {arXiv},
  eprint    = {1411.1784},
  timestamp = {Mon, 13 Aug 2018 16:48:15 +0200},
  biburl    = {https://dblp.org/rec/journals/corr/MirzaO14.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}
#+END_QUOTE
###### [[Mehdi Mirza]]
#### 对抗生成网络
#### 注意力机制
#### 结合注意力和GAN
#### AttnGAN，第一个
##### develops an **attention mechanism** that enables **GANs** to generate **ﬁne-grained high-quality images** via **multi-level** (e.g., word level and sentence level) conditioning.
### 模型
#### 架构图
##### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210313170832.png)
#### 注意力生成网络
##### 架构图
###### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210313171032.png)
##### generator，G0到Gm-1
###### m个
###### input是 hidden states ，h0到hm-1
###### 生成small-to-large的图片，$$\hat{x}_{0}, \hat{x}_{1}, \ldots, \hat{x}_{m-1}$$
###### 准确的说是这一部分
####### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210313171254.png){:height 137, :width 47}
###### 公式
#######
$$
\begin{array}{l}
h_{0}=F_{0}\left(z, F^{c a}(\bar{e})\right) \\
h_{i}=F_{i}\left(h_{i-1}, F_{i}^{a t t n}\left(e, h_{i-1}\right)\right) \text { for } i=1,2, \ldots, m-1 ; \\
\hat{x}_{i}=G_{i}\left(h_{i}\right)
\end{array}
$$
####### z是noise vector，从正态分布采样
####### .$$\bar e$$, 全局句向量
####### e，词向量矩阵
####### .$$F^{c a}$$, Conditioning Augmentation
####### .$$F_{i}^{\text {attn }}$$, attention model
###### 注意力模型 $$F^{a t t n}(e, h)$$
####### 两个input
######## word feature，e
######### e‘=Ue
######## image feature，即h
####### word context vector
########
$$
c_{j}=\sum_{i=0}^{T-1} \beta_{j, i} e_{i}^{\prime}, \quad \text { where } \beta_{j, i}=\frac{\exp \left(s_{j, i}^{\prime}\right)}{\sum_{k=0}^{T-1} \exp \left(s_{j, k}^{\prime}\right)}
$$
########
$$
s_{j, i}^{\prime}=h_{j}^{T} e_{i}^{\prime}
$$
####### word context matrix
######## 
$$
F^{a t t n}(e, h)=\left(c_{0}, c_{1}, \ldots, c_{N-1}\right)
$$
###### 目标函数
#######
$$
\mathcal{L}=\mathcal{L}_{G}+\lambda \mathcal{L}_{D A M S M}, \quad \text { where } \mathcal{L}_{G}=\sum_{i=0}^{m-1} \mathcal{L}_{G_{i}}
$$
###### adversarial loss
####### 生成器Gi，判别器Di
####### 
$$
\mathcal{L}_{G_{i}}=\underbrace{-\frac{1}{2} \mathbb{E}_{\hat{x}_{i} \sim p_{G_{i}}}\left[\log \left(D_{i}\left(\hat{x}_{i}\right)\right]\right.}_{\text {unconditional loss }} \underbrace{-\frac{1}{2} \mathbb{E}_{\hat{x}_{i} \sim p_{G_{i}}}\left[\log \left(D_{i}\left(\hat{x}_{i}, \bar{e}\right)\right]\right.}_{\text {conditional loss }},
$$
####### where the unconditional loss determines whether the image is real or fake while the conditional loss determines whether the image and the sentence match or not.
####### cross-entropy loss，最小化
######## 
$$
\begin{aligned}
\mathcal{L}_{D_{i}}=& \underbrace{-\frac{1}{2} \mathbb{E}_{x_{i} \sim p_{\text {data }_{i}}}\left[\log D_{i}\left(x_{i}\right)\right]-\frac{1}{2} \mathbb{E}_{\hat{x}_{i} \sim p_{G_{i}}\left[\log \left(1-D_{i}\left(\hat{x}_{i}\right)\right]\right.}}_{\text {unconditional loss }}+\\
& \underbrace{-\frac{1}{2} \mathbb{E}_{x_{i} \sim p_{\text {data }_{i}}}\left[\log D_{i}\left(x_{i}, \bar{e}\right)\right]-\frac{1}{2} \mathbb{E}_{\hat{x}_{i} \sim p_{G_{i}}\left[\log \left(1-D_{i}\left(\hat{x}_{i}, \bar{e}\right)\right]\right.}}_{\text {conditional loss }}
\end{aligned}
$$
####### DAMSM，word level ﬁne-grained image-text matching loss，见下一节
#### 深度注意力多模态相似度模型DAMSM
##### text encoder
###### 双向LSTM
###### word features
###### sentence feature
##### image encoder
###### CNN
###### 输入图片，resize
###### local feature，f，768乘289
####### 有289个sub regions
###### global feature vector $$\bar f$$
###### convert to common semantic space
####### 
$$
v=W f, \quad \bar{v}=\bar{W} \bar{f}
$$
##### attention-driven image text matching score
###### 测量 图片-句子对 的相似度
###### 首先是 词-图片区域 的相似度矩阵
#######
$$
s=e^{T} v
$$
####### 归一
#######
$$
\bar{s}_{i, j}=\frac{\exp \left(s_{i, j}\right)}{\sum_{k=0}^{T-1} \exp \left(s_{k, j}\right)}
$$
###### 区域背景向量
#######
$$
c_{i}=\sum_{j=0}^{288} \alpha_{j} v_{j}, \quad \text { where } \alpha_{j}=\frac{\exp \left(\gamma_{1} \bar{s}_{i, j}\right)}{\sum_{k=0}^{288} \exp \left(\gamma_{1} \bar{s}_{i, k}\right)}
$$
###### 词-区域 相关度 Relevance
#######
$$
R\left(c_{i}, e_{i}\right)=\left(c_{i}^{T} e_{i}\right) /\left(\left\|c_{i}\right\|\left\|e_{i}\right\|\right)
$$
###### 句子-图片 配对分数
####### 
$$
R(Q, D)=\log \left(\sum_{i=1}^{T-1} \exp \left(\gamma_{2} R\left(c_{i}, e_{i}\right)\right)\right)^{\frac{1}{\gamma_{2}}}
$$
##### DAMSM loss
###### 图-句子对$$\left\{\left(Q_{i}, D_{i}\right)\right\}_{i=1}^{M}$$
###### 句子Di配对图Qi的后验概率
####### 
$$
P\left(D_{i} \mid Q_{i}\right)=\frac{\exp \left(\gamma_{3} R\left(Q_{i}, D_{i}\right)\right)}{\sum_{j=1}^{M} \exp \left(\gamma_{3} R\left(Q_{i}, D_{j}\right)\right)}
$$
###### negative log posterior probability
####### 
$$
\mathcal{L}_{1}^{w}=-\sum_{i=1}^{M} \log P\left(D_{i} \mid Q_{i}\right)
$$
###### 对称
####### 
$$
\mathcal{L}_{2}^{w}=-\sum_{i=1}^{M} \log P\left(Q_{i} \mid D_{i}\right)
$$
###### 代入$$R(Q, D)$$，得到$$\mathcal{L}_{1}^{s}$$  和$$\mathcal{L}_{2}^{s}$$
###### 得到DAMSM loss
####### 
$$
\mathcal{L}_{D A M S M}=\mathcal{L}_{1}^{w}+\mathcal{L}_{2}^{w}+\mathcal{L}_{1}^{s}+\mathcal{L}_{2}^{s}
$$
### 实验
#### 评估
##### 方法
###### 定量
####### IS
######## 跟随Zhang
####### R-precision
###### 定性
####### 可视化中间结果
##### 和其他模型比较
###### IS