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

$$min_{x}\frac{1}{2}||Ax - b||^{2} + \lambda\frac{1}{2}||Dx||^{2}$$

This objective can be expressed equivalently as:

$$||Ax - b||^{2} + \lambda||Dx||^{2} = ||\begin{bmatrix} A \\ \sqrt{\lambda}D \end{bmatrix}x - \begin{bmatrix} b \\ 0 \end{bmatrix}||^{2}$$

If D has full rank, then the stacked matrix $$\begin{bmatrix} A \\ \sqrt{\lambda}D \end{bmatrix}$$ neccessarily also has full rank for any positive $\lambda$, which implies that the regularized problem always has an unique solution.

#### Code Example:
```python
import pandas as pd
```