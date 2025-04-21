---
layout: single
title: "Decision Tree"
categories: ['Machine Learning']
tag: [Data, ['Machine Learning']]
toc: true
---

#### Decision Tree Algorithm
[Decision tree algorithm](https://en.wikipedia.org/wiki/Decision_tree_learning) is a type of supervised learning algorithm used for both classification and regression tasks, used as a predictive model to get conclusions given a set of observations (i.e., training data)

A decision tree is a structure that includes a root node, branches, and leaf nodes. Each internal node denotes a test on an atrribute, each branch denotes the outcome of a test, and each leaf node holds a class label.
The very top node in the tree is the root node.

The intuition behind decision tree algorithms is as follows:
1. For each attribute in the dataset, the decision tree algorithm forms a node. The most important attribute is placed at the root node.
2. For evaluating the task, we start at the root node and we work our way done the tree by following the corresponding node that meets our condition or decision.
3. This process continues until a lead node is reached. It contains the prediction or the outcome of the decision tree.

##### Root Node
Represents the entire dataset. It splits into two or more homogeneous sets based on a feature.

##### Decision Nodes
Internal nodes where a feature is tested

##### Leaf Nodes
Final (or terminal) nodes that do not split further

### Metrics

Decision Trees use metrics to evaluate the best attribute to split the data at each node:

#### Gini Impurity
Gini Impurity measures the probability of a randomly chosen element being incorrectly labeled. Gini Index measures the purity of a node by estimating the probability that two randomly selected items belong to the same class. A Gini value of 1 indicates perfect purity. It is mainly used for categorical targets like "Success" or "Failure" and supports only binary splits.

[CART (Classification and Regression Trees)](https://www.geeksforgeeks.org/cart-classification-and-regression-tree-in-machine-learning/) uses the Gini method to create binary splits.

##### Mathematical Formula

$$Gini = 1 - \sum_{i=1}^{C}p_{i}^{2}$$


#### Entropy (Information gain)

Entropy is a measure of the disorder or uncertainty in a dataset (commonly used in Physics and Mathematics). 
In decision tree, it's used to quantify the impurity in a node. A node with only one class has entropy of 0 (meaning pure), while higher values indicate more disorder. In information theory, it refers to the impurity in a group of examples. Information gain is the decrease in entropy. Information gain computes the difference between entropy before split and average entropy after the split of the dataset based on given attribute values.

##### Mathematical Formula

$$Entropy = \sum_{i=1}^{C}-p_{i}*log_{2}(p_{i})$$

The [ID3 (Iterative Dichotomiser 3)](https://en.wikipedia.org/wiki/ID3_algorithm) decision tree algorithm uses entropy to calculate information gain. By calculating the decrease in entropy for each attribute, we determine its information gain. The attribute with the highest information gain is selected as the best splitting attribute at a decision tree node.



#### Python code example (with Gini Index)

```python
import warnings

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

from sklearn.datasets import load_iris
from sklearn.tree import DecisionTreeClassifier
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

warnings.filterwarnings('ignore')

# Load Iris Dataset
iris = load_iris()

X = iris.data
y = iris.target
feature_names = iris.feature_names
class_names = iris.target_names

# Split Dataset
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Train DecisionTreeClassifier Model
clf_gini = DecisionTreeClassifier(criterion='gini', max_depth=3, random_state=0)
clf_gini.fit(X_train, y_train)

# Predict the Test set results
y_pred_gini = clf_gini.predict(X_test)

# Check Accuracy score with criterion gini index
print(f"Model accuracy score with criterion gini index: {accuracy_score(y_test, y_pred_gini):.2f}")         # Model accuracy score with criterion gini index: 1.00

# Check for overfitting and undefitting
print(f"Training set score: {clf_gini.score(X_train, y_train):.4f}")                                        # Training set score: 0.9583
print(f"Test set score: {clf_gini.score(X_test, y_test):.4f}")                                              # Test set score: 1.0000

plt.figure(figsize=(12,8))

tree.plot_tree(clf_gini.fit(X_train, y_train)) 
```

##### Sample Output
After calling tree.plot_tree(clf_gini.fit(X_train, y_train)), we get:

<img src="/assets/files/pictures/decisiontree1.png" width="30%" height="30%">

#### Python Example (Continued)
```python
import graphviz

dot_data = tree.export_graphviz(clf_gini,
                                out_file= None,
                                feature_names = feature_names,
                                class_names = class_names,
                                filled=True, 
                                rounded=True,
                                special_characters = True)

graph = graphviz.Source(dot_data)

graph
```

##### Sample Output
<img src="/assets/files/pictures/decisiontree2.png" width="30%" height="30%">
