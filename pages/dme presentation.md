---
title: DME Presentation
---

- [[DME presentation information]]
  id:: 603a5e9b-b946-41ee-9a71-940f862daeac
- DME presentation team information
	- s2119299-weijian zhang
	- s2018229-xi zhao
	- s2093718-yunbo liu
	- s2060292-shifeng xu
- [[DME presentation paper outline]]
- 文章分配 分割
	- Background
		- 123
	- Method
		- 45
	- Experiment
		- 6
	- Contribution
		- 7
- 资源
	- 中文博客 [详解独立成分分析](https://j.mp/3bloY8M)
- [[DME Presentation 第一遍 理解内容 收集要素]]
- [[DME Presentation 第二遍 删繁就简]]
- [[DME Presentation 第三遍 演讲稿 第一版]]
- DME Presentation 第三遍 演讲稿 第二版
	- Now we have the ICA model. Next, we will introduction ICA estimation method to find out the solutions of the independent components.
	- First, we need to find an objective function to estimate.
	  As we know, the central limit theorem is that the distribution of a sum of independent random variables tends to be a Gaussian distribution.
	  We define a variable y to be the linear combination of x. As you can see, y is also a linear combination of s. 
	  By central limit theorem, y is more gaussian than any of s. And if y equals one of the s, it is least gaussian. 
	  Therefore, we can maximize the non-gaussianity of y, to find the independent components s.
	  To do this, we need methods to measure the non-gaussianity.
	- The paper introduced 5 measurements.
	- The first is kurtosis.
	  As a gaussian random variable has 0 kurtosis, while for most nongaussian random variables, kurtosis is nonzero.
	  Therefore, we can measure the non-gaussianity by maximizing the absolute value of the kurtosis of y.
	- The second is negative entropy.
	  A fundamental result of information theory tells us a gaussian variable has the largest entropy among all random variables of equal variance.
	  Therefore, we can measure the non-gaussianity by maximizing the negative entropy, which represents the difference between y and a gaussian variable. 
	  In practice, we use these two equations to approximate the neg-entropy.
	- The third is mutual information.
	  It measures the dependence between random variables. 
	  It's non-negative, and zero if and only if the variables are independent.
	  Therefore, we can measure sure the non-gaussianity by minimizing mutual information
	- The forth is Likelihood
	  We have the log-likelihood and the output entropy of a neural network. 
	  Researchers have proved that maximizing likelihood is equivalent to minimizing mutual information under some constraints.
	- The last is projection pursuit
	  It is a technique developed for ﬁnding "interesting" projections of multidimensional data. One of the interesting projections shows the least Gaussian distribution, while Gaussian distribution is **least** interesting.
	  Therefore, we can use this technique to measure non-gaussianity.
	- The paper also mentioned some data preprocessing methods, such as centering, whitenning and band-pass filtering. 
	  They are used to simplify the algorithms, reduce the number of parameters to be estimated and remove noise signal for time-signal data. 
	  Attention! You can only use those methods where the ICA model remains valid.
- DME Presentation QA 准备
	- In practice, how to make a decision about using which measurement of nongaussianity. Shall we choose the measurement empirically or we have to make a choice based on some certain rules.
		- In practice, we often use FastICA, which is a very efficient method for maximizing the contrast function. It can can be considered as a fixed-point algorithm for maximum likelihood estimation.
	- Why is intuition about the equivalence between minimization of mutual information and maximization of likelihood hold. Does it mean these two measurements are essentially identical but describe the problem from different angles?
		- motivation中的鸡尾酒会问题 cocktail party problem，假设了x和s数量相等
		- 后面基本上也是基于这个假设来做推导
		- 然后对于x大于s和x小于s的情况，学术界都有研究
		- 论文中的project persuit方法是一种用于处理s比x少的情况的方法
	- converge
		- 比如kurtosis受到outliner影响
		- maximum likelihood收到估计函数不正确的影响
		- If the convergence is not satisfactory, one may then increase the sample size.
	- PCA and ICA
		- 可以同时用PCA和ICA。进行ICA之前需要对数据预处理，比如白化。PCA就是一种白化方法。白化的目的是去除特征之间的相关性，并且让所有特征有相同的方差。方便后面的计算。
		- 相同点：PCA和ICA都是已知一个数据x，找一组新的basis，x可以表示为这个basis的线性组合；
		- 不同点：
			- PCA：find the one that best explains the variability of your data 找到的这组basis，可以最大化解释原数据的variability；ICA：find the one in which each vector is an independent component of your data 找到的这组basis，互相之间是独立的。
			- PCA components are orthogonal
			- ICA components are not orthogonal
			  讲
	-
-
  �够简化计算
	-
-