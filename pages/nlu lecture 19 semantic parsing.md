---
title: NLU Lecture 19 Semantic Parsing
---

## Motivation
### Example
#### sentence-logical form
##### Question
###### Who are the male actors in Titanic?
##### Logical Form
###### λx. ∃y. gender (MALE, x ) ∧ cast (TITANIC, x, y )
### Why the Task is Hard
#### 挑战
##### Machine language is different from NL string and its syntactic representation.
###### neural encoder-decoder architecture for mapping natural language expressions to their logical forms.
##### Well-formedness of Machine Language 格式严格
##### Linguistic Coverage，多（NL）对一
#### 解决
##### Structural Mismatches:
###### neural encoder-decoder architecture for mapping natural language expressions to their logical forms.
##### Well-formedness Constraints:
###### coarse-to-ﬁne decoding algorithm generates well-formed meaning representations.
##### Linguistic Coverage:
###### query paraphrasing framework handles variation of natural language input.
#### 其他挑战略
## Modeling
### Sequence-to-Sequence
#### 解决 Structural Mismatches
#### 模型大概
##### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210502192725.png)
#### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210502192827.png)
#### Encoder encodes natural language input q into a vector representation
#### Decoder generates $y_{1}, \cdots, y_{|a|}$ conditioned on the encoding vector.
#### 模型细节
##### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210502193043.png)
##### $\mathbf{h}_{t}^{\prime}=\operatorname{LSTM}\left(\mathbf{h}_{t-1}^{\prime}, \mathbf{h}_{t}^{\prime-1}\right)$
$\mathbf{h}_{t}^{0}=\mathbf{W}_{q} \mathbf{e}\left(x_{t}\right)$
$\mathbf{h}_{t}^{0}=\mathbf{W}_{a} \mathbf{e}\left(y_{t-1}\right)$
$p\left(y_{t} \mid y_{<t}, q\right)=\operatorname{softmax}\left(\mathbf{W}_{o} \mathbf{h}_{t}^{L}\right)^{\top} \mathbf{e}\left(y_{t}\right)$
#### 注意力模型
##### Bahdanau et al., (2015), Luong et al., (2015b), Xu et al., (2015)
##### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210502193128.png)
##### $\begin{aligned} r_{t, k} & \propto \exp \left\{\mathbf{h}_{t}^{L} \cdot \mathbf{h}_{k}^{L}\right\} \\ \mathbf{h}_{t}^{a t t} &=\tanh \left(\mathbf{W}_{1} \mathbf{h}_{t}^{L}+\mathbf{W}_{2} \mathbf{c}_{t}\right) \\ p\left(y_{t} \mid y_{<t}, q\right) &=\operatorname{softmax}_{a_{t}}\left(\mathbf{W}_{o} \mathbf{h}_{t}^{a t t}\right) \end{aligned}$
#### 训练 training
##### maximizes likelihood of logical forms given natural language input:
###### $\max \sum_{(q, a) \in \mathcal{D}} \log p(a \mid q)$
#### 测试 test
##### predict the logical form for an input utterance q by:
###### $\hat{a}=\underset{a^{\prime}}{\arg \max } p\left(a^{\prime} \mid q\right)$
##### Iterating over all possible a ′ s to obtain the optimal prediction is **impractical.**
##### greedy/beam search
### Coarse-to-Fine
#### 解决 Well-formedness Constraints
#### 例子 Coarse-to-Fine Decoding
##### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210502193650.png)
#### Meaning Sketches
##### **Disentangle** high-level from low-level semantics; different levels of granularity 粒度.
##### More **compact** 紧凑 meaning representation (length: 21.1 → 9.2 on ATIS).
##### Explicit **sharing** of coarse structure which is the same for examples with same basic meaning. 同结构分享
##### Provide **global** context to ﬁne meaning decoding. 全局背景
#### Coarse-to-Fine Model
#### Modeling Framework
#### Training and Inference
