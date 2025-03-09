---
title: "Correlation and Regression: A Gentle Introduction"
author: arjit_praveen
description: Introduction to Regression with statsmodels in Python
date: 2025-03-08 20:29:00 +0000
categories: [Data Science]
tags: [Statistics, Python]
math: true
toc: true
---

## Introduction

### Correlation coefficient and Scatter graphs

A **correlation coefficient** ($$r$$) is the measure of the strength and direction of a linear relationship between two variables. 

- *Strength* refers to how closely data points cluster around a straight line. A strong correlation allows us to predict one variable based on the other.

    - $$ r = 1 $$ or $$ r = -1 $$: perfect correlation
    - $$ r $$ close to $$ 1 $$: strong correlation. (eg. $$ r = 0.90 $$)
    - $$ r $$ close to $$ 0 $$: weak correlation. (eg. $$ r = 0.23 $$)

- *Direction* is indicated by the sign of the correlation coefficient, $$+$$ and $$-$$.

    - Positive correlation ($$r < 0$$): As one variable increases, the other increases.
    - Negative correlation ($$r > 0$$): As one variable increases, the other decreases.

This relationship can be represented using a scatter plot using Python's `seaborn` library, which is built on top of `matplotlib`.

```python
sns.relplot(x = 'happiness_score', y = 'life_exp', data = happiness, kind = 'scatter')
plt.show()
```

![Desktop View](..\code\img\output.svg){: width = "" height = ""}
_happiness score vs. life expectancy_

The image above is a scatter plot with a fitted line regression (you don't need to know what line regression is for now). It shows a scatter plot between the happiness score of an individual and their corresponding life expectancy. Notice how the trend goes upwards and is clustered closely towards the line? It suggests that there is a **strong positive correlation** between the two variables.

### Calculating correlation coefficient

There are several ways to calculate the correlation coefficient, one of which is Pearson's product-moment correlation, more commonly known as the **Pearson correlation coefficient**.

$$r = \frac{\text{cov}(X, Y)}{\sigma_X \sigma_Y} = \frac{\sum (x_i - \bar{x})(y_i - \bar{y})}{\sqrt{\sum (x_i - \bar{x})^2} \sqrt{\sum (y_i - \bar{y})^2}}$$

This can also be computed using the `np.corrcoef()` function. It returns the correlation matrix of 2 variables. 

```python
np.corrcoef(happiness['happiness_score'], happiness['life_exp'])
```

### Correlation $$\neq$$ Causation!

A common misconception of a near perfect correlation is that 

## Regression

Dataset: [World Happiness](..\code\data\world_happiness.csv)