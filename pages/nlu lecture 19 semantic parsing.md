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
#### 挑战
##### Machine language is different from NL string and its syntactic representation.
###### neural encoder-decoder architecture for mapping natural language expressions to their logical forms.
##### Well-formedness of Machine Language 格式严格
##### Linguistic Coverage，多（NL）对一
#### 解决
##### Structural Mismatches:
###### neural encoder-decoder architecture for mapping natural language expressions to their logical forms.
##### Well-formedness Constraints:
###### coarse-to-ﬁne decoding algorithm generates well-formed meaning representations.
##### Linguistic Coverage:
###### query paraphrasing framework handles variation of natural language input.
#### 其他挑战略
## Modeling
### Sequence-to-Sequence
### Coarse-to-Fine
