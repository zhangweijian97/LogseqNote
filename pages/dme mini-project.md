---
title: DME mini-project
---

## 主题
### Predicting cuisines of recipes
## 团队
### s52119299-weijian zhang
 s2018229-xi zhao
 s2093718-yunbo liu
 s2060292-shifeng xu
## 理解数据
### citiesDistMat['citiesDistMat']
#### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210316220014.png)
### recipes['recipes'].shape
#### (4236, 709)
#### 内容是0和1，应该和另外几个recipes文件内容一样
#### 行表示食谱
#### 列表示食材
### labels['labels'].shape
#### (4236, 1)
#### 所属食物，也就是标签，内容分别是数字1到12
### labelNameSet
#### {'Moroccan', 'Indian', 'Italian', 'Thai', 'English', 'French', 'Greek', 'Mexican', 'Spanish', 'Chinese', 'German', 'Japanese'}
### ingredients
#### 太多了列不出来，总之就是一个个食材
## 第一次会议
### 可能的task
#### 根据食材预测菜系
### 我们也都看了数据，大部分能理解，suggested testbed
### 建议回去看一下lab
#### 看看有什么函数和方法
### 探索性数据分析
#### 描述数据是什么，文字描述，描述数据表示
#### 每个菜系有多少种不同的食谱
### 国家距离
#### 用某种方式表示为特征
### yunbo，试一下拟合数据，根据食材预测菜系
###
## report
### Introduction
### Data preparation
#### 可能有问题的数据要清理掉
### Exploratory data analysis
#### 资料
##### https://www.jianshu.com/p/9325c9f88ee6
##### https://robinchao.github.io/simple-eda/
### Results
####
### Conclusions
####
