---
title: MLP project final report abstract
---

### GAN已经在 从文本生成图像 方面取得很好的结果
### 但是目前的工作大多关注从文本生成简单图片，如花朵。
### 从文本生成细粒度的人脸仍然是一个困难的任务。
### 并且因为数据集的缺乏，在 文本生成人脸 领域只有极少数的研究。
### 用于文本生成人脸的GAN模型都基于cGAN，它包含这几个结构：生成器（image decoder），判别器（image encoder），和text encoder（to condition on input text）
### 最近OpenAI发表了CLIP，包括一个text encoder 和 一个image encoder，在400M图像-文本数据集上预训练的模型。
### 我们尝试用CLIP的TE和IE替换掉GAN的相对应部分。
### 我们选择了AttnGAN作为baseline model。它引入了Attention机制到GAN，并且用COCO数据集生成了细粒度的图片。
### 我们在一个新的文本-人脸数据集 Face2Text 1.0. 上进行了实验。
### 我们使用了 这个那个 评估方法
### 我们发现了 这里那里
### 翻译一波
### Generative Adversarial Networks (GANs) have been developed for text to image synthesis and achieved a good performance.
### However, most of the current works are limited to synthesising simple images like flowers.
### Synthesising the human face from text is a tough task.
### And due to the lack of dataset, there are few research work focusing on this area.
### The related GAN models are based on cGAN, which includes a generator, a discriminator and a text encoder. The generator can be seen as an image decoder and the discriminator can be seen as an image encoder.
### Recently, OpenAI published their newest work, the CLIP, which is pretrained on a dataset that has 400M text-image pairs. CLIP includes a text encoder and an image encoder.
### In this paper, we replace the text encoder and image encoder of a GAN model with the ones from CLIP.
### We choose the AttnGAN as the baseline, because it achieved a good performance on synthesising fine-grain image on COCO dataset, and it first introduced the attention mechanism into GAN, which also motivates the CLIP.
### We use a new face dataset called Face2Text 1.0, which includes 4000 faces with captions and it is currently the largest dataset on this type.
### We use **blabla** to evaluate our methods. It shows **some** results.