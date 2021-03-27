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
#### [[CLIP OpenAI 2021]] 
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
#### [[MLP评估方法收集统计]]
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
:PROPERTIES:
:id: 6054eb90-0f1d-4d73-9728-ebee7efdc43c
:END:
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
##### 比如大纲是
###### abstract
###### introduction
###### related work
####### text to image
####### text to face
####### clip
###### model
####### text encoder
####### image decoder
####### discriminator
####### loss function
###### Experience
####### Performance on face2text 1.0
####### compare with previous methods (evaluation)
######## IS
######## FID
######## FSD
######## FSS
###### conclusion
##### 那对于abstract和introduction，我需要看一下cw3 feedback来整合一下
##### related work部分，大体上参考那几篇最新的text2face的论文。但是clip的部分不确定怎么写。现在应该不可能已经出来引用了clip的论文，但可以试试找找。如果不行，就凭感觉直接写吧
###### [[FTGAN Chen 2019]]
###### [[TTF-HD Wang 2020 Faces la Carte]]
###### [[CLIP OpenAI 2021]]
##### 模型部分，对现在的我，问题还很大。我完全没理解他们的架构。需要先看attngan的论文，对attngan和clip都熟悉之后，确定上面大纲中的四个部分的原理和结合。然后询问林扬和楚婷是如何替换clip，构建我们自己的模型
###### [[AttnGAN Xu 2018]]
##### 实验部分，问题也不小。第一部分模型效果，是队友负责完成的。我只需要理解其结果，放上来。但是第二部分模型评估，似乎有不少实验要做。除了实现这些方法。整个对比流程的设计和运行也要花不少时间。
##### 中间三部分完成的话，结论介绍和概述倒是不难了。
##### 估计了一下，上述内容至少20+小时。换算成天数，是全天的4天以上。而且是只算我一个人。没加上队友的时间。恐怖。
##### 安排一下顺序。
##### 有没有办法边看边写？比较难。这个模型比较复杂。分成几轮比较好。要不然每个模块会相当的卡顿。
##### 感觉related work的内容还不够，即便看了那两篇。我还需要更多的材料。
##### 第一轮，先看attngan，做笔记。看ftgan，做笔记。然后试一试找引用clip的论文，做笔记。需要几个小时，可能需要两个时间块
##### 第二轮，先把related work的架子搭起来，有什么先填进去。等写完再看看还缺什么。也需要几个小时，应该需要一个时间块，也可能2个。
##### 第三轮，到这里，我应该一方面对GAN的大致局面有了解，同时对模型架构也有基本了解。所以这一轮去找林扬给我答疑。理解清楚我们的模型架构，然后把模型这一部分写了。这至少需要2-3个时间块。很可能需要更多
##### 第四轮。由于以上部分需要大量时间，显然短时间内没办法继续evaluation method的实现。问一问林扬能否take这部分。顺利的话，等我完成前三轮，楚婷和林扬会完成模型的实现和测试。并且林扬会完成评估方法的实现和实验。所以这一轮，我首先需要了解他们的实验流程和结论，收集各种图片素材等。然后写实验部分的论文。和队友沟通需要1个时间块，撰写论文需要2-3个时间块。
##### 第五轮，以上部分包含了整个项目的主体内。到这里我应该已经写完了相关工作，模型和实验三个部分。所以这一轮我要回顾cw3和cw3feedback。提取可用的素材，然后写introduction，conclusion，和abstract。回顾就需要大半个时间块，加上思考，算1个时间块。然后撰写应该在2-3个时间块。
##### 一个时间块在1-3个小时不等。算下来，在也符合刚才估计的20+小时。根据低估原理，实际花费应该在30小时以上。今明两天可用时间加起来可能在8-12小时。所以需要再来两个两天。
##### 今明两天最好能完成前两轮，第三轮应该有一部分进展。
##### 周日（下）周一周二应该是毕设和RL。
##### 那周三周四继续推MLP。继续第三轮和第四轮的一部分。
##### 最后一周再找两天出来把剩下的完成。相当勉强。哎
##### 那么现在开始第一轮
##### 补充，related work除了gan模型方面，和clip方面。还需要收集一下他们用的评估方法和为什么用。也放到第一轮吧
#### 第一轮 看论文 理解模型架构 了解相关工作 收集评估方法
##### 材料
###### [[CLIP OpenAI 2021]]
##### [[AttnGAN Xu 2018]]
##### [[TTF-HD Wang 2020 Faces la Carte]]
##### [[FTGAN Chen 2019]]
#### 第二轮
##### [[MLP Project final report related work]]
#### 小组讨论 我们的模型
##### variants
###### 替换text encoder
####### sentence feature
###### 替换image encoder（还没做
###### 替换判别器（image encoder）
####### CLIP已经是很好的判别器，需要先训练生成器到非常好的程度，再训练判别器
####### 会影响生成器的adversarial loss，其中conditional loss替换为(未定)
##### 句子长度问题，调整DAMSM参数，重新训练
#### 第三轮 每个小结分别准备
##### [[MLP project final report abstract]]
##### [[MLP Project final report introduction]]
##### [[MLP Project final report dataset and task]]
###### [[MLP评估方法收集统计]]
####### FID
####### FSD
##### [[MLP Project final report methodology]]
###### 草稿
####### Ls1, Ls2
####### text encoder, sentence feature
####### replace text only
####### replace damsm only
######## compare hyperparameter
####### replace both
######## compare hyperparameter
##### [[MLP Project final report experiments]]
##### [[MLP Project final report related work]]
#### 第四轮 去 overleaf 扩写
##### abstract 完成
##### introduction 完成
##### dataset and task 完成
##### methodology 完成
##### experiment 队友负责
##### related work
#### 第五轮
