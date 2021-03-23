---
title: KEPLER Wang 2019
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
##### [[MLM Masked Language Modeling]]
##### we construct [[Wikidata5M]]
###### containing about 5M entities, 20M triplets, and aligned entity descriptions from Wikipedia.
#### 2 模型
##### 2.1 encoder
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
##### 2.2 Knowledge Embedding
###### factual knowledge
###### deﬁne KGs
###### triplet
###### instead of using stored embeddings
###### encode entities into vectors by using their **corresponding text.**
###### 三个嵌入方法
####### entity descriptions as embeddings,
########
$$
\begin{array}{l}
\mathbf{h}=E_{<s>}\left(\operatorname{text}_{h}\right) \\
\mathbf{t}=E_{<s>}\left(\operatorname{text}_{t}\right) \\
\mathbf{r}=\mathbf{T}_{r}
\end{array}
$$
######## text， descriptions
######## T， relation embeddings
######## use the loss from Sun et al. (2019) as our KE objective,
######## 略
####### entity and relation descriptions as embeddings
######## 
$$
\hat{\mathbf{r}}=E_{<s>}\left(\operatorname{text}_{r}\right)
$$
####### entity embeddings conditioned on relations
########
$$
\mathbf{h}_{r}=\mathrm{E}_{<\mathrm{s}>}\left(\operatorname{text}_{h, r}\right)
$$
#
##### 2.3 Masked Language Modeling
###### 遮住一部分，预测
##### 2.4 Training Objectives
###### 两个loss加起来，很多好处
##### 2.5 Variants
###### 略
###### 实现
####### RoBERTa
####### 参数
#### 3 Wikidata5M
##### 收集
##### 分割
##### 设计benchmark
#### 4 实验
##### 4.1 与之对比的模型
##### 4.2 NLP 任务
###### [[Relation Classiﬁcation]]
####### requires models to classify relation types between two given entities from text.
####### two widely-used **benchmarks**:
######## [[TACRED]] and
######### (Zhang et al., 2017)
######## [[FewRel]].
######### (Han et al., 2018b)
######### two state-of-the-art few-shot frameworks
:PROPERTIES:
:id: 6046582b-2881-4d21-88a7-f6587f1db03d
:END:
########## [[Proto]] (Snell et al., 2017)
########## [[PAIR]] (Gao et al., 2019).
###### [[Entity Typing]]
####### Entity typing requires to classify given entity mentions into pre-deﬁned types.
####### [[OpenEntity]] (Choi et al., 2018)
###### [[GLUE]]
####### General Language Understanding Evaluation
####### (Wang et al., 2019b)
##### 4.3 KE 任务
###### Wikidata5M
###### transductive link prediction setting and the inductive setting.
###### Experimental Settings
####### link prediction
####### compare our models with [[TransE]] (Bordes et al., 2013).
####### 对比 [[DKRL]] (Xie et al., 2016)
###### Transductive Setting
###### Inductive Setting
##### 5 分析
###### 5.1 Ablation Study
####### 消融？
####### 对比
######## 完整模型
######## 只有KE loss
######## 只有MEM loss
###### 5.2 Knowledge Probing Experiment
####### 知识探索实验
###### 5.3 Running Time Comparison
###### 5.4 Correlation with Entity Frequency
###### 5.5 Understanding Text or Storing Knowledge
#### 6 Related Work