---
title: RL Chapter 5 Monte Carlo Methods
---

## 首次访问蒙特卡罗预测 first-visit Monte Carlo Prediction
### 图略
## 蒙特卡罗探索起点 Explore Start
### 图略
## on-policy
## off-policy
## π 是目标策略，b 是行为策略
## 重要性采样率和v
###
$$\rho_{t:T-1}=\prod^{T-1}_{k=t}\frac{\pi(A_k|S_k)}{b(A_k|S_k)}$$
###
$$\mathbb{E}[\rho_{t:T-1}G_t|S_t=s]=v_\pi(s)$$
### 对于off-policy，回报是在行为策略下产生的，所以用重要性采样率$\rho$乘上回报修正回去
### 修正后的回报的期望就是状态值v
## 计算期望的两个方法，普通重要性采样和加权重要性采样
### 普通重要性采样
####
$$V(s)=\frac{\sum_{v\in \mathcal{T}(s)}\rho_{t:T(t)-1}G_t}{|\mathcal{T}(s)|}$$
### 加权重要性采样
####
$$V(s)=\frac{\sum_{v\in \mathcal{T}(s)}\rho_{t:T(t)-1}G_t}{\sum_{v\in \mathcal{T}(s)}\rho_{t:T(t)-1}}$$
### 增量的加权重要性采样
#### 
$$V_{n+1}=V_n+\frac{W_n}{C_n}[G_n-V_n]$$
#### 
$$C_{n+1}=C_n+W_{n+1}$$
#### W是权重，可以是$W_i=\rho_{t_i:T(t_i)-1}$
## on-policy的增量计算v
###
$$V_n(S_t)=V_{n-1}(S_t)+\frac{1}{n}(G_n(t)-V_{n-1}(S_t))$$
## 预测，用来估计v。控制，用来估计pi
##
