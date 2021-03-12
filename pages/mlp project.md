---
title: MLP Project
---

### 资源
#### [DCGAN 教程](https://pytorch.apachecn.org/docs/1.7/22.html)
:PROPERTIES:
:id: 604025bb-1ba8-45b1-a886-9ae94553d1a2
:END:
#### ((603fd356-d8cf-4835-a88c-a6fa3ffd71ad))
#### [ImageNet](http://image-net.org/download-images)
#### [[CLIP]] 
:PROPERTIES:
:id: 60411750-41c8-4ada-a8ad-0d110c5e9565
:END:
#### DALL-E
##### https://openai.com/blog/dall-e/
##### 项目地址：
###### https://github.com/openai/DALL-E
##### 论文地址：
###### https://arxiv.org/abs/2102.12092
### 评估方法
#### 两个方法
##### [[Inception Score]]
##### [[Fréchet Inception Distance]]
#### 方案一，弃用
##### 把我们的模型丢去ImageNet训练，生成它的图片，然后跑Inception Score和FID
##### 原因
######
#+BEGIN_QUOTE
不能在一个数据集上训练分类模型，用来评估另一个数据集上训练的生成模型
#+END_QUOTE
###### Inception V3 是在 ImageNet 上训练的判别模型
###### 我们的模型是在F2T数据集上训练的生成模型
###### 数据集不同，把我们生成的图像放进Inception V3是没有意义的
#### **方案二，选用**
##### 把预训练的Inception V3拿过来，在我们的数据集上fine tuning一下（Text2FaceGAN在CelebA上微调），再评估。这样就是直接评估我们的数据集生成的图片。
###### **问题**是我们的数据集太小了，微调需要足够的数据集，Text2FaceGAN说要50M，网上则说每类至少100张
#### 问题
##### 要用tensorflow的还是pytorch的
###### 我先试试pytorch，我比较熟悉
##### 要用gpu吗，看github，两个都可以用gpu
###### 先试试cpu，看看速度和效果如何
#### 阅读 [Torchvision模型微调](https://pytorch.apachecn.org/docs/1.0/finetuning_torchvision_models_tutorial.html)
:PROPERTIES:
:now: 1614792290134
:END:
##### Inception V3是可选模型的一种
##### 微调
##### 部署dice环境
:PROPERTIES:
:now: 1614795158561
:later: 1614795157062
:END:
##### 注意inception_v3的输入大小为(299,299）
##### 初始化模型
##### 加载数据
##### 创建优化器
### Tutorial 6
#### abstract
##### 随机
##### resnet clip
##### transformer clip
##### clip
### CW3 Feedback
:PROPERTIES:
:id: 60436919-d155-43ba-8544-6c351ecc7a51
:END:
#### Overall:
##### Majour fluency and clarity issues. I’d advise using the free version of Grammarly as a starting point to improving these, and then potentially having a bi-lingual or native english speaker providing feedback on your report’s fluency and clarity.
##### Furthermore, there seems to be an overall confusion going on as to what your actual research proposal is here and how you motivate it. Ask me about this in a tutorial.
#### Abstract:
##### Sentence 1: A decent way to start, but not as good as it could be. Ask me about this in a tutorial.
##### Sentence 2: How do you know this? Is it just the data? What about the model efficiency? Maybe that’s another angle? Make sure your statements are precise and careful.
##### Sentence 3: This sentence doesn’t deliver any useful messages. Why is the fact that it contains only attributes a problem? What are ‘enough’ data points?
##### Sentence 4-5: You talk about specific datasets and what they contain. What’s the point?
##### Sentence 6: Feels out of place and does not work well with the previous context.
##### Sentence 7-8: It seems that you are a bit confused as to what you are doing here. You have a baseline of a known model on a new dataset, and then you are using CLIP as a pretrained embedding to see if that helps. You should write that explicitly and clearly. As its written it’s very hard to decipher and I am supposed to be your tutor who is aware of your work!
#### Introduction:
##### Paragraph 1: Are these the only potential applications? If not, you should state that. Motivating the problem of lacking datasets.
##### Paragraph 2: You describe some of the existing datasets and motivate the one you will be using. There are clarity issues as well as narrative and conciseness issues here. Ask me about more details in a tutorial.
##### Paragraph 3: 400M -> 300M.
##### Paragraph 4: Summarizes the key points, but could be done a lot more precisely and clearly.
##### Paragraph 5: This paragraph should not be part of this report. It’s about the project management side of things, it should be in your plan, not your introduction.
##### Paragraph 6: Lack of datasets and how you try to improve things.
#### The overall narrative here is a bit confusing. I suggest reading:
##### As a guide to your report writing.
###### a. https://cs.stanford.edu/people/widom/paper-writing.html
###### b. https://www.easterbrook.ca/steve/2010/01/how-to-write-a-scientific-abstract-in-six-easy-steps/
##### For samples of good papers and further tips.
###### c. http://karpathy.github.io/2016/09/07/phd/
###### d. https://old.reddit.com/r/MachineLearning/comments/85cwiu/d_wellwritten_paper_examples/
#### Dataset and Task:
##### There is no point in explaining how the dataset came to be and all of its revisions. Just state the dataset you use and why. You also mention your metric but do not explain what it is or how it works. Also, you never mention or describe your task in either mathematical notation or textual descriptions. Ideally you want something like ‘Our task, being text to image translation, involves learning a mapping f, that receives input datapoints x and generates bla bla bla.
#### Methodology:
##### In this section you must describe the methods you will be using in detail, as well as the exact way in which you will be utilize them. This is the single most important section where you explain your proposal.
#### Experiment Designs:
##### The key experimental checkpoints are good, however, this is not what this section is just about. You are supposed to describe and motivate all experiments that you intent to run, as well as explain what each one attempts to find out.
#### Experiment Results and Interim Conclusions:
##### We have discussed these in the tutorial. Feel free to ask more questions.
#### Extra questions:
##### We have discussed these in the tutorial. I’ll assume you have noted down the details
### MLP final report
#### 草稿 整理思路
##### 有点不知道从何下手，那就先发散思路
##### 比如大纲还是
###### abstract
###### introduction
###### related work
###### model
######
