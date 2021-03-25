---
title: MLP Project final report introduction
---

### 先介绍 从文本生成图像，以及这个技术的应用
#### （资料待收集，看一下其他几个论文的对应部分）
#### AttnGAN
##### art generation
##### computer-aided design
##### multimodal learning and inference across vision and language
##### [20, 18, 31, 19, 4, 29, 5, 1, 30]
### 然后解释 GAN 和 从文本生成图像 的关系
#### 先说original GAN，缺点，无法控制生成的图像
##### [[GAN Goodfellow 2014]]
#### 然后cGAN，生成图片依赖于输入的标签
#### 然后proGAN和stackGAN，生成高精度图片
##### ProGAN
#### 2016
#### attnGAN，引入attention增强文本和图片sub-region的关系，能够生成细粒度的图片
### 然后讲到从文本生成人脸
#### 先对比人脸和其他图像
##### 如花，鸟。
##### 人脸复杂，如皱纹
##### 文本高度抽象
#### 然后说一下缺乏数据集，所以就只有很少研究
##### 列一下仅有的几个研究和他们使用的数据集
##### T2F使用progan和stackgan，但是生成效果很差。作者的后续项目MSG-GAN可以生成高精度的图片但是diversity很差
##### Text2FaceGAN生成的图片精度很低
##### FTGAN基于
##### 目前最好的
### 最近OpenAI提出了CLIP。介绍两句。CLIP有很好的text encoder和image encoder。因为用来做 从文本生成图片 的GAN，的基本架构包含text encoder，image encoder和image decoder。受到启发，我们选了attnGAN作为baseline，然后替换了对应部分。我们设计了3个varient的模型。分别替换了text encoder，image encoder，以及同时替换。
### 我们使用了一个新的数据集Face2Text 1.0，它的前一个版本只包含400个图片，而它包含了4000张图片
### 通过定性分析和定量分析，我们发现新的CLIP-AttnGAN在
### 我们的贡献
#### 1. 提出了一个通用的提高GAN的性能的办法，用CLIP来替换GAN的对应部分。
#### 2. 我们在attnGAN上测试了这个方法，效果喜人。这个方法还能被用在其他GAN上面
#### 3. 我们使用了一个新的文本-人脸数据集。希望以后的研究者也能使用。