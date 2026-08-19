# Outlier Detection and Treatment

A short and simple guide to **outliers in Machine Learning**, their effects, detection methods, and treatment techniques.

## What is an Outlier?

An **outlier** is a data point that is significantly different from the majority of observations in a dataset.

Example:

```text
10, 12, 11, 13, 12, 150
```

Here, `150` is an outlier because it is far away from the other values.

## Why are Outliers Important?

Outliers can negatively affect some Machine Learning algorithms.

They can:

* Change the statistical properties of the data.
* Distort the mean and standard deviation.
* Affect model parameters.
* Pull regression lines away from the expected pattern.
* Reduce model performance.

Algorithms such as **Linear Regression, Logistic Regression, KNN, and some other distance/weight-based methods** can be sensitive to outliers.

Tree-based algorithms are generally less sensitive to outliers.

## Should We Always Remove Outliers?

**No.**

An outlier is not necessarily an error.

### Remove an outlier when:

* It is caused by a data-entry mistake.
* It is physically or logically impossible.
* It is clearly corrupted data.
* There is enough evidence that it does not represent the real problem.

### Keep an outlier when:

* It is a genuine observation.
* It represents an important rare event.
* It contains useful information for the problem.

For example, unusual credit-card transactions may actually be the most important observations when detecting fraud.

## How to Treat Outliers?

Common techniques include:

### 1. Trimming

Remove the outlier observations from the dataset.

**Advantage:** Simple and fast.

**Disadvantage:** You lose data, which can be problematic when there are many outliers.

### 2. Capping / Winsorization

Replace extreme values with predefined upper and lower limits.

Example:

```text
Lower limit = 5
Upper limit = 95
```

Values below `5` become `5`, and values above `95` become `95`.

### 3. Treat as Missing Values

Outliers can sometimes be converted to missing values and then handled using missing-value imputation techniques.

### 4. Binning / Discretization

Convert continuous numerical values into ranges or bins.

This can reduce the influence of extreme values.

## How to Detect Outliers?

### 1. Z-Score Method

Useful when the data is approximately normally distributed.

For a normal distribution:

* About **68%** of observations lie within ±1 standard deviation.
* About **95%** lie within ±2 standard deviations.
* About **99.7%** lie within ±3 standard deviations.

A common rule is:

```text
Z-score < -3  → Outlier
Z-score > +3  → Outlier
```

### 2. IQR Method

Useful for skewed/non-normal distributions.

Calculate:

```text
IQR = Q3 - Q1

Lower Limit = Q1 - 1.5 × IQR
Upper Limit = Q3 + 1.5 × IQR
```

Values outside these limits can be treated as outliers.

### 3. Percentile Method

Define lower and upper percentile limits.

For example:

```text
Below 1st percentile → Outlier
Above 99th percentile → Outlier
```

The exact percentiles can be selected according to the problem and dataset.

## Techniques Covered

This topic focuses on four important approaches:

1. **Z-Score**
2. **IQR / Box Plot**
3. **Percentile Method**
4. **Winsorization**


