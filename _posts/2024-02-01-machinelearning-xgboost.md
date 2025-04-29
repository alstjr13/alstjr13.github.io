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
from sklearn.impute import SimpleImputer

data = pd.read_csv('/kaggle/input/home-data-for-ml-course/train.csv')
data.dropna(axis=0, subset=['SalePrice'], inplace=True)
y = data.SalePrice

X = data.drop(['SalePrice'], axis=1).select_dtypes(exclude=['object'])
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.25)

imputer = SimpleImputer()
X_train = imputer.fit_transform(X_train)
X_test = imputer.fit_transform(X_test)
```

```python
from xgboost import XGBRegressor
from sklearn.metrics import mean_absolute_error

model = XGBRegressor(n_estimators=1000)
model.fit(X_train, y_train, 
          early_stopping_rounds=5,
          eval_set=[(X_test, y_test)],
          verbose=False)

predictions = model.predict(X_test)
print(f"Mean Absolute Error : {mean_absolute_error(predictions, y_test)}")                           # Mean Absolute Error : 17708.147988013698
```