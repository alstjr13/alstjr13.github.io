---
layout: single
title: "Overfitting / Underfitting"
categories: ['Machine Learning']
tag: [Data, ['Machine Learning'], ['Deep Learning'], ['Neural Network']]
toc: true
---

#### Introduction
We train a model by choosing weights or parameters that minimize loss on a training data set. In order to accurately assess a model's performance, we need to evaluate it on a new set of data, <ins> the validation data</ins>,

We plot a plot called **learning curves** to interpret how effectively the model is being trained.

We need to know that the training loss will go down either when the model learns signal or when it learns noise. BUT, the validation loss will go down **only** when the model learns signal.

#### Trade-off
Ideal model is a model that learn all of the signal and none of the noise. However, this practically never happens. 

Instead, we ca get the model to learn more signal at the cost of learning more noise. Until the point of trade is in our favour, the validation loss will continue to decrease. However, after a certain point, the trade begins to go against us and cost exceeds the benefit and the validation loss begins to rise.

##### Underfitting
Underfitting the training set is when the loss is not as low as it could be, because the model hasn't learned enough signal.

##### Overfitting
Overfitting the training set is when the loss is not as low as it could be, because the model learned too much noise. 

##### Objective
The objective of training a deep learning model is to find the best point between underfitting and overfitting (optimizing a model).

##### Capacity
A model's capacity refers to the size and complexity of the patterns it is able to learn.

You can increase the capacity of a network either by:
- Making it wider (more units to existing layers)
- Making it deeper (adding more layers)

**Wider networks** have easier time learning more linear relationships.

**Deeper networks** have easier time learning more nonlinear ones. Dependent of the datasets we decide to choose.


#### Early stopping

<img src="/assets/files/pictures/early-stopping.png" width="30%" height="30%" style="border:none;">

##### Code Sample

```python
from tensorflow.keras.callbacks import EarlyStopping

early_stopping = EarlyStopping(
  min_delta=0.001,             # minimium amount of change to count as an improvement
  patience=20,                 # how many epochs to wait before stopping
  restore_best_weights=True,
)

```