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

# Read .csv file using Pandas
df = pd.read_csv("https://github.com/ybifoundation/Dataset/raw/main/Salary%20Data.csv")

'''
    | "Experience Years" | "Salary"
-----------------------------------------
0   |                1.1 |   39343
-----------------------------------------
1   |                1.2 |   42774
-----------------------------------------
.
.
.
'''
```

```python
# Define target and feature variables
X = df[["Experience Years"]]
y = df[["Salary"]]
```

```python
from scipy import stats

# Returns:
'''
- slope: Slope of the regression line.
- intercept: Intercept of the regression line.
- rvalue: The Pearson correlation coefficient.
- pvalue: The p-value for a hypothesis test whose null hypothesis is that the slope is zero
- stderr: Standard error of the estimated slope (gradient), under the assumption of residual normality.
- intercept_stderr: Standard error of the estimated intercept, under the assumption of residual normality.
'''
result = stats.linregress(X.values.flatten(), y.values.flatten())

print(result.slope)                  # 9523.650507417702
print(result.intercept)              # 25673.01576053029
print(result.rvalue)                 # 0.9776918968570497
print(result.pvalue)                 # 2.324309157602015e-27
print(result.stderr)                 # 331.90995198065553
print(result.intercept_stderr)       # 1920.0997893859012

# Equation for computing: f(x) = mx + b, where m is the slope and b is the intercept 
y_pred = result.slope * X + result.intercept
```

```python
import matplotlib.pyplot as plt

# Plot the data points
plt.scatter(X, y, color='blue', label='Data points')

# Plot the linear regression line
y_pred = result.slope * X + result.intercept
plt.plot(X, y_pred, color='red', label='Regression line')

# Scientific notation for p-value
formatted_p_value = f"{result.pvalue:.3e}"

# Add regression equation and p-value in a box at the bottom-right
equation = f"y = {result.slope:.2f}x + {result.intercept:.2f}"
p_value_text = f"p-value: {formatted_p_value}"
text_box = f"{equation}\n{p_value_text}"

# Create a bounding box for for LOBF equation and p-value
props = dict(boxstyle='round', facecolor='white', alpha=0.8)
plt.text(X.max() * 0.72, y.min() * 1.0, text_box, fontsize=8, bbox=props, color='black')

# Add labels
plt.xlabel("Experience Years")
plt.ylabel("Salary")
plt.title("Linear Regression: Salary vs. Experience")
plt.legend()

plt.show()
```

##### Output from Code Example
<img src="/assets/files/pictures/linear-regression-photo.png" width="30%" height="30%" style="border:none;">

##### Insights:
