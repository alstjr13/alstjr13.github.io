---
layout: single
title: "Federated Learning"
categories: ['Deep Learning']
tag: [Data, ['Machine Learning'], ['Deep Learning']]
toc: true
---

#### What is Federated Learning in Deep Learning?
**Federated learning** (also known as **Collaborative Learning**) is a **distributed machine learning process (technique)** that uses multiple servers to share model updates without exchanging raw data. In other words, federated learning is a machine learning technique that allows multiple decentralized devices or servers to collaboratively train a shared model without exchanging raw data. This process helps to overcome the sensitivity to data and privacy-protected technology.

Instead of sending data to a central server, each participant (smartphone, IoT device or edge server for example) trains a local model on its own data, then shares only model updates with a central aggregator. The central server then combines these updates to improve the global model.

#### Why do we use Federated Learning?
Federated Learning provides key advantages such as:
- **Data privacy (Security)**
  - Federated Learning **ensures that raw data remains on the local device (user's device)**. This helps minimize the exposure of sensitive information. 
  - **Compliance with data protection regulations** 
- **Efficiency**
  - Instead of updating large datasets, only model updates (such as graients or weights) are shared.
- **Scalability**
  - Since training occurs across diverse devices, the model learns from a 
- **Personalization!!**
  - Since training happens locally within the user's own device, federated learning allows personalized models without compromising user's privacy.
    - Example of usage: [Google Keyboard (Gboard)](https://research.google/pubs/federated-learning-for-mobile-keyboard-prediction-2/)
      - Journal:
        - [Federated Learning of Gboard Language Models with Differential Privacy](https://arxiv.org/pdf/2305.18465)

#### Mathematical Equation:
The objective function for federated learning is:

$$ f(x_{1}, \cdots, x_{K}) = \frac{1}{K}\sum_{i=1}^{K}f_{i}(x_{i}) $$

where:
- $K$ is the number of nodes
- $x_{i}$ are the weights of model as viewed by node $i$
- $f_{i}$ is node $i$'s local objective function, which describes how model weights $x_{i}$ conforms to node $i$'s local dataset.

##### The goal is to:
- Optimize the objective function $f(x_{1}, \cdots, x_{K})$
- Achieving consensus on $x_{i}$ at the end of training process.

#### Types of Federated Learning:

##### Centralized federated learning
- Central server is used to orchestrate the different steps of the algorithms and coordinate all the participating nodes during the learning process.
- The server is responsible for 
  - the nodes selection at the beginning of the training process
  - the aggregation of the received model updates

##### Decentralized federated learning
- Individual devices or nodes communicate directly with each other to collaboratively train a machine learning model.
- Shares only model weights instead of user data

Journals:
- [Decentralized Federated Learning: A Survey and Perspective](https://arxiv.org/pdf/2306.01603)

##### Horizontal Federated Learning (HFL)

##### Vertical Federated Learning (VFL)

##### Cross-Silo Federated Learning

##### Cross-Device Federated Learning

#### Python
- [Flower Framework](https://flower.ai/docs/framework/tutorial-series-what-is-federated-learning.html)
- [TFF (TensorFlow Federated)](https://www.tensorflow.org/federated?hl=ko)

```python
!pip install tensorflow==2.10.0
!pip install tensorflow_federated

# Check TFF specifications
```

#### Applications
- Healthcare
  - Electronic Health Records (EMR)
  - Biomedical Image Analysis
  - EEG Classification (Brain activity patern classification)
  - Clinical Prediction
- Internet of Things (IoT)
  - Smart Transporation
  - Smart City
    - Journals:
      - [Federated learning for smart cities: A comprehensive survey](https://www.sciencedirect.com/science/article/abs/pii/S2213138822010359)
      - [Applications of Federated Learning in Smart Cities: Recent Advances, Taxonomy, and Open Challenges](https://arxiv.org/pdf/2102.01375)
  - Smart Grid
- Industrial Engineering
  - 6G Industry
  - Image Detection
  - Image Representation
  - Unmanned Aerial Vehicles
  - Electrical Vehicles
  - Financial Field
  - Text Mining
- Smart manufactoring
- Robotics
- Blockchain
- Edge Computing

#### Journals about Federated Learning
- [Federated learning: Overview, strategies, apllications, tools and future directions](https://www.sciencedirect.com/science/article/pii/S2405844024141680)