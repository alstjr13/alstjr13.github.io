---
layout: single
title: "XGBoost"
categories: ['Machine Learning']
tag: [Data, ['Machine Learning']]
toc: true
---

#### What is XGBoost?
[XGBoost (eXtreme Gradient Boosting)](https://xgboost.readthedocs.io/en/release_3.0.0/) is an open-source library that provides a highly scalable and efficient implementation of gradient boosting decision trees. It has become one of the most popular algorithms for structured / tabular data (used for ex. classification - spam detection, ex. regression - house price prediction), powering many winning solutions in machine learning competitions.

(Refer to Gauss Newton's method of gradient descent)

Gradient boosting is a method that goes through cycles to iteratively add models into an ensemble. It begins by initializing the ensemble with a single model (with naive predictions), then we start the cycle: 
- We use the current ensemble to generate predictions for each observation in the dataset. To make a prediction, we add the predictions from all models in the ensemble.
- These predictions are used to calculate a loss function (ex. MSELoss)
- We use the loss function to fit a new model that will be added to the ensemble. We determine model parameters so that adding this new model to the ensemble will reduce the loss.
- Finally, we add the new model to ensemble.
  - Iterate...

#### Python Code Example
```python
# Preprocess data
import pandas as pd
from sklearn.model_selection import train_test_split

data = pd.read_csv('../input/melbourne-housing-snapshot/melb_data.csv')

columns_to_use = ['Rooms', 'Distance', 'Landsize', 'BuildingArea', 'YearBuilt']

X = data[columns_to_use]
y = data.Price

X_train, X_valid, y_train, y_valid = train_test_split(X, y)
```

```python
from xgboost import XGBRegressor
from sklearn.metrics import mean_absolute_error

model = XGBRegressor()
model.fit(X_train, y_train)

predictions = model.predict(X_valid)



```