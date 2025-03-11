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
import numpy as np
import matplotlib.pyplt as plt
from sklearn.linear_model import Ridge

n = 300
t = np.linspace(0, 4, n)
x = np.sin(t) + t * np.cos(t)**2 
w = 0.1 * np.random.randn(n)
b = x + w 

degree = 10                                           # Polynomial degree for smooth approximation
X = np.vstack([t**i for i in range(degree + 1)]).T    # Transposed array for manually creating polynomial features

# Fit
alpha = 0.1                                           # Regularization Strength
ridge = Ridge(alpha = alpha)                          # Ridge regression object
ridge.fit(X, b)

# and predict
b_denoised = ridge.predict(X)

plt.figure(figsize=(8, 5))
plt.plot(t, b, label="Noisy signal", alpha=0.5)
plt.plot(t, b_denoised, label="Denoised signal (Ridge)", color='red', linewidth=2)
plt.plot(t, x, label="Original signal", color='green', linestyle='dashed')
plt.legend(loc="upper left")
plt.xlabel("t")
plt.ylabel("Signal")
plt.title("Signal Denoising using Ridge Regression")
plt.show()
```

##### Output
<img src="/assets/files/pictures/noisy-original-ridge.png" width="30%" height="30%" style="border:none;">

#### Mean Squared Error (MSE)
```python
from sklearn.metrics import mean_squared_error

mse = mean_squared_error(x, b_denoised)
mse_original = mean_squared_error(x, b)
mse_compare = mean_squared_error(b, b_denoised)
print(f"[ORIGINAL / RIDGE] Mean Squared Error (MSE): {mse}")
print(f"[NOISY / ORIGINAL] Mean Squared Error (MSE): {mse_original}")
print(f"[NOISY / RIDGE] Mean Squared Error (MSE): {mse_compare}")

"""
[ORIGINAL / RIDGE] Mean Squared Error (MSE): 0.0001466062179224322
[NOISY / ORIGINAL] Mean Squared Error (MSE): 0.01026635119617647
[NOISY / RIDGE] Mean Squared Error (MSE): 0.010157205751110005
"""
```

#### Summary
MSE (between noisy and original, denote $\epsilon_{1}$) is approximately $1.0266 \%$ and MSE (between noisy and ridge model, denote $\epsilon_{2}$) is about $1.018 \%$.

Since $\epsilon{2}$ is lower than $\epsilon_{1}$, it implies that the ridge regression model provides a better reconstruction of the original signal than the noisy version alone. More accurate approximation! 

