---
title: KEPLER
---

## 临时笔记
### Wang et al. 2020
### 阅读原文
#### 介绍
##### Pre-trained language representation models (PLMs) [[预训练语言表征模型]]
###### [[BERT]]
###### [[RoBERTa]]
###### 问题：不能捕捉factual knowledge
###### 从未标注文本学习
##### knowledge graphs (KGs)
###### contain extensive structural facts,
##### 两个合作，KE methods can provide factual knowledge for PLMs, while the informative text data can also beneﬁt KE.
##### entity descriptions
##### KEPLER
###### encoder,
####### encode the texts and entities into a uniﬁed semantic space with the same PLM
##### masked language modeling (MLM)
##### we construct Wikidata5M,
###### containing about 5M entities, 20M triplets, and aligned entity descriptions from Wikipedia.
#### 模型
##### encoder
###### 基于transformer
###### 输入
####### sequence of N token
###### computes L layers of d-dimensional contextualized representations
#######
$$
\mathbf{H}_{i} \in \mathbb{R}^{N \times d}
$$
######
