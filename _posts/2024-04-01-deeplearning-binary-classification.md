---
layout: single
title: "Binary Classification"
categories: ['Deep Learning']
tag: [Data, ['Machine Learning'], ['Deep Learning'], ['Neural Network']]
toc: true
---


#### Binary Classification Example

```python
from tensorflow import keras
from tensorflow.keras import layers

model = keras.Sequential([
  layers.Dense(4, activation='relu', input_shape=[33]),
  layers.Dense(4, activation='relu'),
  layers.Dense(1, activation='sigmoid'),
])

model.compile(
  optimizer='adam',
  loss='binary_crossentropy',
  metrics=['binary_accuracy'],
)

early_stopping = keras.callbacks.EarlyStopping(
  patience=10,
  min_delta=0.001,
  restore_best_weights=True,
)

history = model.fit(
  X_train, y_train,
  validation_data = (X_valid, y_valid),
  batch_size = 512,
  epochs = 1000,
  callbacks=[early_stopping],
  verbose=0,
)

history_df = pd.DataFrame(history.history)

history_df.loc[5:, ['loss', 'val_loss']].plot()
history_df.loc[5:, ['binary_accuracy', 'val_binary_accuracy']].plot()



```