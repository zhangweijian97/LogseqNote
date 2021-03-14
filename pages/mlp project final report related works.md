---
title: MLP Project final report related works
---

## 要不就不细分小结
## 整理一下思路
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
## 从文本生成图片的任务是非常有挑战性的。有如下深度生成模型（需要再找一些材料，只有AttnGAN的相关工作提到了几个）。与之对比，GAN能够生成更细致的图片（需要更多材料。
### 深度生成模型
#### Mansimov， Generating images from captions with attention
#### Gregor，DRAW: A recurrent neural network for image generation.
#### Nguyen，Conditional iterative generation of images in latent space.
####
