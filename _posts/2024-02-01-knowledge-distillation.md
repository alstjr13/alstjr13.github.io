---
layout: single
title: "[Deep Learning] Knowledge Distillation"
categories: ['ML & DL']
tag: [Data, ['Machine Learning'], ['Deep Learning']]
toc: true
---

<!-- 언제 (when do we use?) 무엇을 (what do we use it for?) 어떻게 (How do we use it?) 왜 (Why do we use it?)-->

#### What is Knowledge Distillation?
**Knowledge distillation** is a machine learning technique that aims to transfer the learnings of a large pre-trained model (the "teacher" model) to a smaller model (the "student" model). In other words, it is a model compression technique in machine learning where a smaller model ('student' model) learns from a more complex model ('teacher' model).

The goal is to transfer the 'knowledge' from the teacher to the student so that the students performs almost the same as the teacher, but with fewer parameters, faster inference, and lower resource requirements.

#### Why use Knowledge Distillation?
- To deploy models on edge devices (ex. phones or IoT), where the memory are limited
- To speed up inference in real-time applications (ex. Recommendation Systems, ChatBots)
- To maintain most of the performance of the larger model, and use the more efficient one

##### Diagram
<figure>
    <img src="/assets/files/pictures/knowledge-distillation.png" width="50%" height="50%">
    <figcaption>Source: <a href="https://arxiv.org/abs/2006.05525" target="_blank">Arxiv</a></figcaption>
</figure>

#### Python Code Example:

```python
import torch
import torch.nn as nn
import torch.optim as optim
import torchvision.transforms as transforms
import torchvision.datasets as datasets

# Teacher Model
class DeepNN(nn.Module):
    def __init__(self, num_classes = 10):
        super(DeepNN, self).__init__()
        self.features = nn.Sequential(
            nn.Conv2d(3, 128, kernel_size = 3, padding = 1),
            nn.ReLU(),
            nn.Conv2d(128, 64, kernel_size = 3, padding = 1),
            nn.ReLU(),
            nn.MaxPool2d(kernel_size = 2, stride = 2),
            nn.Conv2d(64, 64, kernel_size = 3, padding = 1),
            nn.ReLU(),
            nn.Conv2d(64, 32, kernel_size = 3, padding = 1),
            nn.ReLU(),
            nn.MaxPool2d(kernel_size = 2, stride = 2),
        )
        self.classifier = nn.Sequential(
            nn.Linear(2048, 512),
            nn.ReLU(),
            nn.Dropout(0.1),
            nn.Linear(512, num_classes)
        )
    
    def forward(self, x):
        x = self.features(x)
        x = torch.flatten(x, 1)
        x = self.classifier(x)
        return x

# Student Model
class LightNN(nn.Module):
    def __init__(self, num_classes = 10):
        super(LightNN, self).__init__()
        self.features = nn.Sequential(
            nn.Conv2d(3, 16, kernel_size = 3, padding = 1),
            nn.ReLU(),
            nn.MaxPool2d(kernel_size = 2, stride = 2),
            nn.Conv2d(16, 16, kernel_size = 3, padding = 1),
            nn.ReLU(),
            nn.MaxPool2d(kernel_size = 2, stride = 2),
        )
        self.classifier = nn.Sequential(
            nn.Linear(1024, 256),
            nn.ReLU(),
            nn.Dropout(0.1),
            nn.Linear(256, num_classes)
        )
    def forward(self, x):
        x = self.features(x)
        x = torch.flatten(x, 1)
        x = self.classifier(x)
        return x
```

```python
'''
For Training and Evaluation 
'''

def train():

```

#### Article Links:
- [Distilling the Knowledge in a Neural Network](https://arxiv.org/abs/1503.02531)
- [Knowledge Distillation: A Survey](https://arxiv.org/abs/2006.05525)

