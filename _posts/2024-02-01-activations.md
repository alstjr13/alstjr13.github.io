---
layout: single
title: "[Deep Learning] Activation Functions"
categories: ['ML & DL']
tag: [Data, ['Machine Learning'], ['Deep Learning'], ['Neural Network']]
toc: true
---

#### Rectified Linear Unit (ReLU)

$$RELU(x) = \begin{cases} x, & \text{if } x > 0, \\ 0, & \text{if } x \leq 0 \end{cases}$$

<img src="/assets/files/pictures/relu.png" width="30%" height="30%" style="border:none;">

#### Exponential Linear Unit (ELU)

$$ELU(x) = \begin{cases} x, & \text{if } x > 0, \\ \alpha (e^x - 1), & \text{if } x \leq 0 \end{cases}$$

<img src="/assets/files/pictures/elu.png" width="30%" height="30%" style="border:none;">

#### Scaled Exponential Linear Unit (SELU)

$$SELU(x) = \lambda{} \begin{cases} x, & \text{if } x > 0, \\ \alpha (e^x - 1), & \text{if } x \leq 0 \end{cases}$$

<img src="/assets/files/pictures/selu.png" width="30%" height="30%" style="border:none;">

#### Sigmoid Linear Unit (SiLU)

$$silu(x) = x * \sigma{(x)} \text{      where   } \sigma{(x)} \text{      is the logistic sigmoid}$$

<img src="/assets/files/pictures/swish.png" width="30%" height="30%" style="border:none;">