---
title: MLP评估方法收集统计
---

##
### [[FTGAN Chen 2019]]
#### FID
#### FSD
#### FSS
### [[AttnGAN Xu 2018]]
#### IS
#### R-precision
### [[Faces la Carte Wang 2020]]
#### IS
#### Learned Perceptual Image Patch Similarity (LPIPS)
##### which is for evaluating the diversity of the generated images
#### CS
##### cosine similarity
##### which is widely used to evaluate the similarity of two chunks of a corpus in natural language processing.
### [[MSG-GAN Karnewar 2020]]
#### FID
#### MSE
##### Mean Square Error
#### IS
### [[StackGAN Zhang 2017]]
#### IS
#### Human rank
### [[StackGANplusplus Zhang 2018]]
#### IS
#### Human rank
#### FID
### [[Dualattn-GAN Cai 2019]]
#### IS
#### FID
#### Human Rank
### [[Text-SeGAN Cha 2019]]
#### IS
### [[MS-GAN Mao 2019]]
#### IS
#### FID
#### PSS
##### Perceptual Similarity Score （这个也是由真人对比）
### [[HfGAN Huang 2019]]
#### IS
#### VS similarity
##### pre-trained visual-semantic embedding models for three datasets provided by [[HDGAN Zhang 2018]].
### [[HDGAN Zhang 2018]]
#### IS
#### MS-SSIM
##### Multi-scale structural similarity
##### T. Salimans, I. Goodfellow, W. Zaremba, V. Cheung, A. Radford, X. Chen, and X. Chen. Improved techniques for training gans. In NIPS. 2016.
##### It tests pair-wise similarity of generated images and can identity mode collapses reliably
###### A. Odena, C. Olah, and J. Shlens. Conditional image synthesis with auxiliary classiﬁer gans. arXiv preprint arXiv:1610.09585, 2016.
##### Lower score indicates higher diversity of generated images
#### VS similarity
### Semantic Object Accuracy for Generative Text-to-Image Synthesis
#### IS
#### FID
#### VS similarity
#### R-presicion
#### CAS
##### Classification Accuracy Score
#### Caption Generation
#### Semantic Object Accuracy (SOA)
### A Realistic Image Generation of Face From Text Description Using the Fully Trained Generative Adversarial Networks
#### FSD
##### face semantic distance
#### FID
#### PNSR
##### Peak Noise to Signal Ratio
#### Human Assessment
### [[MirrorGAN Qiao 2019]]
#### IS
#### R-precision
### [[DM-GAN Zhu 2019]]
#### IS
#### FID
#### R-precision
### Semantic Image Synthesis via Adversarial Learning
#### Human
### [[Obj-GANs Li 2019]]
#### IS
#### FID
#### R-precision
### [[rdAttnGAN Tian 2020]]