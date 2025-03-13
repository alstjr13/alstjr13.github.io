---
layout: single
title: "Deep Learning"
categories: ['ML & DL']
tag: [Data, ['Machine Learning'], ['Deep Learning'], ['Neural Network']]
toc: true
---

#### What is Deep Learning?
Deep learning is an approach to machine learning characterized by deep stacks of computations.

#### Linear Unit:
The fundamental component of a neural network: the individual neuron. As a diagram, a neuron (or unit) with one input looks like:

<img src="/assets/files/pictures/single-input.png" width="30%" height="30%" style="border:none;">

where the equation of linear unit can be expressed as: 

$$y = wx + b$$

and the input is $x$.

Its connection to the neuron has a weight $w$. Whenever a value flows through a connection, you multiply the value by the connection's weight (i.e. $w * x$). A neural network "learns" by modifying its weight.

생각을 해보면, 우리도 무언가를 "학습" 할 때, 중요하다고 생각이 들면 좀 더 집중해서 배우게 된다. 똑같이 생각하면 될 듯싶다.

$b$ is a special kind of weight called bias. The bias doesn't have any input data associated with it. Instead, we put a $1$ in the diagram so that the value that reaches the neuron is just $b$ ($1 * b = b$). The bias enables the neuron to modify the output independently of its inputs.

The $y$ is the value the neuron ultimately outputs. This neuron's activation is $y = wx + b$

##### Linear Units in Keras

```python
from tensorflow import keras
from tensorflow.keras import layers

# Create a network with 1 linear unit
model = keras.Sequential([
  layer.Dense(units=1, input_shape=[3])
])

# To look at the weight and bias
w, b = model.weights                             # returns two tf.Variable
print(f"Weight: {w}, \n Bias: {b}")

# or we can also use:
# w, b = model.get_weights()
```

##### Multiple Inputs

Consider this image demonstrating multiple inputs to a single neuron:

<img src="/assets/files/pictures/multiple-inputs.png" width="30%" height="30%" style="border:none;">

where the equation of linear unit can be expressed as: 

$$y = w_{0}x_{0} + w_{1}x_{1} + w_{2}x_{2} + b$$

#### Layers

Neural networks typically organize their neurons into layers. When we collect together linear units having a common set of inputs, we get a dense layer.

<img src="/assets/files/pictures/layers.png" width="30%" height="30%" style="border:none;">

We can also interpret each layer in a neural network as performing a relatively simple transformation. Through a deep stack of layers, a neural network can transform its inputs in more complex ways. In a well-trained neural network, each layer can lead to such transformations closer to the solutions we want.


#### Sequential Model

```python
from tensorflow import keras
from tensorflow.keras import layers

model = keras.Sequential([
  # the hidden ReLU layers
  layers.Dense(units=4, activation='relu', input_shape=[2]),
  layers.Dense(units=3, activation='relu'),

  # the linear output layer
  layers.Dense(units=1)
])

```