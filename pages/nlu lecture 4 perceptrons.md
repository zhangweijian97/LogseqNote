---
title: NLU Lecture 4 Perceptrons
---

	- Simple Perceptrons
		- input function
			-
			  $$
			  u(x)=w \cdot x+b
			  $$
		- Activation function
			-
			  $$
			  y=f(u(x))=\left\{\begin{array}{ll}
			  1, & \text { if } u(x)>0 \\
			  0, & \text { otherwise }
			  \end{array}\right.
			  $$
		- Learning Rule
			-
			  $$
			  \begin{array}{l}
			  w_{i} \leftarrow w_{i}+\Delta w_{i} \\
			  \Delta w_{i}=\eta(t-o) x_{i}
			  \end{array}
			  $$
			- learning rate
				-
				  $$0 < \eta \leq 1$$
	- Multilayer perceptrons
		- universal function approximator