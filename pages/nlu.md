---
title: NLU
---

## #UoE
## My Lecture Notes
### Lecture 1 Introduction
#### Natural Language Understanding
##### input is natural language
##### output is structured information
#### Natural Language Generation
##### input is some form of non-linguistic data
##### Output: A natural language description of that data
#### Machine Translation
##### Both input and output are text that convey the same meaning, but written in a different language or style.
#### Objective
##### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210222235327.png)
#### Methods
##### **probabilistic models** parameterised by **deep learning architectures**
###### feed-forward neural networks
###### recurrent neural networks
###### transformers
###### convolutional networks
#### Why deep learning
##### universal function approximators
##### representation learning
##### multi-task learning
#### Ethical concerns
#### supervised, unsupervised, transfer learning
#### Second part of this course
##### Problems
###### morphological analysis
###### syntactic parsing
###### semantic parsing
##### applications
###### question answering
###### paraphrasing
###### summarization
###### data-to-text generation
###### sentiment analysis
### Lecture 2 Machine Translation
#### 略
#### Key points to remember
##### Very simple cues are very helpful in translation.
###### Pairs of words that occur consecutively in the target language(bigrams).
###### Pairs of source and target words that frequently occur together in translations.
##### Q for next time: how would you model these cues?
##### Q for all the time: what are the ways in which this can fail?
### Lecture 3 Machine translation with n-grams
#### words conditioned on some input
##### speech recognition: condition on speech signal
##### machine translation: condition on text in another language
##### text completion: condition on the first few words of a sentence optical
##### character recognition: condition on an image of text
##### image captioning: condition on an image
##### grammar checking: condition on surrounding words
#### model
##### V, vocabulary
##### P, probability distribution
######
$$
P: V^{*} \rightarrow \mathbb{R}_{+}
$$
##### $w$ a sequence of words
##### $|w|$, length
##### $w_i$ i-th word
##### joint distribution, conditional distribution
######
$$
\begin{aligned}
P\left(w_{1} \ldots w_{|w|}\right)=& P\left(w_{1}\right) \times \\
& P\left(w_{2} \mid w_{1}\right) \times \\
& \ldots \\
& P\left(w_{|w|} \mid w_{1}, \ldots, w_{|w|-1}\right) \\
& P\left(\langle\mathrm{STOP}\rangle \mid w_{1}, \ldots, w_{|w|}\right) \\
&=\prod_{i=1}^{|w|+1} P\left(w_{i} \mid w_{1}, \ldots, w_{|w|}\right)
\end{aligned}
$$
##### n-gram probabilities, MLE
##### sampling zeros or structural zeros
##### predict
######
$$
\hat{w}_{k+1}=\underset{w_{k+1}}{\operatorname{argmax}} P\left(w_{k+1} \mid w_{1} \ldots w_{k}\right)
$$
#### Conditional language models
##### 第一种尝试 one long sequence
######
$$
P(y x)=P\left(x_{1} \ldots x_{|x|} y_{1} \ldots y_{|y|}\right)
$$
###### Problem: the English sentence will usually be longer than n!
##### 第二种 pair
######
$$
P(y x)=P\left(x_{1} y_{1} \ldots x_{|x|} y_{|x|} y_{|x|+1} \cdots y_{|y|}\right)
$$
###### Problem 1: The sentences are not usually the **same length**!
###### Problem 2: English and Swedish **word orders** are different!
##### 关键点 model bigram **translation probabilities**
######
$$
\begin{aligned}
P(y, z \mid x)=& P(y \mid x, z) P(z \mid x) \\
=& P(|y|,|z| \mid x) \\
& \prod_{i=1}^{|y|} P\left(y_{i} \mid y_{1}, \ldots, y_{i-1}, x, z\right) \prod_{i=1}^{|z|} P\left(z_{i} \mid z_{1}, \ldots, z_{i-1}, x\right)
\end{aligned}
$$
##### full model
######
$$
P(|y| \mid x) \prod_{i=1}^{|y|} \underbrace{P\left(z_{i}\mid |x|\right)}_{\text {transition probability}} \underbrace{P\left(y_{i} \mid x_{z_{i}}\right)}_{\text {~~emission probability }}
$$
###### problem, z is a latent variable
###### solution by Maximum likelihood
#######
$$
\begin{aligned}
\hat{\theta} &=\arg \max _{\theta} P(\mathcal{D} \mid \theta) \\
&=\arg \max _{\theta} \prod_{x_{j}, y_{i} \in V^{2}} \theta_{x_{j} y_{i}}^{\mathbb{E}_{P(\mathcal{D} \mid \theta)}\left[\operatorname{Count}\left(x_{j} y_{i}\right)\right]}
\end{aligned}
$$
###### 用 EM 算法 (Expectation maximization) 求 $\theta$
##### Greedy search，每步求最优
##### Beam search，每步保存k个最优
#### Summary
##### n-gram models use a **Markov assumption** to model an infinite sample space with a finite set of parameters.
##### Machine translation is just **conditional language modelling**.
##### To effectively model translation with n-grams, we need additional **latent variables** to model word alignment
##### One way to estimate the parameters of latent variable models is with a generalisation of maximum likelihood estimation, called **expectation maximisation**.
### Lecture 4 Perceptrons
#### Simple Perceptrons
##### input function
######
$$
u(x)=w \cdot x+b
$$
##### Activation function
######
$$
y=f(u(x))=\left\{\begin{array}{ll}
1, & \text { if } u(x)>0 \\
0, & \text { otherwise }
\end{array}\right.
$$
##### Learning Rule
######
$$
\begin{array}{l}
w_{i} \leftarrow w_{i}+\Delta w_{i} \\
\Delta w_{i}=\eta(t-o) x_{i}
\end{array}
$$
###### learning rate
#######
$$0 < \eta \leq 1$$
#### Multilayer perceptrons
##### universal function approximator
### Lecture 5 n-gram language modelling with feedforward neural networks
#### One-hot encoding
#### softmax
#### logistic regression
#### maximize likelihood
#### minimise error, cross-entropy loss
#### Gradient descent
##### gradient descent with momentum
##### individual learning rates for each dimension
##### adaptive learning rates
##### decoupling step length from partial derivates
#### n-grams with a multilayer neural network
:PROPERTIES:
:id: 6033f4e0-afdc-4f7b-8097-f76d3ee3dd20
:END:
##### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210222181532.png){:height 189, :width 286}
#####
$$
\begin{aligned}
P\left(w_{i} \mid w_{i-3}, w_{i-2}, w_{i-1}\right) &=\operatorname{softmax}\left(\mathrm{Vh}_{2}+\mathrm{b}_{2}\right) \\
\mathrm{h}_{2} &=\tanh \left(\mathrm{Wh}_{1}+\mathrm{b}_{1}\right) \\
\mathrm{h}_{1} &=\mathrm{Cw}_{i-3} ; \mathrm{Cw}_{i-2} ; \mathrm{Cw}_{i-1} \\
\mathrm{w}_{i} &=\text { onehot }\left(w_{i}\right)
\end{aligned}
$$
##### Each hidden layer is a **representation** of its input.
##### Multiplying one-hot by C selects a row of C (a vector).
##### We call i-th row of C the **embedding** of i-th word in V.
##### Learned **word embeddings** replace hand-engineered features of logistic regression.
#### feedforward neural networks
##### 1. Send an input pattern, x, from the training set.
##### 2. Get the output y.
##### 3. Compare y with the "right answer", or target t, to get the error quantity.
##### 4. Use the error quantity to modify the weights, so next time y will be closer to t.
##### 5. Repeat with another x from the training set.
#### SGD
### Lecture 6 Recurrent Neural Networks and LSTMs
#### Recurrent networks for language modelling
##### RNN Architecture
:PROPERTIES:
:id: 60341335-7dab-4af4-8418-3f90ce1af87a
:END:
###### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210222202413.png){:height 249, :width 352}
######
$$
\begin{aligned}
P\left(x_{i+1} \mid x_{1}, \ldots, x_{i-1}\right) &=\mathbf{y}_{i} \\
\mathbf{y}_{i} &=\operatorname{softmax}\left(\mathbf{W h}_{i}+\mathbf{b}_{2}\right) \\
\mathbf{h}_{i} &=\sigma\left(\mathbf{V} \mathbf{x}_{i}+\mathbf{U h}_{i-1}+\mathbf{b}_{1}\right) \\
\mathbf{x}_{i} &=\text { onehot }\left(x_{i}\right)
\end{aligned}
$$
##### no Markov assumption
##### Training
###### Use stochastic gradient descent, with cross-entropy.
###### dynanmic
##### Backpropagation
######
$$
\Delta w_{k j}=\eta \sum_{p}^{n} \delta_{p k} s_{p j} \quad \delta_{p k}=\left(d_{p k}-y_{p k}\right) g^{\prime}\left(n e t_{p k}\right)
$$
######
$$
\Delta v_{j i}=\eta \sum_{p}^{n} \delta_{p j} x_{p i} \quad \delta_{p j}=\sum_{k}^{0} \delta_{p k} w_{k j} f^{\prime}\left(n e t_{p j}\right)
$$
######
$$
\Delta u_{j i}=\eta \sum_{p}^{n} \delta_{p j}(t) s_{p h}(t-1) \quad \delta_{p j}(t)=\sum_{k}^{0} \delta_{p k} w_{k j} f^{\prime}\left(n e t_{p j}\right)
$$
######
$$
\delta_{p j}(t-1)=\sum_{h}^{m} \delta_{p h}(t) u_{h j} f^{\prime}\left(s_{p j}(t-1)\right)
$$
###### time steps $\tau$
###### truncated backpropagation through time
###### 梯度消失
#### LSTM Long short-term memory
##### architecture
###### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210223005222.png)
###### O: open gate
###### --: closed gate
###### black: high activation
###### white: low activation
##### memory blocks
###### trainable
###### Input gate: controls whether the input to is passed on to the memory cell or ignored;
###### Output gate: controls whether the current activation vector of the memory cell is passed on to the output layer or not;
###### Forget gate: controls whether the activation vector of the memory
 cell is reset to zero or maintained;
###### Memory cell: stores the current activation vector; with recurrent
connection to itself controlled by forget gate.
####### linear
####### no vanishing gradient
###### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210223005606.png){:height 239, :width 299}
##### relaxes vanishing gradient problem ( somewhat ) using gates.
### Lecture 7 Sequence-to-sequence models with attention
#### Encoding and decoding sequences
##### use RNN
##### problem
###### Word order is different
###### Different number of words
##### two RNNs as encoder and decoder
###### Encoder-Decoder Architecture
:PROPERTIES:
:id: 603454d6-c59f-4b54-b1c0-ae31e4fa5334
:END:
####### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210223010554.png){:height 262, :width 352}
###### Encoder:
#######
$$
\mathbf{h}_{i}=\operatorname{RNN}_{\text {enc }}\left(\mathbf{x}_{i}, \mathbf{h}_{i-1}\right)
$$
###### Decoder:
#######
$$
\begin{aligned}
\mathbf{s}_{i} &=\operatorname{RNN}_{\mathrm{dec}}\left(\mathbf{y}_{i}, \mathbf{s}_{i-1}\right) \\
P\left(y_{i} \mid y_{1}, \ldots, y_{i-1}, x_{1}, \ldots, x_{|x|}\right) &=\operatorname{softmax}\left(\mathbf{W} \operatorname{concat}\left(\mathbf{s}_{i}, \mathbf{h}_{|x|}\right)+\mathbf{b}\right)
\end{aligned}
$$
###### context, $\mathbf{h}_{|x|}$
###### problem
####### fixed size
####### recency bias
#### Attention
:PROPERTIES:
:id: 603455ce-8391-481e-b4a6-cf0964921958
:END:
##### Encoder-Decoder with Attention
:PROPERTIES:
:id: 603455d7-87c7-41fd-bf79-d67a62f06cb0
:END:
###### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210222103358.png){:height 328, :width 360}
##### 计算公式
######
$$
\begin{aligned}
P\left(y_{i} \mid y_{1}, \ldots, y_{i-1}, x_{1}, \ldots, x_{|x|}\right) &=\operatorname{softmax}\left(W \operatorname{concat}\left(s_{i}, c_{i}\right)+b\right) \\
c_{i} &=\sum_{j=1}^{|x|} \alpha_{i j} h_{j}
\end{aligned}
$$
##### output hidden state, the **query**; input vector, the **keys**
##### dot product attention
######
$$
\begin{array}{l}
a_{i j}=s_{i} \cdot h_{j} \\
\alpha_{i}=\operatorname{softmax}\left(a_{i}\right)
\end{array}
$$
###### 点乘，两个向量越接近，结果越大，所以可以表示相似的权重
##### 还有其他方法计算相似度
###### bilinear model
#######
$$
\begin{array}{l}
a_{i, j}=\mathbf{s}_{i} \mathbf{V} \mathbf{h}_{j}
\end{array}
$$
###### FNN
#######
$$a_{i, j}=\operatorname{FFN}\left(\mathbf{s}_{i}, \mathbf{h}_{j}\right)$$
#### bidirectional RNN
### Lecture 8 Evaluating Machine Translation Systems
#### good translation
##### Adequacy:
###### Does the output convey the same meaning as the input sentence? Is part of the message lost, added, or distorted?
##### Fluency:
###### Is the output good fluent English? Is is grammatically correct? Does it use appropriate words and idioms?
#### human evaluation
#####
$$
\kappa=\frac{p(A)-p(E)}{1-p(E)}
$$
##### $p(A)$ is proportion of times that evaluators agree.
##### $p(E)$ is proportion of times that they would agree by chance.
#### BLEU
#####
$$
\mathrm{BLEU}=\min \left(1, \frac{\text { output length }}{\text { reference length }}\right)\left(\prod_{n=1}^{4} \text { precision }_{i}\right)^{\frac{1}{4}}
$$
##### Not all words are equally important! BLEU treats determiners and punctuation the same as names and other content words.
##### BLEU is a poor proxy for both adequacy and fluency
##### BLEU isn't interpretable across datasets.
##### BLEU often scores human translation low.
### Lecture 9 Open-Vocabulary Models
#### 之前提到的模型都需要一个固定的vocabulary size
#### 问题是
##### many training corpora contain millions of word types
##### productive word formation processes (compounding; derivation)
 allow formation and understanding of unseen words
##### names, numbers are morphologically simple, but open word
classes
#### Open-vocabulary models
##### Non-Solution: Ignore Rare Words
###### replace out-of-vocabulary words with UNK
###### 50 000 words covers 95% of text
###### 但很稀少的词往往有极其独特的含义，所以很重要
##### Solution 1: Approximative Softmax
###### [Jean et al., 2015]
###### compute softmax over ”active” subset of vocabulary
###### limitations
####### allows larger vocabulary, but still not open
####### network may not learn good representation of rare words
##### Solution 2: Back-off Models
###### replace rare words with UNK at training time
###### when system produces UNK, align UNK to source word, and translate this with back-off method
###### 结果就挺离谱的
###### 限制
####### compounds: hard to model 1-to-many relationships
####### morphology: hard to predict inflection with back-off dictionary
####### names: if alphabets differ, we need transliteration
####### alignment: attention model unreliable
##### Solution 3: Subword NMT
###### Byte pair encoding (BPE)
####### open-vocabulary: operations learned on training set can be applied to unknown words
####### compression of frequent character sequences improves
 efficiency → trade-off between text length and vocabulary size
##### Solution 4: Character-level NMT
###### advantages:
####### (mostly) open-vocabulary
####### no heuristic or language-specific segmentation
####### neural network can conceivably learn from raw character sequences
###### drawbacks:
####### increasing sequence length slows training/decoding (reported x2-x8 increase in training time)
###### open questions
####### on which level should we represent meaning?
####### on which level should attention operate?
###### hierarchical model: back-off revisited
####### word-level model produces UNKs
####### for each UNK, character-level model predicts word based on word hidden state
### Lecture 10 Transformer
#### 复习
##### {{embed ((603454d6-c59f-4b54-b1c0-ae31e4fa5334))}}
##### {{embed ((603455ce-8391-481e-b4a6-cf0964921958))}}
#### self-attention
##### input $$\boldsymbol{x}_{1}, \ldots, \boldsymbol{x}_{t}$$
##### output $$\boldsymbol{y}_{1}, \ldots, \boldsymbol{y}_{t}$$
#####
$$
\mathrm{y}_{i}=\sum_{j} w_{i j} \mathrm{x}_{j}
$$
##### $w_{ij}$ is the attention, computed as the dot-product of each input token with every other token
######
$$
\begin{array}{r}
w_{i j}^{\prime}=x_{i} \cdot x_{j} \\
w_{i}=\operatorname{softmax}\left(w_{i}^{\prime}\right)
\end{array}
$$
###### 注意力权重 $w_{ij}'$
###### 注意力分布 $w_i$
##### Architecture
###### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210222105758.png){:height 416, :width 554}
###### 和前一个结构相比，x之间的连接没有了
##### 缺点  The input is a position invariant, i.e., we have no way to represent word order (unlike in an RNN).
##### Query
###### compare $x_i$ to every other vector to compute attention weights for its own output $y_i$
##### Key
###### compare $x_i$ to every other vector to compute attention weights for its other output $y_j$
##### Value
###### use $x_i$ in the weighted sum to compute every output vector based on these weights.
#####
$$
\begin{array}{rl}
\mathrm{q}_{i}=W_{q} x_{i} & \mathrm{k}_{i}=W_{k} \mathrm{x}_{i} \quad \mathrm{v}_{i}=W_{v} \mathrm{x}_{i} \\
w_{i j}^{\prime} & =\mathrm{q}_{i} \cdot \mathrm{k}_{j} \\
\mathrm{w}_{i} & =\operatorname{softmax}\left(\mathrm{w}_{i}^{\prime}\right) \\
\mathrm{y}_{i} & =\sum_{j} w_{i j} \mathrm{v}_{j}
\end{array}
$$
##### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210222175350.png){:height 294, :width 342}
#### Multi-Head attention
##### 相当于多几个上面的模型输出给加权一下
#####
$$W^r_q, W^r_k, W^r_v$$
##### Narrow self-attention: cut the input into chunks of size k/h (h: number of heads), use weight matrices of size k/h x k/h.
##### Wide self-attention: use weight matrices that cover the whole input for each head, i.e., of size k x k.
#### Transformer
##### Architecture of Transformer Block
###### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210222180317.png)
###### blue connections are residual connections
####### They prevent the gradients from getting to large or small.
###### Layer normalisation makes training faster.
###### The feedforward layer applies a single MLP independently to
 each input vector.
##### A bigger architecture
###### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210222180646.png)
###### Attention is position invariant
###### Position Encodings
#######
$$
f: \mathbb{N} \rightarrow \mathbb{R}^{k}
$$
####### Vaswani et al. ( 2017 )
########
$$
\begin{aligned}
P E_{(p o s, 2 i)} &=\sin \left(\operatorname{pos} / 10000^{2 i / k}\right) \\
P E_{(p o s, 2 i+1)} &=\cos \left(p o s / 10000^{2 i / k}\right)
\end{aligned}
$$
######## 所以在i=2的the和i=7的the会有一些些不一样
#### 剩余部分在Lecture 12讲
### Lecture 11 Word Embeddings
#### Recall Lecture 5, n-gram probabilities:
##### {{embed ((((6033f4e0-afdc-4f7b-8097-f76d3ee3dd20))))}}
##### C 和 word embedding 最相关
#### Recall Lecture 6, RNN
##### drop Markov assumption
##### {{embed ((60341335-7dab-4af4-8418-3f90ce1af87a)) }}
#### 引入
##### 隐藏层是其输入的表示
##### one-hot encoding是一种 word embedding
##### 和迁移学习的关系？
#### Pre-training and Finetuning
##### Feature Extraction
###### VGG-16
####### architecture
######## ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210222203652.png){:height 324, :width 509}
####### take the output of the last layer (here: fc8) as a feature vector.
##### **Pre-training**: train a generic source model (e.g., VGG-16) on a standard, large dataset (e.g., ImageNet).
##### **Fine-tuning**: then take the resulting model, keep its parameters, and replace the output layer to suit the new task. Now train this target model on the dataset for the new task.
###### Transfer learning by ﬁne-tuning.
###### truncate the last layer
##### **weight freezing**: only finetune a handful of final layers, you keep the other ones fixed
###### Finetuning without weight freezing is normally too slow.
##### **source model** is the neural language model (NLM)
##### **target model** is often ver y diﬀerent from the NLM
##### **target model** is often ver y diﬀerent from the NLM
##### word embeddings as the input representations for a new task, then we're doing feature extraction.
#### Word Embeddings
##### word embeddings as the input representations for a new task, then we're doing feature extraction.
##### contextualised word embeddings
###### 原来每个单词自己编码成向量，比如word2vec
###### 上下文词嵌入则是先过一层，把获得单词上下文，再对每个单词输出一个向量
##### Overview
###### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210222205625.png)
###### Fast Text挺好的
###### 之后会细讲Elmo，GPT，BERT
###### Static Word Embeddings
####### fixed vector to each word
####### used for feature extration
####### not designd for fine-tuning，但是也能用
###### Contextualised (or Dynamic) Word Embeddings
####### a vector to a word that depends on its context
####### Static Word Embeddings
######## fixed vector to each word
######## used for feature extration
######## not designd for fine-tuning，但是也能用
##### Static Word Embeddings
###### Word2Vec
####### architecture
######## ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210222210337.png){:height 324, :width 253}
####### Has only a single, linear hidden layer.
###### Word2Vec: Skipgram
####### architecture
######## ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210222210620.png){:height 320, :width 234}
####### uses the current word to predict the context words.
####### Levy and Goldberg ( 2014 )
####### word $w \in W$, vector $v_w \in \mathbb{R}^d$
####### context $c \in C$, vector $v_c \in \mathbb{R}^d$
####### $W$ word vocabulary, $C$ context vocabulary, $d$ embedding dimensionality
####### Vector components are **latent** ( parameters to be learned )
####### 目标函数
########
$$\underset{\theta}{\operatorname{argmax}} \prod_{(w, c) \in D} p(c \mid w ; \theta)$$
####### basic skipgram formulation
########
$$
p(c \mid w ; \theta)=\frac{\exp \left(v_{c} \cdot v_{w}\right)}{\sum_{c^{\prime} \in C} \exp \left(v_{c^{\prime}} \cdot v_{w}\right)}
$$
######## 但分母没办法计算
####### Traning，略
###### Contextualised (or Dynamic) Word Embeddings
####### a vector to a word that depends on its context
##### Contextualised (or Dynamic) Word Embeddings
######## 但分母没办法计算，解决办法是Negative Sampling
####### Negative Sampling
### Lecture 12 Contextualised Word Embeddings
#### 复习
##### In lecture 10, we saw how we can stack transformers and use them for **classification**. We apply mean pooling to the output and map it onto a class vector.
##### We can also use transformers for **sequence prediction**. For this we need to mask some of the input.
##### In lecture 11, we saw how we can derive **embeddings** from neural language models.
##### Transformers are language model that can represent context
 very well: they can learn **contextualized embeddings**.
##### Contextualized language models can be used for feature
 extraction, but also in a **pre-training/finetuning** setup.
#### Bert ( Bidirectional Encoder Representations from Transformers ) :
##### Basic Bert Architecture
###### multi-layer bidirectional transformer (Vaswani et al. 2017); L: layers (transformer blocks); H: dimensionality of hidden
 layer, A: number of self-attention heads;
###### GPT 单向
###### ELMo 不为fine tuning设计
###### BERT 双向，fine tuning
6, 340M parameters.
###### Ber
###### multi-layer bidirectional transformer (Vaswani et al. 2017);
###### L: layers (transformer blocks);
###### H: dimensionality of hidden layer,
###### A: number of self-attention heads;
##### Input sequence: can be (Question, Answer) pair, single sentence, or any other string of tokens;
##### use WordPiece to do word embedding (token embedding), 30000 vocabulary
##### [CL^^^^S], [SEP]
##### plug Segment Embeddings and Position Embeddings
#### Masked Training
##### 因为输入输出一样，可能网络什么都没学到，所以需要masking
##### Solution: 随机 mask 15% of the tokens in the input sequence; train the model to predict these.
##### 在fine tuning的时候，没有[MASK]
###### 1. the [MASK] token 80% of the time;
###### 2. a random token 10% of the time;
###### 3. the unchanged i-th token 10% of the time.
###### 原因
####### if we always use [MASK] token, the model would not have to learn good representation for other words;
####### if we only use [MASK] token or random word, model would learn that observed word is never correct;
####### if we only use [MASK] token or observed word, model would just learn to trivially copy
##### Secondary Task: Next Sentence Prediction
###### generate training data: chose two sentences A and B, such that 50% of the time B is the actual next sentence of A, and 50% of the time a randomly selected sentence.
#### Pre-training and Finetuning Bert
##### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210222231336.png)
### Lecture 13 Ethics in NLP
:PROPERTIES:
:id: 60350bda-eb15-442e-8c85-04fdb69a9ab4
:END:
#### 语言真正相关的是人，而不是单词
#### 这节课主要关于NLP的社会影响
#### The social impact of NLP
##### benefits
###### Efficiency
####### for individuals and institutions trying to understand and summarize information in many languages
###### Personalization
####### for users, e.g. through digital assistants, tutoring agents, and other services.
###### Human understanding
####### of the language faculty and its social use-e.g. through use in computational psycholinguistics and computational sociolinguistics.
##### **How can my system harm people?**
##### Who is aﬀected
###### language data
##### 阿拉伯例子
##### possible harms
###### Harms to **fairness and justice**: different populations have different levels of access to benefits, and are subject to different degrees of harm
###### Note: Our goal is not to balance benefits and harm! We want to have as much benefit as possible, with as few harms as possible. When benefits accrue mostly to the powerful, and harms happen mainly to the powerless, this increases social inequity.
###### Harms to **privacy and security**: data aggregation and inference can lead to many types of harm to individuals
###### Harms to **transparency and autonomy**: Deep learning systems cannot explain outcomes, and individuals may not be able to challenge outcomes that harm them.
###### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210223144701.png)
#####
### Lecture 14 Word Embeddings are Biased
:PROPERTIES:
:id: 6035493a-910e-432e-bb80-4973bfde4149
:END:
#### Bias in representations
#### IAT Implicit-association test
#### IAT for word embeddings

###### 计算group和stereotype的相似度

##### Sanity check 可行性检查

###### 先试试计算“花和虫”（group），“幸福和不满”（stereotype）

###### 果然花和幸福，虫和不满，强相关

##### 正式实验

###### 欧洲人名和非洲人名，舒服和不满。结果欧洲人名和舒服相关，非洲人名和不满相关

###### 男人和事业相关，女人和家庭相关
###### 其他略
##### word2vec embedding
###### he 和 职业
###### she 和 职业
###### she-he
####### 定义上，queen-king，等
####### 刻板印象，lovely-brilliant，等
##### Job descriptions in 20th century (American) texts
###### 相似的工作 分别和 西班牙裔，亚裔，白人
##### 性别和形容词联系，随时间的变化
###### 1910，1950，1990
##### text和种族联系，随时间变化
#### Bias in NLP systems

##### Case study: **219 automatic sentiment analysis systems**, submitted to a shared task intended to measure **anger, fear, joy, sadness**.

###### 生成数据  (PERSON) made me feel (EMOTIONAL STATE WoRD).

####### 比如 Ebony made me feel angry .

###### 结论包括 Most systems associated European-American names more strongly with joy 等

#### What can you do?

##### gender subspace

##### Debiasing

###### 利用一部分词之间embed的关系（she-he）来去除其他词的bias

###### 好像没啥用

##### traps

###### The Framing Trap

####### Data is constrained by access and opportunity, and not all factors are captured in the data frame.

###### The Portability Trap

####### Algorithmic solutions designed for one social context may be misleading, inaccurate, or otherwise harmful in different contexts.

###### The Formalism Trap

####### Social concepts such as fairness-which can be procedural, contextual, and contestable-cannot be resolved mathematically.

###### The Ripple Effect Trap

####### Adding tech to existing social systems changes the behaviours and embedded values of existing systems.

###### The Solutionism Trap

####### The best solution to a problem may not involve technology.

##### Ask questions of your data

###### Why was the dataset created?

###### Who funded the creation of the dataset?

###### What preprocessing or cleaning was done?

###### If it relates to people, were they told what the dataset would

 be usef for, and did they consent?

###### Will the dataset be updated?

#### Summary 考点

##### Word embeddings are a basic technology used in many NLP technologies; they are freely available and used by many developers large and small.

##### Word embeddings empirically exhibit many cultural stereotypes and biases, with strong statistical effects: technology will reflect and can potentially amplify these biases.

##### Who benefits? Who is harmed?

##### Bias and unfairness is a deep sociotechnical problem. We do not know how to solve it with maths, and it's unlikely that we will.

##### Be critical of your data. Does it fit your purpose?

##### When building systems you need to consider social anc historical context, and involve people who will be affected.
### Lecture 15 The Environmental and Human Cost of NLP
:PROPERTIES:
:id: 60355745-fe08-426b-9e3b-10e2ae2a6e10
:END:
#### Anatomy of an Al system 解剖
##### smart speaker
#### Carbon and the Climate Crisis
##### 排放
##### 碳含量
##### 海洋气温
#### The Carbon Cost of Al
##### kinds of costs
###### 开发成本 Costs to progress
####### Research and development of new NLP models multiplies these costs by thousands, due to experimentation with model architectures, parameters, and different datasets.
###### 访问成本（模型运行在昂贵的硬件上）Costs to access
####### Many models require access to specialized hardware (many GPUs or TPUs) limiting access to the richest (Who benefits from this? How does it affect existing power imbalances?)
###### 环境成本 Costs to the environment
####### Computation requires energy, and not all of this energy is carbon-neutral. Where it is. training NLP may not be the best allocation of that energy
##### Estimating the carbon cost of a model
###### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210223195330.png)
#### 总结
##### 训练时间和超参数选择增加了碳排放，而这在SOTA中很常见
##### 对计算资源的掌控导致强者愈强
##### 效率高的算法降低了碳排放，但是 rebound eﬀect 导致更高消耗
###### 便宜的东西，用的人更多
##### 使用已有的模型（预训练）更环保
##### deep adaptation
###### resilience 复原
###### relinquishment 放弃
###### restoration 恢复
### Lecture 16 Neural Parsing
:PROPERTIES:
:id: 60355745-cbce-4ca6-b644-c7a9a672b14d
:END:
#### 复习
##### ((603454d6-c59f-4b54-b1c0-ae31e4fa5334))
##### 输入输出都是符号序列
#### Reading: Vinyals et al. ( 2015 )
#### Neural Parsing
##### Parsing is the task of turning a sequence of words into a syntax tree:
###### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210223200644.png)
##### 这里的输出是树
##### 可以 **linearize**
###### (S (NP (Pro You)) (VP (V saw ) (NP (Det a) (N man ) (PP (P with) (Det a) (N telescope))))).
##### 删掉单词，化简
###### (S (NP Pro) (VP V (NP Det N (PP P Det N))))
##### 标记右括号
###### $(S ~(NP ~Pro)_{NP} (VP~ V (NP~ Det~ N (PP ~P~ Det~ N)_{PP} )_{NP} )_{VP} )_{S}$
##### An Encoder-Decoder for Parsing
###### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210223201250.png){:height 409, :width 557}
##### 增加性能的方法
###### EOS (end of sequence)
###### 反转输入
###### 更深的网络
###### 加注意力
###### 用预训练词嵌入模型
###### ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210223201534.png)
#### Potential Problems
#### Results
#### Parsing with Transformers
