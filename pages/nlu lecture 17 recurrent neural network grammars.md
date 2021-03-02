---
title: NLU Lecture 17 Recurrent Neural Network Grammars
---

## 小复习
### RNN，LSTM，预测序列，效果不错
#### generate sequence (decode)
#### condition on a sequence (encode)
#### recency bias
#### 这节课大概就是要研究recency bias
### LSTM for parsing
#### linearlize the tree
#### no explicit grammar
#### no encoding of hierarchical structure
#### recency bias
#### can't guarantee tree is well formed
## hierarchy
### generate symbols sequentially
### "control symbols"
## RNN grammars (RNNGs)
### **First** type of operation: introduce a new **NT symbol** (in this case, of type S)
### **Second** type of operation: generate (GEN) a new **terminal symbol** (in this case, “The”)
### **Third** type of operation: **REDUCE** or complete the most recent (non-reduced) nonterminal.
### 图
#### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210302211624.png){:height 189, :width 342}
## pushdown automaton 下推自动机，概率下推自动机
### Compress
#### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210302211941.png)
### 用RNN来预测下一个action
#### 1. Previous terminal symbols
#### 2. Previous actions
#### 3. Current stack contents
:PROPERTIES:
:id: 603eac32-ce6e-4927-8fa5-e10d239d6075
:END:
#### 图
##### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210302212030.png){:height 176, :width 316}
### 图
#### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210302211852.png){:height 251, :width 332}
### Final stack symbol is (a vector representation of) the complete tree.
## Syntactic Composition
###
