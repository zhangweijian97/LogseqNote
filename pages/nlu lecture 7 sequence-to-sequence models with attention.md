---
title: NLU Lecture 7 Sequence-to-sequence models with attention
---

	- Encoding and decoding sequences
		- use RNN
		- problem
			- Word order is different
			- Different number of words
		- two RNNs as encoder and decoder
			- Encoder-Decoder Architecture
			  id:: 603454d6-c59f-4b54-b1c0-ae31e4fa5334
				- ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210223010554.png){:height 262, :width 352}
			- Encoder:
				-
				  $$
				  \mathbf{h}_{i}=\operatorname{RNN}_{\text {enc }}\left(\mathbf{x}_{i}, \mathbf{h}_{i-1}\right)
				  $$
			- Decoder:
				-
				  $$
				  \begin{aligned}
				  \mathbf{s}_{i} &=\operatorname{RNN}_{\mathrm{dec}}\left(\mathbf{y}_{i}, \mathbf{s}_{i-1}\right) \\
				  P\left(y_{i} \mid y_{1}, \ldots, y_{i-1}, x_{1}, \ldots, x_{|x|}\right) &=\operatorname{softmax}\left(\mathbf{W} \operatorname{concat}\left(\mathbf{s}_{i}, \mathbf{h}_{|x|}\right)+\mathbf{b}\right)
				  \end{aligned}
				  $$
			- context, $\mathbf{h}_{|x|}$
			- problem
				- fixed size
				- recency bias
	- Attention
	  id:: 603455ce-8391-481e-b4a6-cf0964921958
		- Encoder-Decoder with Attention
		  id:: 603455d7-87c7-41fd-bf79-d67a62f06cb0
			- ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210222103358.png){:height 328, :width 360}
		- 计算公式
			-
			  $$
			  \begin{aligned}
			  P\left(y_{i} \mid y_{1}, \ldots, y_{i-1}, x_{1}, \ldots, x_{|x|}\right) &=\operatorname{softmax}\left(W \operatorname{concat}\left(s_{i}, c_{i}\right)+b\right) \\
			  c_{i} &=\sum_{j=1}^{|x|} \alpha_{i j} h_{j}
			  \end{aligned}
			  $$
		- output hidden state, the **query**; input vector, the **keys**
		- dot product attention
			-
			  $$
			  \begin{array}{l}
			  a_{i j}=s_{i} \cdot h_{j} \\
			  \alpha_{i}=\operatorname{softmax}\left(a_{i}\right)
			  \end{array}
			  $$
			- 点乘，两个向量越接近，结果越大，所以可以表示相似的权重
		- 还有其他方法计算相似度
			- bilinear model
				-
				  $$
				  \begin{array}{l}
				  a_{i, j}=\mathbf{s}_{i} \mathbf{V} \mathbf{h}_{j}
				  \end{array}
				  $$
			- FFN
				-
				  $$a_{i, j}=\operatorname{FFN}\left(\mathbf{s}_{i}, \mathbf{h}_{j}\right)$$
	- bidirectional RNN