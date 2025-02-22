---
layout: single
title: "[Datacamp] Introduction to Statistics in Python"
categories: ["Statistics"]
tag: [Statistics, Mathematics, Data, ["Data Modelling"], Python]
toc: true
---

### Notes

#### Probability of an event:
- $P(event) = \frac{\text{# ways event can happen}}{\text{total # of possible outcomes}}$
- Always a value between $0$ to $1$ (i.e. $P(event) \in [0, 1]$)

#### Independent event:
- Two events are **independent** if the probability of the second event **isn't affected** by the outcome of the first event
- $\textit{example:}$ sampling with replacement

#### Dependent event:
- Two events are **dependent** if the probability of the second event **is affected** by the outcome of the first event
- $\textit{example:}$ sampling without replacement

#### Discrete Distribution:
- Probability distribution $\to$ describes the probability of each possible outcome in a scenario

#### Continuous Distribution:
- Continuous function of probability

```python
from scipy.stats import uniform
uniform.cdf(7,0,12)
```

#### Binomial Distribution
- Describes the probability distribution of the number of successes in a sequence of independent trials
- Described by $n$ and $p$ where:
  - $n:$ total number of trials
  - $p:$ probability of success
- Expected value = $n \times p$
- The binomial distribution is a probability distribution of the number of successes in a sequence of independent trials (i.e. Independence is preserves for each trial of binomial distribution)

```python
from scipy.stats import binom

binom.rvs(1, 0.5, size = 8)          # Flip 1 coin with 50% chance of success 8 times  -> array([0,1,1,0,1,0,1,1])
binom.rvs(8, 0.5, size = 1)          # Flip 8 coins with 50% chance of success 1 time  -> array([5])
binom.rvs(3, 0.5, size = 10)         # Flip 3 coins with 50% chance of success 10 times -> array([0,3,2,1,3,0,2,2,0,0])

# binom.pmf(num_heads, num_trials, prob_of_heads)
binom.pmf(7, 10, 0.5)                # P(heads = 7)

binom.cdf(7, 10, 0.5)                # P(heads <= 7)

1 - binom.cdf(7, 10, 0.5)            # P(heads > 7)
```

#### Normal Distribution