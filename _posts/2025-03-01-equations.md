---
layout: single
title: "Equations"
categories: ["Equations"]
tag: [Math, Econometrics]
toc: true
---

### Metrics

#### Shannon-Wiener Index

**Usage:** a metric used to measure the diversity of a community or ecosystem.

$$\mathbf{H^{'}} = -\sum{p_{i}}\ln{p_{i}}$$ 

where:
- $\mathbf{H^{'}}$: The species diversity index (Shannon diversity index)
- $p_{i}$: The proportion of individuals of $i^{th}$ species in a whole community
  - $p_{i} = \frac{n}{\mathbf{N}}$ where:
    - $n$: individuals of given type/species
    - $\mathbf{N}:$ total number of individuals in a community

#### Gini Coefficient (Gini Index)

**Usage:** Measures how unequal income or wealth is distributed within a population (captures how far the Lorenz curve falls from the "line of equality" by comparing the areas A and B)

$$\text{Gini coefficient} = \frac{A}{A + B}$$

#### Entropy

$$Entropy = \sum_{i=1}^{C}-p_{i}*\log{p_{i}}$$

### Classification Metrics

- TN $\rightarrow$ True Negatives (non-fraud predicted as non-fraud)
- TP $\rightarrow$ True Positives (fraud predicted as fraud)
- FN $\rightarrow$ False Negatives (fraud predicted as non-fraud)
- FP $\rightarrow$ False Positives (non-fraud predicted as fraud)

#### Confusion Matrix

```python
------------------------------------------------------------------------------------------------------  
                                PREDICTED
                           Positive                  Negative             Total
------------------------------------------------------------------------------------------------------  
ACTUAL | Positive |   True Positive         |  False Negative (FN)  |   Number of Positives
       |          |        (TP)             |   (Type 2 Error)      |
------------------------------------------------------------------------------------------------------      
       | Negative |   False Positive (FP)   |    True Negative      |   Number of Negatives
       |          |      (Type 1 Error)     |         (TN)          |
------------------------------------------------------------------------------------------------------
       |  Total   |        TP + FP          |         FN + TN       |   Number of Examples
```

#### Accuracy

$$Accuracy = \frac{TP + TN}{TP + FP + TN + FN}$$

#### Precision

$$Precision = \frac{TP}{TP + FP}$$

#### Recall

$$Recall = \frac{TP}{TP + FN}$$

#### F1 Score

$$F1 Score = 2 \times \frac{Precision \times Recall}{Precision + Recall}$$

#### 

### Statistics

#### Mean Squared Error (MSE)

#### Coefficient of Determination ($R^{2}$)
$$R^{2} = 1 - \frac{\text{Sum of squares of residuals}}{\text{Total sum of squares}} = 1 - \frac{\sum{(y_{i} - \hat{y_{i}})^{2}}}{\sum{(y_{i}-\bar{y})^{2}}}$$


