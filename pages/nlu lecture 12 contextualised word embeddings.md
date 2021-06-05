---
title: NLU Lecture 12 Contextualised Word Embeddings
---

	- 复习
		- In lecture 10, we saw how we can stack transformers and use them for **classification**. We apply mean pooling to the output and map it onto a class vector.
		- We can also use transformers for **sequence prediction**. For this we need to mask some of the input.
		- In lecture 11, we saw how we can derive **embeddings** from neural language models.
		- Transformers are language model that can represent context
		   very well: they can learn **contextualized embeddings**.
		- Contextualized language models can be used for feature
		   extraction, but also in a **pre-training/finetuning** setup.
	- Bert ( Bidirectional Encoder Representations from Transformers ) :
		- Basic Bert Architecture
			- multi-layer bidirectional transformer (Vaswani et al. 2017); L: layers (transformer blocks); H: dimensionality of hidden
			   layer, A: number of self-attention heads;
			- GPT 单向
			- ELMo 不为fine tuning设计
			- BERT 双向，fine tuning
			  6, 340M parameters.
			- multi-layer bidirectional transformer (Vaswani et al. 2017);
			- L: layers (transformer blocks);
			- H: dimensionality of hidden layer,
			- A: number of self-attention heads;
		- Input sequence: can be (Question, Answer) pair, single sentence, or any other string of tokens;
		- use WordPiece to do word embedding (token embedding), 30000 vocabulary
		- [CLS], [SEP]
		- plug Segment Embeddings and Position Embeddings
	- Masked Training
		- 因为输入输出一样，可能网络什么都没学到，所以需要masking
		- Solution: 随机 mask 15% of the tokens in the input sequence; train the model to predict these.
		- 在fine tuning的时候，没有[MASK]
			- 1. the [MASK] token 80% of the time;
			- 2. a random token 10% of the time;
			- 3. the unchanged i-th token 10% of the time.
			- 原因
				- if we always use [MASK] token, the model would not have to learn good representation for other words;
				- if we only use [MASK] token or random word, model would learn that observed word is never correct;
				- if we only use [MASK] token or observed word, model would just learn to trivially copy
		- Secondary Task: Next Sentence Prediction
			- generate training data: chose two sentences A and B, such that 50% of the time B is the actual next sentence of A, and 50% of the time a randomly selected sentence.
	- Pre-training and Finetuning Bert
		- ![](https://gitee.com/zhang-weijian-97/pic-go-bed/raw/master/assets/20210222231336.png)