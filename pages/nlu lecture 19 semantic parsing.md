---
title: NLU Lecture 19 Semantic Parsing
---

- Motivation
	- Example
		- sentence-logical form
			- Question
				- Who are the male actors in Titanic?
			- Logical Form
				- λx. ∃y. gender (MALE, x ) ∧ cast (TITANIC, x, y )
	- Why the Task is Hard
		- 挑战
			- Machine language is different from NL string and its syntactic representation.
				- neural encoder-decoder architecture for mapping natural language expressions to their logical forms.
			- Well-formedness of Machine Language 格式严格
			- Linguistic Coverage，多（NL）对一
		- 解决
			- Structural Mismatches:
				- neural encoder-decoder architecture for mapping natural language expressions to their logical forms.
			- Well-formedness Constraints:
				- coarse-to-ﬁne decoding algorithm generates well-formed meaning representations.
			- Linguistic Coverage:
				- query paraphrasing framework handles variation of natural language input.
		- 其他挑战略
- Modeling
	- Sequence-to-Sequence
		- 解决 Structural Mismatches
		- 模型大概
			- ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210502192725.png)
		- ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210502192827.png)
		- Encoder encodes natural language input q into a vector representation
		- Decoder generates $y_{1}, \cdots, y_{|a|}$ conditioned on the encoding vector.
		- 模型细节
			- ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210502193043.png)
			- $\mathbf{h}_{t}^{\prime}=\operatorname{LSTM}\left(\mathbf{h}_{t-1}^{\prime}, \mathbf{h}_{t}^{\prime-1}\right)$
			  $\mathbf{h}_{t}^{0}=\mathbf{W}_{q} \mathbf{e}\left(x_{t}\right)$
			  $\mathbf{h}_{t}^{0}=\mathbf{W}_{a} \mathbf{e}\left(y_{t-1}\right)$
			  $p\left(y_{t} \mid y_{<t}, q\right)=\operatorname{softmax}\left(\mathbf{W}_{o} \mathbf{h}_{t}^{L}\right)^{\top} \mathbf{e}\left(y_{t}\right)$
		- 注意力模型
			- Bahdanau et al., (2015), Luong et al., (2015b), Xu et al., (2015)
			- ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210502193128.png)
			- $\begin{aligned} r_{t, k} & \propto \exp \left\{\mathbf{h}_{t}^{L} \cdot \mathbf{h}_{k}^{L}\right\} \\ \mathbf{h}_{t}^{a t t} &=\tanh \left(\mathbf{W}_{1} \mathbf{h}_{t}^{L}+\mathbf{W}_{2} \mathbf{c}_{t}\right) \\ p\left(y_{t} \mid y_{<t}, q\right) &=\operatorname{softmax}_{a_{t}}\left(\mathbf{W}_{o} \mathbf{h}_{t}^{a t t}\right) \end{aligned}$
		- 训练 training
			- maximizes likelihood of logical forms given natural language input:
				- $\max \sum_{(q, a) \in \mathcal{D}} \log p(a \mid q)$
		- 测试 test
			- predict the logical form for an input utterance q by:
				- $\hat{a}=\underset{a^{\prime}}{\arg \max } p\left(a^{\prime} \mid q\right)$
			- Iterating over all possible a ′ s to obtain the optimal prediction is **impractical.**
			- greedy/beam search
	- Coarse-to-Fine
		- 解决 Well-formedness Constraints
		- 例子 Coarse-to-Fine Decoding
			- ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210502193650.png)
		- Meaning Sketches
			- **Disentangle** high-level from low-level semantics; different levels of granularity 粒度.
			- More **compact** 紧凑 meaning representation (length: 21.1 → 9.2 on ATIS).
			- Explicit **sharing** of coarse structure which is the same for examples with same basic meaning. 同结构分享
			- Provide **global** context to ﬁne meaning decoding. 全局背景
		- Coarse-to-Fine Model
			-
			  $$
			  p(y \mid x)=p(y \mid x, a) p(a \mid x)
			  $$
			  where $a=a_{1} \ldots a_{|a|}$ is an abstract sketch representing the meaning of $y$.
			- $p(y \mid x, a)=\prod_{t=1}^{|y|} p\left(y_{t} \mid y_{<t}, x, a\right) \quad p(a \mid x)=\prod_{t=1}^{|a|} p\left(a_{t} \mid a_{<t}, x\right)$
			  where $a_{<t}=a_{1} \cdots a_{t-1}$, and $y_{<t}=y_{1} \cdots y_{t-1} .$
		- Modeling Framework
			- ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210502194231.png)
		- Training and Inference
			- maximizes the log likelihood of the generated meaning representations given natural language expressions:
				-
				  $$
				  \max \sum_{(x, a, y) \in \mathcal{D}} \log p(y \mid x, a)+\log p(a \mid x)
				  $$
				  $\mathcal{D}$ are training pairs, $x$ input, a sketch, and $y$ meaning representation
			- predict a and y via greedy search
				-
				  $$
				  \hat{a}=\underset{a^{\prime}}{\arg \max } p\left(a^{\prime} \mid x\right) \quad \hat{y}=\underset{y^{\prime}}{\arg \max } p\left(y^{\prime} \mid x, \hat{a}\right)
				  $$
				  $a^{\prime}$ and $y^{\prime}$ represent coarse- and fine-grained meaning candidates.
	- 论文
		- Tasks: Natural Language to Logical Form
			- G EO Q UERY and ATIS (Zettlemoyer and Collins, 2005; Kwiatkowski et al., 2011)
		- Tasks: Natural Language to Source Code
			- D JANGO dataset (Oda et al., 2015).
		- Tasks: Natural Language to SQL
			- W IKI SQL dataset (Zhong et al., 2017), 80,654 questions and queries distributed across 24,241 tables from Wikipedia).
	- 评估
		- Exact Match Accuracy
			- proportion of input queries that are correctly parsed to their gold standard logical forms.
		- Denotation Match Accuracy:
			- proportion of correct denotations (answers that the logical forms give when executed against the knowledge base).