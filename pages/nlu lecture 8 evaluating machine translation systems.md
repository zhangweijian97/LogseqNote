---
title: NLU Lecture 8 Evaluating Machine Translation Systems
---

	- good translation
		- Adequacy:
			- Does the output convey the same meaning as the input sentence? Is part of the message lost, added, or distorted?
		- Fluency:
			- Is the output good fluent English? Is is grammatically correct? Does it use appropriate words and idioms?
	- human evaluation
		-
		  $$
		  \kappa=\frac{p(A)-p(E)}{1-p(E)}
		  $$
		- $p(A)$ is proportion of times that evaluators agree.
		- $p(E)$ is proportion of times that they would agree by chance.
	- BLEU
		-
		  $$
		  \mathrm{BLEU}=\min \left(1, \frac{\text { output length }}{\text { reference length }}\right)\left(\prod_{n=1}^{4} \text { precision }_{i}\right)^{\frac{1}{4}}
		  $$
		- Not all words are equally important! BLEU treats determiners and punctuation the same as names and other content words.
		- BLEU is a poor proxy for both adequacy and fluency
		- BLEU isn't interpretable across datasets.
		- BLEU often scores human translation low.