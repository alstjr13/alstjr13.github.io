---
layout: single
title: "Linear Regression"
categories: ["Data Analysis"]
tag: [Data, Mathematics, ["Data Modelling"]]
toc: true
use_math: true
---

#### Introduction:
[Linear Regression](https://en.wikipedia.org/wiki/Linear_regression) is a statistical method used to model the relationship between a dependent variable and an independent variable (in case of simple linear regression) by fitting a linear equation to observed data.
The objective is to find the linear equation that best predicts the dependent variable based on the values of the independent variables. It is widely used in data analysis and predictive modeling due to its simplicity and interpretability.

(한국어로는 "선형 회귀", 선형 **상관** 관계를 모델링하는 회귀 분석 기법이다.)

#### Mathematical Equation:
The mathematical equation to linear regression can be expressed as:

$$y = \beta_0 + \beta_1x_1 + \beta_2x_2 + \ldots + \beta_nx_n + \epsilon$$

$$\text{or}$$

$$\mathbf{y} = \mathbf{X}\boldsymbol{\beta} + \boldsymbol{\epsilon}$$

$$\text{where}$$

$$\mathbf{y} = \begin{bmatrix}
y_1 \\
y_2 \\
\vdots \\
y_n
\end{bmatrix}$$
