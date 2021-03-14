---
title: MLP Project final report related works
---

## 要不就不细分小结
## 整理思路
### 先倒推
#### 我们的模型基于AttnGAN和CLIP
#### 我们的模型的应用领域是文本生成人脸
#### 文本生成人脸脱胎于文本生成图片
#### 文本生成图片又源自从噪声直接生成图片
### 然后正推
#### 图片生成，GAN包括生成器和判别器。生成器分为文本编码器和图片解码器，分别的作用。判别器，就是一个图片编码器加上一个线性层。普通的GAN从随机噪声中采样。
#### 从文本生成图片，Reed首发，用到conditional GAN。conditional GAN 把 文本编码向量和随机噪声结合作为生成网络的输入。后人推进，暂略。缺点，没有分区域的掌控
#### AttnGAN引入了注意力机制，能够对应起单词和图片的区域，实现生成高质量细粒度的图片
#### 文本生成人脸，因为数据集的缺乏，研究很少，有如下，暂略
#### CLIP，包含预训练的文本和图片的编码器。zero-shot。注意力。
#### 受此启发，我们用CLIP的文本编码器和图片编码器来替换GAN的对应部分。对所有基于Conditional GAN的网络都可以进行这样的替换。
## 试写
### 从文本生成 高精度 细粒度 图片的任务是非常有挑战性的。已经有一些深度生成模型做到了很不错的效果（需要再找一些材料，只有AttnGAN的相关工作提到了几个）。与之对比，GAN是另一种架构，并且证明能够生成更**细致**sharper的图片。
#### 深度生成模型
##### Mansimov， Generating images from captions with attention
##### Gregor，DRAW: A recurrent neural network for image generation.
##### Nguyen，Conditional iterative generation of images in latent space.
##### Reed，Parallel multiscale autoregressive density estimation
#### GAN
##### Radford，Unsupervised representation learning with deep convolutional generative adversarial networks.
##### Denton，Deep generative image models using a laplacian pyramid of adversarial networks
##### Salimans， Improved techniques for training gans.
##### Ledig，Photo-realistic single image superresolution using a generative adversarial network.
##### Isola，Image-to-image translation with conditional adversarial networks.
### （先水一波GAN生成图片的原理） 2014年Goodfellow 提出 GAN，包含生成器和判别器。生成器的作用，略。判别器的作用，略。因为这个网络从随机噪声中采样，作为生成器的输入，所以只能完成**图片生成**任务。
### 2014年，Mirza提出了conditional GAN，通过给生成器和判别器的输入添加标签，使得生成的图片依赖于输入的标签。
### 2016年，Reel首次证明了cGAN能够在**文本生成图片**上取得可行的结果。他使用了编码器解码器框架作为生成器。文本编码器将文本转换到语义空间。图片解码器从语义空间生成图片。
### Zhang 则提出了stackGAN来生成**高精度**的图片
### 以上存在问题，依赖于整个句子作为输入。失去了单独单词的信息。
### 2016年Vaswani提出Attention机制，成功用于建模multi-level。受此启发，AttnGAN利用Attention机制，考虑了单词和图片的sub-region之间的attention，设计了一个注意力生成网络和一个新的loss function called DAMSM loss。
### 同样启发于Attention，OpenAI提出了一个新的预训练任务来，并且在400 million 图片文本数据集，上训练，得到CLIP。
