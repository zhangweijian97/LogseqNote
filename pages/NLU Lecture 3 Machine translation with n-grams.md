---
title: NLU Lecture 3 Machine translation with n-grams
---

	- words conditioned on some input
		- speech recognition: condition on speech signal
		- machine translation: condition on text in another language
		- text completion: condition on the first few words of a sentence optical
		- character recognition: condition on an image of text
		- image captioning: condition on an image
		- grammar checking: condition on surrounding words
	- model
		- V, vocabulary
		- P, probability distribution
			-
			  $$
			  P: V^{*} \rightarrow \mathbb{R}_{+}
			  $$
		- $w$ a sequence of words
		- $|w|$, length
		- $w_i$ i-th word
		- joint distribution, conditional distribution
			-
			  $$
			  \begin{aligned}
			  P\left(w_{1} \ldots w_{|w|}\right)=& P\left(w_{1}\right) \times \\
			  & P\left(w_{2} \mid w_{1}\right) \times \\
			  & \ldots \\
			  & P\left(w_{|w|} \mid w_{1}, \ldots, w_{|w|-1}\right) \\
			  & P\left(\langle\mathrm{STOP}\rangle \mid w_{1}, \ldots, w_{|w|}\right) \\
			  &=\prod_{i=1}^{|w|+1} P\left(w_{i} \mid w_{1}, \ldots, w_{|w|}\right)
			  \end{aligned}
			  $$
		- n-gram probabilities, MLE
		- sampling zeros or structural zeros
		- predict
			-
			  $$
			  \hat{w}_{k+1}=\underset{w_{k+1}}{\operatorname{argmax}} P\left(w_{k+1} \mid w_{1} \ldots w_{k}\right)
			  $$
	- Conditional language models
		- 第一种尝试 one long sequence
			-
			  $$
			  P(y x)=P\left(x_{1} \ldots x_{|x|} y_{1} \ldots y_{|y|}\right)
			  $$
			- Problem: the English sentence will usually be longer than n!
		- 第二种 pair
			-
			  $$
			  P(y x)=P\left(x_{1} y_{1} \ldots x_{|x|} y_{|x|} y_{|x|+1} \cdots y_{|y|}\right)
			  $$
			- Problem 1: The sentences are not usually the **same length**!
			- Problem 2: English and Swedish **word orders** are different!
		- 关键点 model bigram **translation probabilities**
			-
			  $$
			  \begin{aligned}
			  P(y, z \mid x)=& P(y \mid x, z) P(z \mid x) \\
			  =& P(|y|,|z| \mid x) \\
			  & \prod_{i=1}^{|y|} P\left(y_{i} \mid y_{1}, \ldots, y_{i-1}, x, z\right) \prod_{i=1}^{|z|} P\left(z_{i} \mid z_{1}, \ldots, z_{i-1}, x\right)
			  \end{aligned}
			  $$
		- full model
			-
			  $$
			  P(|y| \mid x) \prod_{i=1}^{|y|} \underbrace{P\left(z_{i}\mid |x|\right)}_{\text {transition probability}} \underbrace{P\left(y_{i} \mid x_{z_{i}}\right)}_{\text {~~emission probability }}
			  $$
			- problem, z is a latent variable
			- solution by Maximum likelihood
				-
				  $$
				  \begin{aligned}
				  \hat{\theta} &=\arg \max _{\theta} P(\mathcal{D} \mid \theta) \\
				  &=\arg \max _{\theta} \prod_{x_{j}, y_{i} \in V^{2}} \theta_{x_{j} y_{i}}^{\mathbb{E}_{P(\mathcal{D} \mid \theta)}\left[\operatorname{Count}\left(x_{j} y_{i}\right)\right]}
				  \end{aligned}
				  $$
			- 用 EM 算法 (Expectation maximization) 求 $\theta$
		- Greedy search，每步求最优
		- Beam search，每步保存k个最优
	- Summary
		- n-gram models use a **Markov assumption** to model an infinite sample space with a finite set of parameters.
		- Machine translation is just **conditional language modelling**.
		- To effectively model translation with n-grams, we need additional **latent variables** to model word alignment
		- One way to estimate the parameters of latent variable models is with a generalisation of maximum likelihood estimation, called **expectation maximisation**.