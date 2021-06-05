---
title: NLU Lecture 6 Recurrent Neural Networks and LSTMs
---

	- Recurrent networks for language modelling
		- RNN Architecture
		  id:: 60341335-7dab-4af4-8418-3f90ce1af87a
			- ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210222202413.png){:height 249, :width 352}
			-
			  $$
			  \begin{aligned}
			  P\left(x_{i+1} \mid x_{1}, \ldots, x_{i-1}\right) &=\mathbf{y}_{i} \\
			  \mathbf{y}_{i} &=\operatorname{softmax}\left(\mathbf{W h}_{i}+\mathbf{b}_{2}\right) \\
			  \mathbf{h}_{i} &=\sigma\left(\mathbf{V} \mathbf{x}_{i}+\mathbf{U h}_{i-1}+\mathbf{b}_{1}\right) \\
			  \mathbf{x}_{i} &=\text { onehot }\left(x_{i}\right)
			  \end{aligned}
			  $$
		- no Markov assumption
		- Training
			- Use stochastic gradient descent, with cross-entropy.
			- dynanmic
		- Backpropagation
			-
			  $$
			  \Delta w_{k j}=\eta \sum_{p}^{n} \delta_{p k} s_{p j} \quad \delta_{p k}=\left(d_{p k}-y_{p k}\right) g^{\prime}\left(n e t_{p k}\right)
			  $$
			-
			  $$
			  \Delta v_{j i}=\eta \sum_{p}^{n} \delta_{p j} x_{p i} \quad \delta_{p j}=\sum_{k}^{0} \delta_{p k} w_{k j} f^{\prime}\left(n e t_{p j}\right)
			  $$
			-
			  $$
			  \Delta u_{j i}=\eta \sum_{p}^{n} \delta_{p j}(t) s_{p h}(t-1) \quad \delta_{p j}(t)=\sum_{k}^{0} \delta_{p k} w_{k j} f^{\prime}\left(n e t_{p j}\right)
			  $$
			-
			  $$
			  \delta_{p j}(t-1)=\sum_{h}^{m} \delta_{p h}(t) u_{h j} f^{\prime}\left(s_{p j}(t-1)\right)
			  $$
			- time steps $\tau$
			- truncated backpropagation through time
			- 梯度消失
	- LSTM Long short-term memory
		- architecture
			- ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210223005222.png)
			- O: open gate
			- --: closed gate
			- black: high activation
			- white: low activation
		- memory blocks
			- trainable
			- Input gate: controls whether the input to is passed on to the memory cell or ignored;
			- Output gate: controls whether the current activation vector of the memory cell is passed on to the output layer or not;
			- Forget gate: controls whether the activation vector of the memory
			   cell is reset to zero or maintained;
			- Memory cell: stores the current activation vector; with recurrent
			  connection to itself controlled by forget gate.
				- linear
				- no vanishing gradient
			- ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210223005606.png){:height 239, :width 299}
		- relaxes vanishing gradient problem ( somewhat ) using gates.