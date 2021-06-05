---
title: NLU Lecture 5 n-gram language modelling with feedforward neural networks
---

	- One-hot encoding
	- softmax
	- logistic regression
	- maximize likelihood
	- minimise error, cross-entropy loss
	- Gradient descent
		- gradient descent with momentum
		- individual learning rates for each dimension
		- adaptive learning rates
		- decoupling step length from partial derivates
	- n-grams with a multilayer neural network
	  id:: 6033f4e0-afdc-4f7b-8097-f76d3ee3dd20
		- ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210222181532.png){:height 183, :width 286}
		-
		  $$
		  \begin{aligned}
		  P\left(w_{i} \mid w_{i-3}, w_{i-2}, w_{i-1}\right) &=\operatorname{softmax}\left(\mathrm{Vh}_{2}+\mathrm{b}_{2}\right) \\
		  \mathrm{h}_{2} &=\tanh \left(\mathrm{Wh}_{1}+\mathrm{b}_{1}\right) \\
		  \mathrm{h}_{1} &=\mathrm{Cw}_{i-3} ; \mathrm{Cw}_{i-2} ; \mathrm{Cw}_{i-1} \\
		  \mathrm{w}_{i} &=\text { onehot }\left(w_{i}\right)
		  \end{aligned}
		  $$
		- Each hidden layer is a **representation** of its input.
		- Multiplying one-hot by C selects a row of C (a vector).
		- We call i-th row of C the **embedding** of i-th word in V.
		- Learned **word embeddings** replace hand-engineered features of logistic regression.
	- feedforward neural networks
		- 1. Send an input pattern, x, from the training set.
		- 2. Get the output y.
		- 3. Compare y with the "right answer", or target t, to get the error quantity.
		- 4. Use the error quantity to modify the weights, so next time y will be closer to t.
		- 5. Repeat with another x from the training set.
	- SGD