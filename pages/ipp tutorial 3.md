---
title: IPP Tutorial 3
---

## Tutor: Mohammad Tahaei
## **Introducing** your projects
### title
#### A Framework of Multi-view Knowledge Graph Embeddings
### short description
#### Knowledge Graph
##### Basic element: Triple, (entity, relation, entity), with attributes
###### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210221204209.png){:height 115, :width 349}
##### Graph
###### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210221202458.png)
#### Knowledge Graph Embedding
##### represents entities and relations as vectors
##### useful to machine learning models
##### for tasks, like Question & Answer, Recommendation System
##### Bordes et al., 2013
###### relation based model
###### $(\boldsymbol{h}, \boldsymbol{\mathscr{l}}, \boldsymbol{t})$
###### $\boldsymbol{h} + \boldsymbol{\mathscr{l}} \approx \boldsymbol{t}$
#### Sparsity Problem
##### graph incompleteness scenario
###### an entity does not have many (or any) relationships to other entities in the graph
##### missing data scenario
###### the entity is new and there is not much information about it yet, or the relevant information is corrupted/lost
##### relation-based approaches cannot produce adequate representations
#### Multi-view framework
##### combine information not only from **relations**, but also from **textual attributes**
### completion criteria
#### Implement and train a model that learns embedding from multiple sources.
##### for new entity, and entities with less relations
#### Test the model on a community dataset and report performance.
## {{embed [[Past IPP Example 5]] }}
## Activity 2: draft the **motivation** for your allocated projects
### problem
### time and novelty
### beneficiaries
## Discussion
###
