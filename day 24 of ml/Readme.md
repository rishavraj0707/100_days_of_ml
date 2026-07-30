# Feature Scaling

### Google colab code file:  https://colab.research.google.com/drive/1VBx_Nt_xdvUWZZ9fNI1O9DnPKMrGi8ty?usp=sharing
## What is Feature Scaling?

Feature scaling is the process of transforming numerical features so they are on a similar scale without changing their underlying relationships. It helps machine learning algorithms learn more efficiently.

---

## Why Do We Need Feature Scaling?

Feature scaling is important because features with larger values can dominate features with smaller values, leading to biased model performance.

**Benefits:**
- Improves model performance.
- Speeds up model convergence.
- Prevents features with large values from dominating.
- Makes distance-based algorithms more accurate.

---

## Types of Feature Scaling

1. Standardization (Z-score Normalization)
2. Normalization (Min-Max Scaling)

---

# 1. Standardization (Z-score Normalization)

Standardization transforms data so that it has:
- Mean = 0
- Standard Deviation = 1

### Formula

\[
z = \frac{x - \mu}{\sigma}
\]

Where:

- **z** = Standardized value (Z-score)
- **x** = Original data point
- **μ** = Mean of the feature
- **σ** = Standard deviation of the feature

---

## Intuition Behind Standardization

Instead of measuring the actual value, standardization measures **how far a data point is from the mean** in terms of standard deviations.

Example:

Suppose the average height is **170 cm** with a standard deviation of **10 cm**.

Height = **180 cm**

```
z = (180 - 170) / 10
  = 1
```

This means the person's height is **1 standard deviation above the mean**.

---

## Impact of Outliers

Standardization uses the **mean** and **standard deviation**, both of which are affected by outliers.

As a result:
- Outliers can shift the mean.
- Outliers can increase the standard deviation.
- The scaled values may become less representative.

Although standardization is affected by outliers, it is generally **less sensitive than Min-Max Normalization**.

---

## When to Use Standardization

Use standardization when:

- Features approximately follow a normal (Gaussian) distribution.
- The algorithm assumes normally distributed data.
- Features contain moderate outliers.

It is commonly used with:

1. K-Means - Use the Euclidean distance measure.

2. K-Nearest-Neighbours - Measure the distances between pairs of samples and these distances are influenced by the measurement units

3. Principal Component Analysis (PCA) - Try to get the feature with maximum variance

4. Artificial Neural Network - Apply Gradient Descent

5. Gradient Descent - Theta calculation becomes faster after feature scaling and the learning rate in the update equation of Stochastic Gradient Descent is the same for every parameter

---

## Advantages

- Centers data around zero.
- Works well for many machine learning algorithms.
- Does not restrict values to a fixed range.

---

## Disadvantages

- Sensitive to extreme outliers.
- Scaled values are not bounded within a specific range.

---
