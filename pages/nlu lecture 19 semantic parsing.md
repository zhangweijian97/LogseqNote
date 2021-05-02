---
title: NLU Lecture 19 Semantic Parsing
---

## Motivation
### Example
#### sentence-logical form
##### Question
###### Who are the male actors in Titanic?
##### Logical Form
###### λx. ∃y. gender (MALE, x ) ∧ cast (TITANIC, x, y )
### Why the Task is Hard
#### Machine language is different from NL string and its syntactic representation.
#### 一（NL）对多（KB）
## Modeling
### Sequence-to-Sequence
### Coarse-to-Fine
