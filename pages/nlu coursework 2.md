---
title: NLU Coursework 2
---

## 描述
### part 1 补comment，跑baseline
#### question 1 补注释，跑baseline
#### question 2 5个问题，用linux命令
### part 2 扩展baseline
#### Question 3 3个思考问题
#### Question 4 增加层数（命令行），重新训练，分析结果
### part 3 lexical attention model，写代码
#### Question 5 Lexical Model 看论文，实现，重新训练，小数据集调试，分析结果
### part 4 Transformer，add the Multi-Head attention code
#### Question 6 补注释
#### Question 7 实现Multi-Head Attention 重新训练，分析结果
### submission，document，files，不包含个人信息
#### <UUN>.pdf
#### <UUN>.zip
##### lstm.py, train.py, transformer.py and transformer_helper.py
## 队友
### s2068339@ed.ac.uk
## 进度
### question 1 模型跑了一遍，忘记记录时间，估计一两个小时
### 新建overleaf项目
### 申请延期
### q1A
#### [五）通俗易懂理解——BiLSTM](https://zhuanlan.zhihu.com/p/40119926)
### q1D
#### [Incremental Decoding during Inference](https://www.telesens.co/2019/04/21/understanding-incremental-decoding-in-fairseq/#Incremental_Decoding_during_Inference)
#### [Incremental decoding](https://fairseq.readthedocs.io/en/latest/models.html?highlight=incremental#incremental-decoding)
#### [teacher forcing](https://zhuanlan.zhihu.com/p/93030328)
#### [TensorFlow教程翻译 | Neural Machine Translation(seq2seq) Tutorial](https://zhuanlan.zhihu.com/p/33319933)
#### [seq2seq 中的 beam search 算法过程是怎样的](https://www.zhihu.com/question/54356960/answer/138990060)
### q7 implementation
### q7 debug
### mask
#### [Transformer & Self-Attention (多头) 自注意力编码](https://congchan.github.io/NLP-attention-03-self-attention/)
##### 需要有一个 mask 来防止当前位置 i 的生成任务看到后续 > i 位置的信息
#### [transformer中自注意力和多头注意力的pytorch实现](https://www.cnblogs.com/xiximayou/p/13343856.html)
#### [多头注意力机制（Multi-head Attention）及其在PyTorch中的使用方法分析](https://blog.csdn.net/HappyCtest/article/details/109847449)
##### mask掉序列中pad的位置
##### 限制attention中每个位置能看到的内容
### [Transformer模型的PyTorch实现](https://luozhouyang.github.io/transformer/)
#### 这篇内容很全
### q7实现完成，感谢冷文翔同学
### q7可能需要dropout，layer normalization等
### 先q5
#### Improving Lexical Choice in Neural Machine Translation
#### tgt_inputs
##### b，t
#### src_embeddings = encoder_out['src_embeddings']
##### t，b，e
#### tgt_embeddings
##### [tgt_time_steps, batch_size, num_features]
#### attn_weights
##### batch_size, tgt_time_steps, src_time_steps
#### src_embeddings
##### [src_time_steps, batch_size, output_dims]
#### weighted_avg_embeddings
##### batch_size, output_dims
#### decoder_output
