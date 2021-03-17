---
title: K-Adapter
---

## 临时笔记
### [知乎 2020|通过知识适配器向预训练模型中注入知识](https://zhuanlan.zhihu.com/p/106107747)
#### 动机
##### 研究问题：向大型预训练（语言）模型中注入知识
##### 背景：以无监督方式训练的语言模型很难捕获丰富的知识
##### [[预训练模型]]
###### [[GPT]]、[[BERT]]、[[XLNET]]
##### knowledge-driven
##### standard LM
##### 多任务学习
##### [[终身学习]]（[[continual learning]]）
###### 重新训练
###### 灾难性遗忘 [[catastrophic forgetting]]
##### 耦合的表示（entangled representations）
##### 笔记作者推荐阅读section 2
######
#+BEGIN_QUOTE
Note：这篇文章中Related Work部分对于向PLM中注入知识这一方向进行了很好的梳理，推荐阅读原文Sec. 2，相关工作的区别主要在于 a) knowledge sources 和 b) training objective；
#+END_QUOTE
#### 本文工作
##### 提出K-Adapter
##### 好处
###### 灵活、简便的向PLM中注入知识的方法
###### 进行持续知识融合
###### 产生解耦的表示
###### 保留了PLM产生的原始表示
###### 可以引入多种知识
##### Adapter
###### Knowledge-specific 模型
###### 作为一个插件加在PLM外部
###### 输入，PLM中间层输出的隐状态
###### 一种知识类型对应于一个Adapter
###### 一个PLM可以连接多个Adapter；
##### 涉及知识类型，数据来源
###### factual knowledge，将Wikipedia文本对齐到Wikidata三元组；
###### linguistic knowledge，对web文本进行依存分析得到；
##### 最终模型
###### 一个Pre-trained language model (PLM) 和两个Adapter
##### [[LAMA]]
##### 对比[[RoBERTa]]
##### 与先前工作的3个不同之处
###### 同时考虑了fact-related和linguistic-related的目标函数（为了同时引入两种类型的知识）；
###### 在注入知识的过程中，原始的PLM参数没有变化；
###### 可以支持持续学习，不同的知识适配器的学习是解耦的（独立的），后续再加入知识不会对已加入的知识产生影响；
#### 模型细节
##### 整体 论文图1
##### Adapter结构 论文图2
###### 结构
####### 每个Adapter模型包含K个adapter层，
######## 每个adapter层包含
######### N 个transformer层；
######### 2 个映射层；
######### 1 个残差连接；
###### 与PLM的连接位置：
####### 将adapter层连接到PLM中不同的transformer层上；
###### 和预训练模型的连接：
####### 当前adapter层的输入：
######## a) transformer层输出的隐藏层，
######## b) 前一个adapter层的输出，这两个表示进行concat；
####### Adapter模型的输出：
######## a) PLM最后一层的隐藏层输出，和
######## b) 最后一个adapter层的输出，进行concat作为最终的输出；
###### 预训练-微调阶段：
####### 不同的Adapter在不同的预训练任务上分别进行训练；
####### 对于不同的下游任务，K-Adapter采用和RoBERTa相同的微调方式；
######## 只使用一种Adapter时，Adapter模型的最终输出作为task-specific层的输入；
######## 使用多种Adapter时，将多个Adapter模型的输出进行concat作为task-specific层的输入；
###### 预训练设置 略
##### Factual Adapter
###### [[Factual Knowledge]] 主要来源于文本中实体之间的关系；
###### 数据集 [[T-REx]]
###### 预训练任务：关系分类
####### 给定context和一对实体，对其间关系标签进行分类；
##### Linguistic Adapter
###### [[Linguistic Knowledge]] 主要来源于文本中词之间的依存关系；
###### 数据集：[[BookCorpus]]
###### 预训练任务：依存关系分类
####### 预测给定句子中每个token在依存分析结果中的father index；
#### 实验
##### 三个下游任务
###### b) [[entity typing]]，
###### c) [[question answering]]；
###### a) [[relation classification]]，
##### QA结果，表格3
##### LAMA query 生成，预测被mask位置的词
## [官方github库](https://github.com/microsoft/k-adapter)
##
