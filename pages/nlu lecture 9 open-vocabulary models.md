---
title: NLU Lecture 9 Open-Vocabulary Models
---

	- 之前提到的模型都需要一个固定的vocabulary size
	- 问题是
		- many training corpora contain millions of word types
		- productive word formation processes (compounding; derivation)
		   allow formation and understanding of unseen words
		- names, numbers are morphologically simple, but open word
		  classes
	- Open-vocabulary models
		- Non-Solution: Ignore Rare Words
			- replace out-of-vocabulary words with UNK
			- 50 000 words covers 95% of text
			- 但很稀少的词往往有极其独特的含义，所以很重要
		- Solution 1: Approximative Softmax
			- [Jean et al., 2015]
			- compute softmax over ”active” subset of vocabulary
			- limitations
				- allows larger vocabulary, but still not open
				- network may not learn good representation of rare words
		- Solution 2: Back-off Models
			- replace rare words with UNK at training time
			- when system produces UNK, align UNK to source word, and translate this with back-off method
			- 结果就挺离谱的
			- 限制
				- compounds: hard to model 1-to-many relationships
				- morphology: hard to predict inflection with back-off dictionary
				- names: if alphabets differ, we need transliteration
				- alignment: attention model unreliable
		- Solution 3: Subword NMT
			- Byte pair encoding (BPE)
				- open-vocabulary: operations learned on training set can be applied to unknown words
				- compression of frequent character sequences improves
				   efficiency → trade-off between text length and vocabulary size
		- Solution 4: Character-level NMT
			- advantages:
				- (mostly) open-vocabulary
				- no heuristic or language-specific segmentation
				- neural network can conceivably learn from raw character sequences
			- drawbacks:
				- increasing sequence length slows training/decoding (reported x2-x8 increase in training time)
			- open questions
				- on which level should we represent meaning?
				- on which level should attention operate?
			- hierarchical model: back-off revisited
				- word-level model produces UNKs
				- for each UNK, character-level model predicts word based on word hidden state