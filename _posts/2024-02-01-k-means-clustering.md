---
layout: single
title: "[Machine Learning] K-Means Clustering"
categories: ['ML & DL']
tag: [Data, ['Machine Learning'], Classification]
toc: true
---

#### K-Means Clustering
[K-Means Clustering (K-평균 군집화 알고리즘)](https://en.wikipedia.org/wiki/K-means_clustering) is the most popular **unsupervised learning algorithm**. It is used when we have unlabelled data which is data without defined categories or groups. K-Means algorithm works iteratively to assign each data point to one of k groups based on the features that are provided. Data points are clustered based on feature similarity.

#### Applications:
1. Image segmentation
2. Customer segmentation
3. Species clustering
4. Anomaly detection
5. Clustering languages

#### Illustration
<img src="/assets/files/pictures/k-means-clustering.jpg" width="50%" height="50%">

<img src="/assets/files/pictures/k-means-clustering2.jpg" width="50%" height="50%">

#### K-Means Clustering (2D) Code Sample

```python
import pandas as pd
import numpy as np
from sklearn.cluster import KMeans
from sklearn.preprocessing import StandardScaler

from sklearn.datasets import load_iris

iris = load_iris()                     # Dataset
X = iris.data                          # Feature data
y = iris.target                        # True labels

scaler = StandardScaler()              
X_scaled = scaler.fit_transform(X)     # Standardize feature data

kmeans = KMeans(n_clusters=3, random_state=0, n_init=10)
kmeans.fit(X_scaled)

iris_labels = kmeans.labels_

iris_df = pd.DataFrame(X, columns=iris.feature_names)
iris_df["Cluster"] = iris_labels

print(iris_df.head())

"""
sepal length (cm)  sepal width (cm)  petal length (cm)  petal width (cm)  \
0                5.1               3.5                1.4               0.2   
1                4.9               3.0                1.4               0.2   
2                4.7               3.2                1.3               0.2   
3                4.6               3.1                1.5               0.2   
4                5.0               3.6                1.4               0.2   

   Cluster  
0        1  
1        1  
2        1  
3        1  
4        1  
"""
```

```python
# 2D Graph Representation (Using Iris Dataset - Sepal Length and Sepal Width)
X_iris_2D = X_scaled[:, :2]

kmeans_iris_2D = KMeans(n_clusters=3, random_state=0, n_init=10)
kmeans_iris_2D.fit(X_iris_2D)

centers_iris_2D = kmeans_iris_2D.cluster_centers
labels_iris_2D = kmeans_iris_2D.labels_

plt.figure(figsize=(8,6))
plt.scatter(X_iris_2D[:, 0], X_iris_2D[:, 1], c=labels_iris_2D, cmap='viridis', alpha=1)
plt.scatter(centers_iris_2D[:, 0], centers_iris_2D[:, 1], c='red', marker='X', s=200, label="Centroids")
plt.xlabel("Sepal Length")
plt.ylabel("Sepal Width")
plt.legend()
plt.title("K-Means Clustering (2D)")
plt.show()
```

##### Output

<img src="/assets/files/pictures/kmeans-2d.png" width="30%" height="30%">


#### K-Means Clustering (3D) Code Sample

```python
import pandas as pd
import numpy as np
from sklearn.cluster import KMeans
from sklearn.preprocessing import StandardScaler

from sklearn.datasets import load_iris

iris = load_iris()                     # Dataset
X = iris.data                          # Feature data
y = iris.target                        # True labels

```