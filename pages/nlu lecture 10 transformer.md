---
title: NLU Lecture 10 Transformer
---

	- 复习
		- {{embed ((603454d6-c59f-4b54-b1c0-ae31e4fa5334))}}
		- {{embed ((603455ce-8391-481e-b4a6-cf0964921958))}}
	- RNN problem
		- the hidden representation is a bottleneck: it has to represent a sentence of any length, but its size is fixed;
		- RNNs and their variants suffer from vanishing gradients;
		- the encoder representation also has a recency bias: mostly represents final words of the input;
		- target words whose corresponding source words are at the beginning therefore more difficult to generate correctly.
	- self-attention
		- input $$\boldsymbol{x}_{1}, \ldots, \boldsymbol{x}_{t}$$
		- output $$\boldsymbol{y}_{1}, \ldots, \boldsymbol{y}_{t}$$
		-
		  $$
		  \mathrm{y}_{i}=\sum_{j} w_{i j} \mathrm{x}_{j}
		  $$
		- $w_{ij}$ is the attention, computed as the dot-product of each input token with every other token
			-
			  $$
			  \begin{array}{r}
			  w_{i j}^{\prime}=x_{i} \cdot x_{j} \\
			  w_{i}=\operatorname{softmax}\left(w_{i}^{\prime}\right)
			  \end{array}
			  $$
			- 注意力权重 $w_{ij}'$
			- 注意力分布 $w_i$
		- Architecture
			- ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210222105758.png){:height 416, :width 554}
			- 和前一个结构相比，x之间的连接没有了
		- 缺点  The input is a position invariant, i.e., we have no way to represent word order (unlike in an RNN).
		- Query
			- compare $x_i$ to every other vector to compute attention weights for its own output $y_i$
		- Key
			- compare $x_i$ to every other vector to compute attention weights for its other output $y_j$
		- Value
			- use $x_i$ in the weighted sum to compute every output vector based on these weights.
		-
		  $$
		  \begin{array}{rl}
		  \mathrm{q}_{i}=W_{q} x_{i} & \mathrm{k}_{i}=W_{k} \mathrm{x}_{i} \quad \mathrm{v}_{i}=W_{v} \mathrm{x}_{i} \\
		  w_{i j}^{\prime} & =\mathrm{q}_{i} \cdot \mathrm{k}_{j} \\
		  \mathrm{w}_{i} & =\operatorname{softmax}\left(\mathrm{w}_{i}^{\prime}\right) \\
		  \mathrm{y}_{i} & =\sum_{j} w_{i j} \mathrm{v}_{j}
		  \end{array}
		  $$
		- ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210222175350.png){:height 294, :width 342}
	- Multi-Head attention
		- 相当于多几个上面的模型输出给加权一下
		-
		  $$W^r_q, W^r_k, W^r_v$$
		- Narrow self-attention: cut the input into chunks of size k/h (h: number of heads), use weight matrices of size k/h x k/h.
		- Wide self-attention: use weight matrices that cover the whole input for each head, i.e., of size k x k.
	- Transformer
		- Architecture of Transformer Block
			- ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210222180317.png)
			- blue connections are residual connections
				- They prevent the gradients from getting to large or small.
			- Layer normalisation makes training faster.
			- The feedforward layer applies a single MLP independently to
			   each input vector.
		- A bigger architecture
			- ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210222180646.png)
			- Attention is position invariant
			- Position Encodings
				-
				  $$
				  f: \mathbb{N} \rightarrow \mathbb{R}^{k}
				  $$
				- Vaswani et al. ( 2017 )
					-
					  $$
					  \begin{aligned}
					  P E_{(p o s, 2 i)} &=\sin \left(\operatorname{pos} / 10000^{2 i / k}\right) \\
					  P E_{(p o s, 2 i+1)} &=\cos \left(p o s / 10000^{2 i / k}\right)
					  \end{aligned}
					  $$
					- 所以在i=2的the和i=7的the会有一些些不一样
	- 剩余部分在Lecture 12讲