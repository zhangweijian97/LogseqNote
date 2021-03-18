---
title: CLIP OpenAI 2021
---

## 资源
### [OpenAI CLIP: ConnectingText and Images (Paper Explained)](https://www.youtube.com/watch?v=T9XSU0pKX2E)
## 学习笔记
### Paper Title:
#### Learning Transferable Visual Models From Natural Language Supervision
### zero-shot classifier
### take image, predict text
#### whereas DALL-E take text, predict image
### how likely of the image to be "a photo of dog"
### zero shot
#### 不用在什么task上训练
### what clip do
#### 训练
##### a set of images into image encoder, a vector in latent space, I1, I2...
##### a set of text to text encoder, T1, T...
##### T1 correspon to I1, so and so on
##### 不再用I1来预测text（其他模型）
##### 而是，问，T1到Tn中，谁和I1更接近？
##### 最大化对应的inner projct
##### 最小化其他的
##### 行和列分别softmax
#### 推理
##### 进来一个图片，一堆text
##### 就知道最相关的那一个text
### linear probing
#### 在clip后面加一层，对一个task训练
### 对比
#### few-shot linear probes
#### clip没训练都比few-shot linear probes的BiT-M的16个epoch好
#### clip自己加上linear probe就更好了