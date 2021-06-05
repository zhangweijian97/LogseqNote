---
title: DME Presentation 第一遍 理解内容 收集要素
---

	- 本部分关键在于目标函数。讲了如何去估计ICA模型中的参数
	- 前情理解
		- 动机，问题举例
			- 前面的部分，首先引出了动机，描述了一个有两个演讲者，两个麦克风的情况下，麦克风记录的信号表示为x1和x2，演讲者的说话信号记为s1和s2。这里已知x1和x2，但是不知道s1和s2。x和s的关系，x是s的加权和，表示为：
				-
				  $$
				  \begin{array}{l}
				  x_{1}(t)=a_{11} s_{1}+a_{12} s_{2} \\
				  x_{2}(t)=a_{21} s_{1}+a_{22} s_{2}
				  \end{array}
				  $$
				- a是各种影响录音的参数。
			- 所以在这个情况下，如果能用x来估计出s，是非常有用的技术。也就是还原了声道。
			- 已知参数a，可以很方便地用传统方法求出s。 但是如果不知道参数，就不能用传统方法了
			- 所以，引出了本文的方法，[[ICA Independent Component Analysis]] 独立成分分析
			- ICA假设了信号s互相之间是统计独立的。正符合上述情况。ICA能够估计出参数a，继而能够从x中分离出 s
		- 定义，模型，参数解释
			- 统计因变量模型 statistical “latent variables”
				- n个独立成分s，n个线性混合信号x
				-
				  $$
				  x_{j}=a_{j 1} s_{1}+a_{j 2} s_{2}+\ldots+a_{j n} s_{n}, \text { for all } j
				  $$
				- 每个x和s都是随机变量，观测值 $$x_{j}(t)$$ 是样本值。
				- 假设混合变量和独立分量都具有零均值（也可以先中心化）
				- 将上式用矩阵表示
					-
					  id:: 604403e5-4961-4684-b3a3-324f33967312
					  $$\mathbf{x}=\mathbf{A} \mathbf{s}$$
				- 或者用列向量表示 $$\mathbf{x}=\sum_{i=1}^{n} \mathbf{a}_{i} s_{i}$$
				- 上面几个公式就称为独立成分分析或ICA模型
				- ICA模型是生成模型，描述了观测数据是如何通过混合元素s_{i}生成的
				- 独立成分是隐变量，不能被直接观测
				- 混合矩阵$$\mathbf{A}$$，假设是未知的
				- 只能观察到x，用x估计A和s
			- ICA假设
				- 成分$$s_{i}$$是统计独立的。而且还假设独立成分是**非高斯分布**的。
					- 第四章就要重点讲非高斯分布
				- s的分布未知
				- A是方阵，其逆矩阵是W，所以
				-
				  id:: 6043fab8-579c-4fbb-887d-0d59e991afcd
				  $$
				  \mathbf{s}=\mathbf{W} \mathbf{x}
				  $$
			- ICA的不确定性
				- 不能确定独立成分的方差
					- 所以直接假设方差是1
					-
					  $$
					  E\left\{s_{i}^{2}\right\}=1
					  $$
				- 不能确定独立成分的顺序
					- 公式中s的顺序可以随意换
			- 图解，略
				- 给了个简单的例子，两个x两个s，观察两个x，确定一个s，得到另一个s
		- 独立性
			- 如果关于y_{1}值的信息没有给出关于y_{2}值的任何信息，则变量y_{1}和y_{2}被认为是独立的
			- 公式
				-
				  $$
				  p\left(y_{1} y_{2}\right)=p_{1}\left(y_{1}\right) p_{2}\left(y_{2}\right)
				  $$
				- 其中
					-
					  $$
					  p_{1}\left(y_{1}\right)=\int p\left(y_{1}, y_{2}\right) d y_{2}
					  $$
					- y2同理
			- 推导之后得到
				-
				  $$
				  E\left\{h_{1}\left(y_{1}\right) h_{2}\left(y_{2}\right)\right\}=E\left\{h_{1}\left(y_{1}\right)\right\} E\left\{h_{2}\left(y_{2}\right)\right\}
				  $$
				- 后面用到
			- 独立independent和不相关Uncorrelated
				- 不相关指两个随机变量y_{1}和y_{2}的协方差为0
					-
					  $$
					  E\left\{y_{1} y_{2}\right\}-E\left\{y_{1}\right\} E\left\{y_{2}\right\}=0
					  $$
				- 独立一定不相关，但是不相关不一定独立
			- 高斯变量不能独立
				- 我们假设混合矩阵\mathbf{A}是正交的，且s_{i}是高斯变量。那么x_{1}和x_{2}是高斯变量，且不相关、方差为1。联合密度略，分布图略。
				- 密度完全对称，因此不包含混合矩阵A的列向量方向的任何信息。A不能被估算
				- 但 如果只有一个独立分量是高斯分布，那么仍然可以估计ICA模型。
	- 我负责的部分，ICA估计原理
		- 优化问题：最大化非高斯性
			- 复苏
			- 传统，高斯
			- {{embed [[中心极限定理]] }}
			- recall
				- {{embed ((604403e5-4961-4684-b3a3-324f33967312))}}
				- x是独立成分s的混合
			- 因为我们只知道x，所以将要估算的独立成分记为y，y是x的线性组合
				-
				  $$
				  y=\mathbf{w}^{T} \mathbf{x}=\sum_{i} w_{i} x_{i}
				  $$
				- w是待求向量
			- recall
				- {{embed ((6043fab8-579c-4fbb-887d-0d59e991afcd))}}
				- W是A的逆矩阵
			- 所以如果w是W中的一行，那y就是s
			- 问题：如何使用中心极限定理去确定\mathbf{w}使得它等于矩阵\mathbf{A}的逆的一行
			- 联立y对x的表达式，和x对y的表达式，可以得到y关于s的表达式
				-
				  $$
				  y=\mathbf{w}^{T} \mathbf{x}=\mathbf{w}^{T} \mathbf{A} \mathbf{s}=\mathbf{z}^{T} \mathbf{s}
				  $$
				- 其中 $$\mathbf{z}=\mathbf{A}^{T} \mathbf{w}$$
				- y是s_{i}的线性组合，权重为z_{i}，
			- 因为 [[中心极限定理]] 说两个独立随机变量的和比原始的变量更接近高斯分布，
			- 所以 $$\mathbf{z}^{T} \mathbf{s}$$ 比任意一个$s_{i}$更接近高斯分布
			- 而当它等于其中一个$s_{i}$时，就变成最小高斯（最大化非高斯性）。
				- 这时候z只有一个非零元素zi
			- 所以问题转换为，选取$$\mathbf{w}$$，使得 $$\mathbf{w}^{T} \mathbf{x}$$ 非高斯性最大。
			- 与此同时，这个w对应的z只有一个非零元素
			- 找到一个w，也就找到一个y，且y是一个独立分量
			- 小结一下，**目标问题**：最大化 $$\mathbf{w}^{T} \mathbf{x}$$ 的非高斯性
			- 理论上来说，这个问题有2n个解，每个独立分量都有两个（y） ，对应正负s
			- 虽然不知道为什么，但是必须找出所有的局部最大值，可以用 **适当变换（即白化）空间中的正交化**的方法
		- 度量非高斯性
				- 既然问题是最大化非高斯性，那么就需要一些方法，来度量它
			- 第一个方法，峰度
				- 峰度公式
					-
					  $$
					  \operatorname{kurt}(y)=E\left\{y^{4}\right\}-3\left(E\left\{y^{2}\right\}\right)^{2}
					  $$
				- 因为y的方差是1，所以化简
					-
					  $$
					  \operatorname{kurt}(y)=E\left\{y^{4}\right\}-3\left(E\left\{y^{2}\right\}\right)^{2}=E\left\{y^{4}\right\}-3
					  $$
				- 高斯变量的峰度是0
				- 非高斯变量，其峰度非零。（极少数的非高斯变量的峰度为0。）
					- 可正可负；
					- 具有负峰度的随机变量称为亚高斯，
						- 例子，均匀分布
					- 具有正峰度的随机变量称为超高斯
						- 例子，拉普拉斯函数
				- **优化问题**：非高斯性通常通常通过**峰度的绝对值或平方**来度量
					- 越大，非高斯性越强
				- 峰度的性质
					-
					  $$
					  \begin{array}{l}
					  k u r t\left(x_{1}+x_{2}\right)=\operatorname{kurt}\left(x_{1}\right)+\operatorname{kurt}\left(x_{2}\right) \\
					  \operatorname{kurt}\left(\alpha x_{1}\right)=\alpha^{4} \operatorname{kurt}\left(x_{1}\right)
					  \end{array}
					  $$
					- x1，x2是独立随机变量，a是常数
				- recall，y的表达式
					-
					  $$
					  y=\mathbf{w}^{T} \mathbf{x}=\mathbf{w}^{T} \mathbf{A} \mathbf{s}=\mathbf{z}^{T} \mathbf{s}=z_{1} s_{1}+z_{2} s_{2}
					  $$
				- 根据性质得到
					-
					  $$
					  \operatorname{kurt}(y)=\operatorname{kurt}\left(z_{1} s_{1}\right)+\operatorname{kurt}\left(z_{2} s_{2}\right)=z_{1}^{4} \operatorname{kurt}\left(s_{1}\right)+z_{2}^{4} \operatorname{kurt}\left(s_{2}\right)
					  $$
				- y的方差是1，所以
					-
					  $$
					  E\left\{y^{2}\right\}=z_{1}^{2}+z_{2}^{2}=1
					  $$
				- 优化问题转换为
					-
					  $$
					  |\operatorname{kurt}(y)|=\mid z_{1}^{4} \operatorname{kurt}\left(s_{1}\right)+z_{2}^{4} \operatorname{kurt}\left(s_{2}\right)|
					  $$
				- 因为s1，s2是均值为0方差为1的独立变量，上面的是单位圆
				- 假设峰度有相同符号，可以去掉绝对值
				- 初始化一个w，通过x计算出y的峰度，用梯度上升法来更新w，就可以找到w，对应峰度局部最大
			- 第二个方法，负熵
				- 随机变量的熵可以被解释为观察变量包含的信息量。变量越随机，越不可预测，那么它的熵越大
				- 熵
						-
						  $$
						  H(Y)=-\sum_{i} P\left(Y=a_{i}\right) \log P\left(Y=a_{i}\right)
						  $$
				- 差分熵
					-
					  $$
					  H(\mathbf{y})=-\int f(\mathbf{y}) \log (f(\mathbf{y})) d \mathbf{y}
					  $$
				- 在信息论中有个基本的结论：在所有方差相等的随机变量中，高斯变量的熵最大。
				- 高斯分布是所有分布中最“随机”的。
				- 随机变量的分布越集中，其熵越小。
				- 负熵，作为非高斯性度量，越大，非高斯性越强
					-
					  $$
					  J(\mathbf{y})=H\left(\mathbf{y}_{\text {gauss }}\right)-H(\mathbf{y})
					  $$
				- **优化问题**：最大化负熵
				- 负熵难计算，用近似方法，
					- 高阶矩
						-
						  $$
						  J(y) \approx \frac{1}{12} E\left\{y^{3}\right\}^{2}+\frac{1}{48} k u r t(y)^{2}
						  $$
						- 受到峰度的非鲁棒性的影响
					- 基于最大熵原理
						-
						  $$
						  J(y) \approx \sum_{i=1}^{p} k_{i}\left[E\left\{G_{i}(y)\right\}-E\left\{G_{i}(v)\right\}\right]^{2}
						  $$
						-
						  $$
						  J(y) \propto[E\{G(y)\}-E\{G(v)\}]^{2}
						  $$
						-
						  $$
						  G_{1}(u)=\frac{1}{a_{1}} \log \left(\cosh a_{1} u\right)
						  $$
						-
						  $$
						  G_{2}(u)=-\exp \left(\frac{-u^{2}}{2}\right)
						  $$
						- 计算速度快，而且还有些比较不错的统计特性，尤其是鲁棒性。
			- 第三个方法，互信息最小化
				- 根据差分熵，定义互信息
					-
					  $$
					  I\left(y_{1}, y_{2}, \ldots, y_{m}\right)=\sum_{i=1}^{m} H\left(y_{i}\right)-H(\mathbf{y})
					  $$
				- 它等于联合密度f(y)和其边缘密度乘积之间的散度，它总是非负的，只有当变量之间统计独立时为0。
				- 如果y_{i}是独立的，那么它们彼此之间就没有任何信息，即互信息为0。
				- 即，优化目标：最小化互信息
				- 特性，对于可逆的线性变换 $$\mathbf{y}=\mathbf{W} \mathbf{x}$$
					-
					  $$
					  I\left(y_{1}, y_{2}, \ldots, y_{n}\right)=\sum_{i} H\left(y_{i}\right)-H(\mathbf{x})-\log |\operatorname{det} \mathbf{W}|
					  $$
				- 因为yi不相关，且方差是1：
					-
					  $$
					  E\left\{\mathbf{y} \mathbf{y}^{T}\right\}=\mathbf{W} E\left\{\mathbf{x} \mathbf{x}^{T}\right\} \mathbf{W}^{T}=\mathbf{I}
					  $$
					-
					  $$
					  \operatorname{det} \mathbf{I}=1=\left(\operatorname{det} \mathbf{W} E\left\{\mathbf{x} \mathbf{x}^{T}\right\} \mathbf{W}^{T}\right)=(\operatorname{det} \mathbf{W})\left(\operatorname{det} E\left\{\mathbf{x} \mathbf{x}^{T}\right\}\right)\left(\operatorname{det} \mathbf{W}^{T}\right)
					  $$
				- 所以det W必须是常量，所以推导得
					-
					  $$
					  I\left(y_{1}, y_{2}, \ldots, y_{n}\right)=C-\sum_{i} J\left(y_{i}\right)
					  $$
					- 表示了互信息和负熵的关系
					- C是常量
					- 最小化互信息，相当于最大化负熵
			- 第四个方法，最大似然估计
				- 和信息最大化原则相似
				- log似然函数
					-
					  $$
					  L=\sum_{t=1}^{T} \sum_{i=1}^{n} \log f_{i}\left(\mathbf{w}_{i}^{\mathrm{T}} \mathbf{x}(t)\right)+T \log |\operatorname{det} \mathbf{W}|
					  $$
					- fi是si的密度函数
					- x(t)是x的实现
				- y的密度，公式
					-
					  $$
					  p_{x}(\mathbf{W} \mathbf{x})|\operatorname{det} \mathbf{W}|
					  $$
					- px是x的密度
				- 基于最大化具有非线性输出的神经网络的输出熵（或信息流）
					-
					  $$
					  L_{2}=H\left(\phi_{1}\left(\mathbf{w}_{1}^{T} \mathbf{x}\right), \ldots, \phi_{n}\left(\mathbf{w}_{n}^{T} \mathbf{x}\right)\right)
					  $$
					- infomax原则
					- 研究者已经证明了infomax原则相当于最大似然估计
					- 要求神经网络中的非线性\phi_{i}是密度函数f_{i}的积分
				- log似然的期望
					-
					  $$
					  \frac{1}{T} E\{L\}=\sum_{i=1}^{n} E\left\{\log f_{i}\left(\mathbf{w}_{i}^{T} \mathbf{x}\right)\right\}+\log |\operatorname{det} \mathbf{W}|
					  $$
					- 如果fi是wiTx的分布，右边第一项等同于 $$-\sum_{i} H\left(\mathbf{w}_{i}^{T} \mathbf{x}\right)$$
					- 即，似然和互信息的负相等，少一个常量
			- 第五种方法，投影跟踪 projection pursuit
				- 找到方向，使数据在这些方向上的投影具有有趣的分布
				- 即显示最低高斯分布的方向
				- 投影追踪使我们能够解决独立分量s_{i}比原始变量x_{i}少的情况
				- 在投影跟踪的公式中，没有关于独立分量的数据模型或假设。
				- 如果ICA模型成立，优化ICA非高斯度量度量会产生独立的分量; 如果模型不成立，那么我们得到的是投影跟踪方向。
		- 数据预处理
			- 中心化
				-
				  $$\tilde \mathbf{x} = \mathbf{x} - E[\mathbf{x}]$$
				- 估计完成之后
				-
				  $$\mathbf{s} = \tilde \mathbf{s} + \mathbf{W}E[\mathbf{s}]$$
			- 白化
				- 即向量元素是不相关的且方差是一致的
					-
					  $$
					  E\left\{\tilde{\mathbf{x}} \tilde{\mathbf{x}}^{T}\right\}=\mathbf{I}
					  $$
				- 一种方式，特征值分解
					-
					  $$
					  \tilde{\mathbf{x}}=\mathbf{E} \mathbf{D}^{-\frac{1}{2}} \mathbf{E}^{T} \mathbf{x}=\mathbf{E D}^{-\frac{1}{2}} \mathbf{E}^{T} \mathbf{A} \mathbf{s}=\widetilde{\mathbf{A}} \mathbf{s}
					  $$
					- 矩阵 $$\widetilde{\mathbf{A}}$$ 正交，方便计算
			- 特定应用的预处理
				- 不会影响模型，因为
					-
					  $$
					  \mathbf{X}=\mathbf{A S}
					  $$
					-
					  $$
					  \mathbf{X}^{*}=\mathbf{X} \mathbf{M}=\mathbf{A} \mathbf{S} \mathbf{M}=\mathbf{A} \mathbf{S}^{*}
					  $$