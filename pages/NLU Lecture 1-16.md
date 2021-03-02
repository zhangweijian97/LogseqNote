---
title: NLU Lecture 1-16
published: false
permalink: nlu%20natural%20language%20understanding%20generation%20and%20machine%20translation
---

## #UoE
## My Lecture Notes
### [[NLU Lecture 14 Word Embeddings are Biased]]
:PROPERTIES:
:id: 6035493a-910e-432e-bb80-4973bfde4149
:END:
#### Bias in representations
#### IAT Implicit-association test
#### IAT for word embeddings

###### 计算group和stereotype的相似度

##### Sanity check 可行性检查

###### 先试试计算“花和虫”（group），“幸福和不满”（stereotype）

###### 果然花和幸福，虫和不满，强相关

##### 正式实验

###### 欧洲人名和非洲人名，舒服和不满。结果欧洲人名和舒服相关，非洲人名和不满相关

###### 男人和事业相关，女人和家庭相关
###### 其他略
##### word2vec embedding
###### he 和 职业
###### she 和 职业
###### she-he
####### 定义上，queen-king，等
####### 刻板印象，lovely-brilliant，等
##### Job descriptions in 20th century (American) texts
###### 相似的工作 分别和 西班牙裔，亚裔，白人
##### 性别和形容词联系，随时间的变化
###### 1910，1950，1990
##### text和种族联系，随时间变化
#### Bias in NLP systems

##### Case study: **219 automatic sentiment analysis systems**, submitted to a shared task intended to measure **anger, fear, joy, sadness**.

###### 生成数据  (PERSON) made me feel (EMOTIONAL STATE WoRD).

####### 比如 Ebony made me feel angry .

###### 结论包括 Most systems associated European-American names more strongly with joy 等

#### What can you do?

##### gender subspace

##### Debiasing

###### 利用一部分词之间embed的关系（she-he）来去除其他词的bias

###### 好像没啥用

##### traps

###### The Framing Trap

####### Data is constrained by access and opportunity, and not all factors are captured in the data frame.

###### The Portability Trap

####### Algorithmic solutions designed for one social context may be misleading, inaccurate, or otherwise harmful in different contexts.

###### The Formalism Trap

####### Social concepts such as fairness-which can be procedural, contextual, and contestable-cannot be resolved mathematically.

###### The Ripple Effect Trap

####### Adding tech to existing social systems changes the behaviours and embedded values of existing systems.

###### The Solutionism Trap

####### The best solution to a problem may not involve technology.

##### Ask questions of your data

###### Why was the dataset created?

###### Who funded the creation of the dataset?

###### What preprocessing or cleaning was done?

###### If it relates to people, were they told what the dataset would be used for, and did they consent?
###### Will the dataset be updated?

#### Summary 考点

##### Word embeddings are a basic technology used in many NLP technologies; they are freely available and used by many developers large and small.

##### Word embeddings empirically exhibit many cultural stereotypes and biases, with strong statistical effects: technology will reflect and can potentially amplify these biases.

##### Who benefits? Who is harmed?

##### Bias and unfairness is a deep sociotechnical problem. We do not know how to solve it with maths, and it's unlikely that we will.

##### Be critical of your data. Does it fit your purpose?

##### When building systems you need to consider social anc historical context, and involve people who will be affected.
### Lecture 15 The Environmental and Human Cost of NLP
:PROPERTIES:
:id: 60355745-fe08-426b-9e3b-10e2ae2a6e10
:END:
#### Anatomy of an Al system 解剖
##### smart speaker
#### Carbon and the Climate Crisis
##### 排放
##### 碳含量
##### 海洋气温
#### The Carbon Cost of Al
##### kinds of costs
###### 开发成本 Costs to progress
####### Research and development of new NLP models multiplies these costs by thousands, due to experimentation with model architectures, parameters, and different datasets.
###### 访问成本（模型运行在昂贵的硬件上）Costs to access
####### Many models require access to specialized hardware (many GPUs or TPUs) limiting access to the richest (Who benefits from this? How does it affect existing power imbalances?)
###### 环境成本 Costs to the environment
####### Computation requires energy, and not all of this energy is carbon-neutral. Where it is. training NLP may not be the best allocation of that energy
##### Estimating the carbon cost of a model
###### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210223195330.png)
#### 总结
##### 训练时间和超参数选择增加了碳排放，而这在SOTA中很常见
##### 对计算资源的掌控导致强者愈强
##### 效率高的算法降低了碳排放，但是 rebound eﬀect 导致更高消耗
###### 便宜的东西，用的人更多
##### 使用已有的模型（预训练）更环保
##### deep adaptation
###### resilience 复原
###### relinquishment 放弃
###### restoration 恢复
### Lecture 16 Neural Parsing
:PROPERTIES:
:id: 60355745-cbce-4ca6-b644-c7a9a672b14d
:END:
#### 复习
##### ((603454d6-c59f-4b54-b1c0-ae31e4fa5334))
##### 输入输出都是符号序列
#### Reading: Vinyals et al. ( 2015 )
##### 后面的三个部分都来自这篇论文。最后一个部分不是
#### Neural Parsing
##### Parsing is the task of turning a sequence of words into a syntax tree:
###### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210223200644.png){:height 218, :width 261}
##### 这里的输出是树
##### 可以 **linearize**
###### (S (NP (Pro You)) (VP (V saw ) (NP (Det a) (N man ) (PP (P with) (Det a) (N telescope))))).
##### 删掉单词，化简
###### (S (NP Pro) (VP V (NP Det N (PP P Det N))))
##### 标记右括号
###### $(S ~(NP ~Pro)_{NP} (VP~ V (NP~ Det~ N (PP ~P~ Det~ N)_{PP} )_{NP} )_{VP} )_{S}$
##### An Encoder-Decoder for Parsing
###### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210223201250.png){:height 276, :width 375}
##### 增加性能的方法
###### EOS (end of sequence)
###### 反转输入
###### 更深的网络
###### 加注意力
###### 用预训练词嵌入模型
###### Vinyals et al. (2015)
####### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210223201534.png)
#### Potential Problems
##### 括号并不能完全配对上
###### 手动加括号
##### 如何配对词和预测的树？
###### 用PoS配对
##### 输出的长度更长
###### 并不是问题
##### 如何确定是best overall sequence 而不是 best symbol at each time step
###### Beam search
#### Results
##### 训练集
###### Wall Street Journal (WSJ): treebank with 40k manually
 annotated sentences.
###### BerkeleyParser corpus: 90k sentences from WSJ and several other treebanks, and 11M sentences parsed with Berkeley Parser.
###### High-confidence corpus: 90k sentences from WSJ from several treebanks, and 11M sentences for which two parsers produce the same tree (length resampled).
##### 在当时实现SOTA
##### 结论
###### The **encoder-decoder model** only works if **attention** is used.
###### Ensembling models helps. Which is almost always the case
###### If we have **a lot of training data**, we get a large boost. And even the simple model without attention starts to work.
###### A simple encoder-decoder model can match the performance of the Berkeley parser (a probabilistic chart parser; O(n3) complexity)
###### Even though we use an LSTM, performance by sentence length is same or better than the Berkeley parser.
##### 分析注意力
###### Attention matrix shows that the model focuses on one word as it produces the parse tree.
###### It moves through the input sequence monotonically (left to right)
###### Model learns stack-like behavior when producing the output.
###### Note that if model focuses on position i, that state has information for all words after i (input is reversed).
###### in some cases, the model skips words
#### Parsing with Transformers
##### Kitaev and Klein (2018):
###### 特点
####### tranformer
####### context aware summary vector
####### word，pos tag，position
####### span scores
####### attention blocks，attention head
####### factored attention head
###### decoder
#######
$$
s(T)=\sum_{(i, j, l) \in T} s(i, j, l)
$$
###### CYK
###### architecture
###### transformer block
###### Factored Attention Head
###### 结果，略
#### Summary
##### linearized parse tree
##### LSTM encoder-decoder
###### given enough training data
##### generate well-formed trees
##### improve by transformer
##### decoder and CYK