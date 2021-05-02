---
title: NLU Lecture 20 Paraphrasing
---

## 什么是 paraphrasing
### Sentences or phrases that convey approximately the same meaning using different words (Bhagat and Hovy, 2012).
### 中文翻译：复述
### 有很多应用（略）
## 过去
### 历史
#### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210502195245.png)
### Bilingual Pivoting
#### 双语旋转（？）
#### paraphrase是语言到自己的另一个表达，通常没有这样的数据。借用第三方（另一个语言）来中转
#### $P\left(e_{2} \mid e_{1}\right)=\sum_{F} P\left(e_{2} \mid f\right) P\left(f \mid e_{1}\right)$
#### paraphrases extracted from phrase table of SMT system
#### lexical and syntactic (aka rules)
#### enriched with annotations for specific tasks(e.g, entailment Simplificatlon
### PPDB
#### The Paraphrase Database
#### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210502195759.png)
## 现在
### NMT (Neural Machine Translation) and PARANET
#### 当前研究（表格图）
##### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210502195840.png)
#### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210502200004.png)
#### 复习 Encoder-Decoder with Attention
#### ParaNet
##### 简要模型
###### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210502200156.png)
###### Source is translated into $K$ -best list of foreign pivots $\mathcal{G}_{x}=\left\{g_{1}, \ldots, g_{K}\right\}$.
$$
p\left(x^{\prime} \mid \mathcal{G}_{x}\right)=\prod_{t=1}^{\left|x^{\prime}\right|} p\left(y_{t} \mid y_{<t}, \mathcal{G}_{x}\right)=\prod_{t=1}^{\left|x^{\prime}\right|} \sum_{k=1}^{K} p\left(g_{k} \mid x\right) p\left(y_{t} \mid y_{<t}, g_{k}\right)
$$
##### 多轴
###### **Late-weighted combination** (Firhat et al., 2016)
####### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210502200453.png)
####### Pivot sentences are encoded separately by two encoders 用两个encoder来编码轴句子
####### At each time step, two decoders produce a probability distribution over all words, which are then combined (in the yellow square)
####### From this combined distribution a word is chosen, which is then given as input to each decoder.
##### 多语
###### Pivot over sentences from multiple language pairs
###### Translate $x$ into $K$ -best German $\mathcal{G}^{\mathcal{D} \mathcal{E}}$ and French $\mathcal{G}^{F R}$ sentences
####### $P\left(x^{\prime} \mid \mathcal{G}^{D E}, \mathcal{G}^{F R}\right)=\prod_{t=1}^{\left|x^{\prime}\right|} p\left(y_{t} \mid y_{<t}, \mathcal{G}^{D E}, \mathcal{G}^{F R}\right)$
$p\left(y_{t} \mid y_{<t}, \mathcal{G}^{D E}\right)=\sum_{k=1}^{K} p\left(g_{k}^{\mathcal{D} \mathcal{E}} \mid x\right) p\left(y_{t} \mid y_{<t}, g_{k}^{\mathcal{D} \mathcal{E}}\right)$
$p\left(y_{t} \mid y_{<t}, \mathcal{G}^{F R}\right)=\sum_{k=1}^{K} p\left(g_{k}^{\mathcal{F R}} \mid x\right) p\left(y_{t} \mid y_{<t}, g_{k}^{\mathcal{F R}}\right)$
###### Then average distributions
####### $p\left(y_{t} \mid y_{<t}, \mathcal{G}^{D E}, \mathcal{G}^{F R}\right)=\lambda_{1} \sum_{k=1}^{K} p\left(g_{k}^{\mathcal{D} \mathcal{E}} \mid x\right) p\left(y_{t} \mid y_{<t}, g_{k}^{\mathcal{F R}}\right)+\lambda_{2} \sum_{k=1}^{K} p\left(g_{k}^{\mathcal{F R}} \mid x\right) p\left(y_{t} \mid y_{<t}, g_{k}^{\mathcal{F} \mathcal{R}}\right)$
##### 相关研究
###### 单轴和多轴
####### (Pavlick et al. 2015)
###### How Good are the Paraphrases?
###### How Good are the Embeddings?
###### Generation
###### Text Rewriting
####### Sentence compression
######## produces a summary of a single sentence by using less words, preserving the most important information, and remaining grammatical.
######## 用ParaNet，加上长度限制
### Sentence Compression
### Question Answering
