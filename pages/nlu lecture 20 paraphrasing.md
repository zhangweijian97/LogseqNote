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
##### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210502200156.png)
#####
### Sentence Compression
### Question Answering
