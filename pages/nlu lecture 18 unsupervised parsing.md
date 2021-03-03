---
title: NLU Lecture 18 Unsupervised Parsing
---

## The Story so Far
### encoder-decoder models [[NLU Lecture 16 Neural Parsing]]
#### RNNs or transformers
#### beam search or CYK
#### {{embed ((603cffc5-abff-49eb-b5ad-4dbddcca69e4))}}
### parser transitions [[NLU Lecture 17 Recurrent Neural Network Grammars]]
#### the actions that are required to build a syntax tree.
#### Recurrent Neural Network Grammars (RNNGs)
#### {{embed ((603eae91-072d-4975-96ab-8ac30333db47))}}
### 以上都需要labeled data
## Unsupervised Parsing
### 现状
#### old problem Gold’s theorem
#### treebanks for a few dozen languages，out of the world’s around 6,000
#### SotA F-score is around 60，for supervised parsing >95
#### unsupervised parsing can be used as the first stage in constructing larger treebanks.
### constituency tests 句子成分测试
#### constituent 句子成分
##### a sequence of words is a constituent if it appears in the context specific for this constituent;
#### long constituents often have short equivalents (pro-forms)
##### NP替换为pronoun，比如戴着帽子的男孩，替换为他
#### **spans** ( sequences of words ) should be **phrases**
### 2002年，Constituent Context Model ( CCM )
### 现在，神经网络版本
### 2020年，combines constituency tests with pre-trained language models
## Unsupervised Parsing via Constituency Tests
### general
#### constituency tests
#### check if the result is grammatical
#### aggregating
#### highest score
### constituency tests
#### Transformation function
#####
$$
c:(\text { sent }, i, j) \mapsto \text { sent }^{\prime}
$$
#### Judgment function
#####
$$
g: \text { sent } \mapsto\{0,1\}
$$
#### Assumption: the span is a constituent if the transformed sentence is grammatical.
#### We need a set of transformations (manually specified) and a grammaticality model (learned).
#### inductive bias.
#### 例子，p11，略
### Parsing Algorithm
#### score each span，用constituency test
#####
$$
g_{\theta}: \text { sent } \mapsto[0,1]
$$
##### averaging the grammaticality judgments over the constituency tests C
#####
$$
s_{\theta}(\text { sent }, i, j)=\frac{1}{|C|} \sum_{c \in C} g_{\theta}(c(\text { sent }, i, j))
$$
#### score each tree
##### summing the scores of its spans and choose the highest scoring binary tree via CYK
#####
$$
t^{*}(\text { sent })=\underset{t \in T(\text { len }(\text { sent }))}{\operatorname{argmax}} \sum_{(i, j) \in t} s_{\theta}(\text { sent }, i, j)
$$
## Grammaticality Model
### 如何得到上面的 $$g_{\theta}$$
### 通常来说，need a corpus of grammatical and ungrammatical sentences as training data。但是这算是监督
### 所以，用real/fake task
#### an unlabeled corpus of sentences and a set of **corruptions**
#### **predict whether a sentence is real or corrupted.**
### not trained from scratch
### by ﬁne-tuning RoBERTa
### set of corruptions
#### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210303004454.png)
###
## Results
##
