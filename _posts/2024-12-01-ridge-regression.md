---
layout: single
title: "Ridge Regression (Tikhonov Regularization)"
categories: ["Data Analysis"]
tag: [Data, Mathematics, ["Data Modelling"]]
toc: true
---

#### Also known as:
- L2 Regularization
- Tikhonov regularization

#### Introduction:
[Ridge regression](https://en.wikipedia.org/wiki/Ridge_regression#Tikhonov_regularization) is a variant of linear regression that includes an L2 regularization term to prevent overfitting.

#### Mathematic Equation:
Tikhonov regularization has the form:

$$Cost = min_{x}\frac{1}{2}||Ax - b||^{2} + \lambda\frac{1}{2}||Dx||^{2}$$

This objective can be expressed equivalently as:

$$||Ax - b||^{2} + \lambda||Dx||^{2} = ||\begin{bmatrix} A \\ \sqrt{\lambda}D \end{bmatrix}x - \begin{bmatrix} b \\ 0 \end{bmatrix}||^{2}$$

If D has full rank, then the stacked matrix $$\begin{bmatrix} A \\ \sqrt{\lambda}D \end{bmatrix}$$ neccessarily also has full rank for any positive $\lambda$, which implies that the regularized problem always has an unique solution.

#### Consider a noisy measurement and its original signal:
```python
import numpy as np
import matplotlib.pyplot as plt

n = 300
t = np.linspace(0, 4, n)
x = np.sin(t) + t * np.cos(t)**2 
w = 0.1 * np.random.randn(n)
b = x + w 

fig, axes = plt.subplots(2, 1, figsize=(8, 6))

# Original Signal
axes[0].plot(t, x, color='green')
axes[0].set_title("Original Signal")
axes[0].set_xlabel("t")
axes[0].set_ylabel("Signal")

# Noisy Measurement
axes[1].plot(t, b, color='red', alpha=0.5)
axes[1].set_title("Noisy Measurement")
axes[1].set_xlabel("t")
axes[1].set_ylabel("Signal")

plt.tight_layout()
plt.show()
```

##### Output
<img src="/assets/files/pictures/noisy-original-graph.png" width="30%" height="30%" style="border:none;">

#### With Ridge Regression:
```python


```