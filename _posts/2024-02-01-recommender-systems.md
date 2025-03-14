---
layout: single
title: "Recommender Systems "
categories: ['ML & DL']
tag: [Data, ['Machine Learning'], ['Collaborative Filtering']]
toc: true
---

#### What is a recommender system?
A recommendation system recommends a particular product or service to users they are likely to consume.

#### Key notes:
- The whole idea is to understand user behaviour in order to recommend them products they are **likely to consume.**
- **"Filter bubble"** - narrows a user's exposure to diverse viewpoints and information.
  - This phenomenon of narrowing someone's perspective can be detrimental, particularly on context of scientific research or political discourse (requires a wide range of perspectives)


#### Data / Approaches to the problem
We need data like:
- Customer purchase history data
- User-item interactions (ex. ratings or clicks)
- Features related to items or users

##### Main approaches:
- Collaborative filtering
  - Unsupervised learning
- Content-based recommenders
  - Supervised learning
- Hybrid
  - Combining collaborative filtering with content-based filtering

#### Recommender Systems:

We have two entities:
  - $\mathbf{N}$ users, where users are consumers of the digital content
  - $\mathbf{M}$ items, where items are products or servises being offered

A **utility matrix** is the matrix that captures interactions between **N users** and **M items**. Interactions may come in as different forms such as ratings, clicks, purchases. A utility matrix is [sparse](https://en.wikipedia.org/wiki/Sparse_matrix), because normally users only interact with few items.

Given a utility matrix of N users and M items, our objective is to predict missing values in the matrix. Once we havfe predicted ratings, we can recommend items to users they are likely to rate higher.

In rating prediction, ratings data has many missing values in teh utility matrix (with no special target column). We want to predict the missing entries in the matrix.

$$Example: \mathbf{N}=6, \mathbf{M}=6, $$

$$\begin{bmatrix} ? & ? & ? & x_{1,4} & ? & x_{1,6} \\ 
                  ? & ? & ? & ? & x_{2,5} & ? \\ 
                  ? & x_{3,2} & x_{3,3} & ? & x_{3,5} & x_{3,6} \\
                  ? & ? & ? & ? & ? & ? \\
                  ? & ? & ? & ? & x_{5,5} & ? \\
                  ? & x_{6,2} & x_{6,3} & x_{6,4} & ? & x_{6,6} \end{bmatrix}$$


#### Python Code Example:
```python
from fastai.collab import *
from fastai.tabular.all import *
import pandas as pd

set_seed(42)

path = untar_data(URLs.ML_100k)

ratings = pd.read_csv(path/'u.data', delimiter='\t', header=None, names=['user','movie','rating','timestamp'])
ratings.head()

"""
     user | movie | rating | timestamp
----------------------------------------
0 |  196  |  242  |   3    |  881250949
----------------------------------------
1 |  186  |  302  |   3    |  891717742
----------------------------------------
2 |  22   |  377  |   1    |  878887116
----------------------------------------
3 |  244  |  51   |   2    |  880606923
----------------------------------------
4 |  166  |  346  |   1    |  886397596
----------------------------------------
"""

# Define keys for accessing this DataFrame
user_key = 'user'
item_key = 'movie'

# Define a function that prints statistics about this data, return number of rows (N) and number of columns (M)
def get_stats(ratings, item_key='movie', user_key='user'):
    print(f"Number of ratings: {len(ratings)}")                          # Number of ratings: 100000
    print(f"Average rating: {(np.mean(ratings['rating'])):.3f}")         # Average rating: 3.530
    N = len(np.unique(ratings[user_key]))
    M = len(np.unique(ratings[item_key]))
    print(f"Number of users (N): {N}")                                   # Number of users (N): 943
    print(f"Number of items (M): {M}")                                   # Number of items (M): 1682
    print(f"Fraction non-nan ratings: {len(ratings) / (N * M)}")         # Fraction non-nan ratings: 0.06304669364224531
    return N, M

# Store values of N, M
N, M = get_stats(ratings)


```


#### Content-based Filtering
Content-based filtering is a supervised machine learning approach to recommender systems. In content-based filtering, we assume that we are given item or user feature. Given movie information (for example), we create user profile for each user. We treat ratings prediction problem as a set of regression problems and build a regression model for each user. Once we have trained regression models for each user, we complete the utility matrix by predicting ratings for each user using their corresponding models.

##### Question to ask: How do we use the features to predict missing ratings?

Using the ratings and movie features:
- We build profiles for difference users
- Train a supervised machine learning model for each user
- Predict ratings using the trained models

##### Building user profiles:
- For each user $i$, create a user profile by:
  - Create $X$ and $y$ for the user $i$ where:
      - Each row in $X$ contains the movie features of movie $j$ rated by $i$
      - Each value in $y$ corresponding rating given to the movie $j$ given by $i$
  - Fit a regression model using $X$ and $y$
  - Apply the model to predict ratings for new items