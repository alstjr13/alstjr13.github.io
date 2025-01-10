---
layout: single
title: "Linear Regression"
categories: ["Data Analysis"]
tag: [Data, Mathematics, ["Data Modelling"]]
toc: true
---

#### Introduction:
[Linear Regression](https://en.wikipedia.org/wiki/Linear_regression) is a statistical method used to model the relationship between a dependent variable and an independent variable (in case of simple linear regression) by fitting a linear equation to observed data.
The objective is to find the linear equation that best predicts the dependent variable based on the values of the independent variables. It is widely used in data analysis and predictive modeling due to its simplicity and interpretability.

(한국어로는 "선형 회귀", 선형 **상관** 관계를 모델링하는 회귀 분석 기법이다.)

#### Mathematical Equation:
The mathematical equation to linear regression can be expressed as:

$$y = \beta_0 + \beta_1x_1 + \beta_2x_2 + \ldots + \beta_nx_n + \epsilon $$

$\text{ }$

$$\text{or}$$

$\text{ }$

$$\mathbf{y} = \mathbf{X}\boldsymbol{\beta} + \boldsymbol{\epsilon}$$

$\text{ }$

$$\text{where}$$ 

$\text{ }$

$$\mathbf{y} = \begin{bmatrix} y_{1} \\ y_{2} \\ \vdots \\ y_{n} \end{bmatrix}, 
\mathbf{X} = \begin{bmatrix} x_{1}^{T} \\ x_{2}^{T} \\ \vdots  \\ x_{n}^{T} \end{bmatrix} = 
\begin{bmatrix} 1 & x_{11} & \cdots & x_{1p} \\ 1 & x_{21} & \cdots & x_{2p} \\ \vdots & \vdots & \ddots & \vdots \\ 1 & x_{n1} & \cdots & x_{np}\end{bmatrix}, 
\boldsymbol{\beta} = \begin{bmatrix} \beta_{0} \\ \beta_{1} \\ \beta_{2} \\ \vdots \\ \beta_{p} \end{bmatrix},
\boldsymbol{\epsilon} = \begin{bmatrix} \epsilon_{1} \\ \epsilon_{2} \\ \vdots \\ \epsilon_{n} \end{bmatrix}$$

$$\text{in matrix notation.}$$




#### Code Example:
```python
# NOTE: The dataset is from Kaggle
import pandas as pd
from sklearn.model_selection import train_test_split

```

