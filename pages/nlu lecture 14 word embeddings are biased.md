---
title: NLU Lecture 14 Word Embeddings are Biased
---

### Bias in representations
### IAT Implicit-association test
### IAT for word embeddings

##### 计算group和stereotype的相似度

#### Sanity check 可行性检查

##### 先试试计算“花和虫”（group），“幸福和不满”（stereotype）

##### 果然花和幸福，虫和不满，强相关

#### 正式实验

##### 欧洲人名和非洲人名，舒服和不满。结果欧洲人名和舒服相关，非洲人名和不满相关

##### 男人和事业相关，女人和家庭相关
##### 其他略
#### word2vec embedding
##### he 和 职业
##### she 和 职业
##### she-he
###### 定义上，queen-king，等
###### 刻板印象，lovely-brilliant，等
#### Job descriptions in 20th century (American) texts
##### 相似的工作 分别和 西班牙裔，亚裔，白人
#### 性别和形容词联系，随时间的变化
##### 1910，1950，1990
#### text和种族联系，随时间变化
### Bias in NLP systems

#### Case study: **219 automatic sentiment analysis systems**, submitted to a shared task intended to measure **anger, fear, joy, sadness**.

##### 生成数据  (PERSON) made me feel (EMOTIONAL STATE WoRD).

###### 比如 Ebony made me feel angry .

##### 结论包括 Most systems associated European-American names more strongly with joy 等

### What can you do?

#### gender subspace

#### Debiasing

##### 利用一部分词之间embed的关系（she-he）来去除其他词的bias

##### 好像没啥用

#### traps

##### The Framing Trap

###### Data is constrained by access and opportunity, and not all factors are captured in the data frame.

##### The Portability Trap

###### Algorithmic solutions designed for one social context may be misleading, inaccurate, or otherwise harmful in different contexts.

##### The Formalism Trap

###### Social concepts such as fairness-which can be procedural, contextual, and contestable-cannot be resolved mathematically.

##### The Ripple Effect Trap

###### Adding tech to existing social systems changes the behaviours and embedded values of existing systems.

##### The Solutionism Trap

###### The best solution to a problem may not involve technology.

#### Ask questions of your data

##### Why was the dataset created?

##### Who funded the creation of the dataset?

##### What preprocessing or cleaning was done?

##### If it relates to people, were they told what the dataset would be used for, and did they consent?
##### Will the dataset be updated?

### Summary 考点

#### Word embeddings are a basic technology used in many NLP technologies; they are freely available and used by many developers large and small.

#### Word embeddings empirically exhibit many cultural stereotypes and biases, with strong statistical effects: technology will reflect and can potentially amplify these biases.

#### Who benefits? Who is harmed?

#### Bias and unfairness is a deep sociotechnical problem. We do not know how to solve it with maths, and it's unlikely that we will.

#### Be critical of your data. Does it fit your purpose?

#### When building systems you need to consider social anc historical context, and involve people who will be affected.