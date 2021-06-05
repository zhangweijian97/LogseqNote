---
title: Inception Score
---

- Name
	- [[Inception Score]]
- Type
	- #PermanentNote
- 笔记
	- 两个标准来衡量GAN的性能
		- quality of the generated images
			- $p(y|x)$具有低熵 [[Entropy]]，高预测性
		- diversity of the generated images
			- $p(y)$ 具有高熵，分布均匀，图像多样
	- 公式
		-
		  $$
		  \mathbf{I S}(G)=\exp \left(\mathbb{E}_{\mathbf{x} \sim p_{g}} D_{K L}(p(y \mid \mathbf{x}) \| p(y))\right)
		  $$
	- 计算
		- 生成N个图片
		- 输入到Inception V3（在ImageNet数据集上预训练）
		- 输出的向量（1000维）即图片属于各个类别的概率分布$p(y|x)$
		- 求平均得到边缘分布 $p(y)$
			-
			  $$
			  \hat{p}(y)=\frac{1}{N} \sum_{i=1}^{N} p\left(y \mid \mathbf{x}^{(i)}\right)
			  $$
		- 计算KL散度
			-
			  $$
			  D_{K L}(P \| Q)=\sum_{i} P(i) \log \frac{P(i)}{Q(i)}
			  $$
		- 上面公式的期望用 求和然后平均 来替代
	- 缺点
		- 略
	- 重新训练
		- 因为研究所使用的数据集往往不是ImageNet，所以需要fine-tuning Inception V3
		- TensorFlow
			- https://github.com/tensorflow/hub/blob/master/examples/image_retraining/retrain.py
				- 升级版 https://github.com/tensorflow/hub/tree/master/tensorflow_hub/tools/make_image_classifier
		- Pytorch
			- [Torchvision模型微调](https://pytorch.apachecn.org/docs/1.0/finetuning_torchvision_models_tutorial.html)
- 联想
	- 用来评估GANs的性能
		- [[Generative adversarial network]]
	- 升级版 FID
		- [[Fréchet Inception Distance]]
	- 用来做 ((6036865a-0182-4f5d-b3ed-7c4a243beefc))
- 入档
	- #EvaluationMethod #MachineLearning #GAN
- 索引
	- [inception score trained on birds](https://github.com/hanzhanggit/StackGAN-inception-model)
	  id:: 60411a97-c2a7-4f35-a818-a3955b69c8f3
	- [inception score trained on coco](https://github.com/openai/improved-gan/tree/master/inception_score)
	  id:: 60411aa7-7588-475a-babf-6faf493b6fc5
	- 博客文章 [Inception Score原理及其代码实现](https://zhuanlan.zhihu.com/p/263652288) [InceptionScore](https://fx0809.gitee.io/2020/10/09/InceptionScore/)
	- Github Repo [Inception Score Pytorch](https://github.com/sbarratt/inception-score-pytorch)
	- Arxiv [Improved Techniques for Training GANs](https://arxiv.org/abs/1606.03498)
	- Github Repo TensorFlow [Inception Score](https://github.com/tsc2017/Inception-Score)