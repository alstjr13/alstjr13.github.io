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
- Symmetrical
- Area = 1
- Curve never hits 0
- Described by mean and standard deviation
- 68% falls within 1 std, 95% falls within 2 std, 99.7% falls within 3 std (68-95-99.7 Rule)

```python
from scipy.stats import norm

# What percent of women are shorter than 154cm?
norm.cdf(154, 161, 7)

# What percent of women are taller than 154cm?
1 - norm.cdf(154, 161, 7)

# What percent of women are 154 - 157 cm?
norm.cdf(157, 161, 7) - norm.cdf(154, 161, 7)

# What height are 90% of women shorter than?
norm.ppf(0.9, 161, 7)

# What height are 90% of women taller than?
norm.ppf((1 - 0.9), 161, 7)

# Generate 10 random heights
norm.rvs(161, 7, size=10)
```


#### Central Limit Theorem (CLT) ⭐⭐⭐⭐⭐
$\underline{\text{Theorem:}}$ The distribution of sample means approximates a normal distribution as the sample size gets larger, regardless of the population's distribution.
**Samples should be random and independent**
Applies to:
- Standard Deviation
- Proportions

Used to:
- Estimate characteristics of unknown underlying distribution
- More easily estimate characteristics of large populations


#### Poisson Distribution
**Equation:**  

$$f(k) = e^{-\mu}\frac{\mu^{k}}{k!}$$

$$\text{for  }     k \geq 0$$


Describes the probability of some number of events occurring over a fixed period of time and it is described by a value $\lambda$
- $\lambda$: average number of events per time interval

Poisson process:
- Events appear to happen at a certain rate, but completely at random
- Time unit is irrelevant, as long as it is consistent.

```python
from scipy.stats import poisson
poisson.pmf(5,8)
poisson.cdf(5,8)

# poisson.cdf(k, mu)
# poisson.pmf(k, mu)
```

#### Exponential Distribution
- Probability of time between Poisson events
- Also uses $\lambda$ (rate)
- Continuous (time)

```python
from scipy.stats import expon

expon.cdf(1, scale=2)                      # P(wait < 1min)

```


#### t-distribution
- Similar shape as the normal distribution

Degree of freedom (df):
- affects the thickness of the tails of the distribution
  - lower df: thicker tails, higher std
  - higher df: closer to normal distribution

#### Log-normal distribution
- Variable whose logarithm is normally distributed


#### Correlation
- Relationship between two variables
- x: explanatory / independent variable
- y: response / dependent variable
- Correlation coefficient quantifies the linear relationship between two variables
  - Number between -1 and 1
  - Magnitude corresponds to strength of relationship
  - Sign (+ / -) corresponds to direction of relationship
- Correlation does not imply causation (go take a look at spurious correlation, confounder)

**Pearson product-moment correlation (r)**
- Most common
- $\bar{x}$: mean of $x$
- $\sigma_{x}$: standard deviation of $x$
- $r = \sum_{i = 1}^{n}\frac{(x_{i} - \bar{x})(y_{i} - \bar{y})}{\sigma_{x} \times \sigma_{y}}$

```python
import seaborn as sns

# Plot scatter plot
sns.scatterplot(x="Independent Variable", y="Dependent Variable", data=msleep, ci=None)

# Correlation
msleep['sleep_total'].corr(msleep['sleep_rem'])
```

#### Transformations
- Log transformations ($\log{x}$)
- Square root transformation ($\sqrt{x}$)
- Reciprocal transformation ($\frac{1}{x}$)

#### Experimental Design
Experiment aims to answer: "What is the effect of the treatment on the response?"
- Treatment: explanatory / independent variable
- Response: response / dependent variable

##### Controlled Experiment
- Participants are assigned by researchers to either treatment group or control group
  - Treatment group sees advertisement
  - Control group does not
  - ex. A/B test
- Groups should be comparable so that causation can be inferred
- If groups are not comparable, this could lead to confounding (bias)

**Use** Randomized Controlled Trial
- Participants are assigned to treatment / control randomly, not based on any other characteristics
- Choosing randomly helps ensure that groups are comparable

**Use** Placebo
- Resembles treatment, but has no effect
- Participants will not know which group they fall into

**Use** Double-blind trial
- Person administering the treatment / running the study doesn't know whether the treatment is real or a placebo
- Prevents bias in the response and/or analysis of results

**Fewer opportunities for bias = more reliable conclusion about causation**

##### Observationsal Studies
- Participants are not assigned randomly to groups
  - Participants assign themselves, usually based on pre-existing characteristics
- Establish association, not causation
  - Effects can be confounded by factors that got certain people into the control or treatment group