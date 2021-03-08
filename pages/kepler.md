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
###### Each layer of the encoder Ei
###### encoder很多层
###### 第一个输入是N token，输出是N乘d的表示，H，作为下一层输入
###### 最后得到一个表示
###### Usually, there is a special token <s> added to the beginning of the text, and the output at <s> is regarded sentence representation. denote the representation function as E <s>(·).
###### requires a tokenizer
####### use the same tokenization as RoBERTa: the Byte-Pair Encoding (BPE)
###### we do not modify the Transformer encoder structure to add external entity linkers or knowledgeintegration layers
##### Knowledge Embedding
###### factual knowledge
###### deﬁne KGs
###### triplet
###### instead of using stored embeddings
###### encode entities into vectors by using their **corresponding text.**
###### 三个嵌入方法
####### entity descriptions as embeddings,
########
####### entity and relation descriptions as embeddings, and
####### entity embeddings conditioned on relations.
#######
