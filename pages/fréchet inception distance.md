---
title: Fréchet Inception Distance
---

- Name
	- [[Fréchet Inception Distance]]
- Type
	- #PermanentNote
- Permanent Notes
	- Inception Score 缺少合成图像与真实图像的比较
	- FID 越低，图像质量越好
	- $d^2 =||\mu_1-\mu_2||^2 + Tr(C_1+ C_2 - 2 \times \sqrt{C_1 \times C_2})$
		- 「mu_1」和「mu_2」指的是真实图像和生成图像的特征均值
		- C_1 和 C_2 是真实图像的和生成图像的特征向量的协方差矩阵
	- 和Inception Score都基于Inception V3，分类器相同，计算分数的过程不同
	- 有个[文章](https://blog.csdn.net/qq_37189298/article/details/108115284)说
	  #+BEGIN_QUOTE
	  FID并不使用Inception Net-V3的原本输出作为依据，它删除模型原本的输出层，于是输出层变为Inception Net-V3的最后一个池化层。这一层的输出是2048 维向量，因此，每个图像会被预测为2048个特征。
	  #+END_QUOTE
- 联想
	- 用来评估GANs
	- [[Inception Score]] 的升级版
	- 用来做 ((6036865a-0182-4f5d-b3ed-7c4a243beefc))
- 入档
	- 加合适的标签（归入对应的卡片盒）
	- #EvaluationMethod #MachineLearning #GAN
- 索引
	- Github Repo TF Official [TTUR](https://github.com/bioinf-jku/TTUR)
	- Github Repo TF [Fréchet Inception Distance](https://github.com/tsc2017/Frechet-Inception-Distance)
	- Github Repo PyTorch [FID score for PyTorch](https://github.com/mseitzer/pytorch-fid)
	- Arxiv [GANs Trained by a Two Time-Scale Update Rule Converge to a Local Nash Equilibrium ](https://arxiv.org/abs/1706.08500)
	- 博客文章 机器之心 [学习GAN模型量化评价，先从掌握FID开始吧](https://www.jiqizhixin.com/articles/2019-10-14-13)
	- [How to Implement the Frechet Inception Distance (FID) for Evaluating GANs](https://machinelearningmastery.com/how-to-implement-the-frechet-inception-distance-fid-from-scratch/)
- Literature Note
	- Bib
		-
		  ```Bib
		  @misc{Seitzer2020FID,
		    author={Maximilian Seitzer},
		    title={{pytorch-fid: FID Score for PyTorch}},
		    month={August},
		    year={2020},
		    note={Version 0.1.1},
		    howpublished={\url{https://github.com/mseitzer/pytorch-fid}},
		  }
		  ```
	-