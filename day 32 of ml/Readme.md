# Encoding Numerical Features

Numerical features can be transformed into a more useful representation using **encoding techniques**. Two common techniques are:

1. **Discretization (Binning)**
2. **Binarization**

---
## Google Colab code file - https://colab.research.google.com/drive/1yGjLYyA7ChdLoyAx7woob--_EcMRp103?usp=sharing
---

# 1. Discretization (Binning)

**Discretization** is the process of transforming a continuous numerical variable into a discrete variable by dividing its range into a set of contiguous intervals.

Each interval is called a **bin**.

For example, if age ranges from 0 to 100, we can divide it into:

| Age Range | Bin |
| --------- | --: |
| 0–20      |   1 |
| 21–40     |   2 |
| 41–60     |   3 |
| 61–80     |   4 |
| 81–100    |   5 |

Instead of using the original age value, we use the corresponding bin.

> **Discretization = Continuous values → Discrete intervals (bins)**

---

## Why Use Discretization?

### 1. Handle Outliers

Discretization can reduce the influence of extreme values.

For example:

```text
Age:
18, 20, 25, 30, 35, 40, 45, 50, 150
```

The value `150` is an extreme value. If we convert the values into bins, its influence can be reduced because it is represented by a bin rather than its exact numerical value.

### 2. Improve Value Distribution

Discretization can make the distribution of values easier to work with, especially when the original numerical feature has a skewed distribution.

---

# Types of Discretization

Discretization can be divided into:

```text
Discretization
│
├── Unsupervised
│   ├── Equal Width Binning (Uniform)
│   ├── Equal Frequency Binning (Quantile)
│   └── K-Means Binning
│
├── Supervised
│   └── Decision Tree Binning
│
└── Custom Binning
```

---

# 2. Unsupervised Discretization

In **unsupervised discretization**, the target/output variable is not considered while creating the bins.

Common methods are:

1. Equal Width Binning
2. Equal Frequency Binning
3. K-Means Binning

---

# 2.1 Equal Width Binning (Uniform)

In **equal width binning**, the entire range of values is divided into bins having approximately the same width.

### Formula

If:

* `Xmax` = maximum value
* `Xmin` = minimum value
* `k` = number of bins

Then:
``` 
Bin Width=(Xmax​−Xmin) / k​​
```
### Example

Suppose we have:

```text
Data = [10, 20, 30, 40, 50, 60, 70, 80, 90, 100]
```

We want **5 bins**.

```text
Minimum = 10
Maximum = 100
Number of bins = 5
```

Therefore:

[
\text{Bin Width} = \frac{100-10}{5}=18
]

The approximate intervals are:

```text
Bin 1: 10–28
Bin 2: 28–46
Bin 3: 46–64
Bin 4: 64–82
Bin 5: 82–100
```

### Benefits

* Helps reduce the effect of outliers.
* Easy to understand and implement.
* All bins have approximately the same numerical width.
* Useful when the numerical range itself is meaningful.

### Limitation

Equal width binning does **not** guarantee that each bin contains the same number of observations.

For example:

```text
Bin 1 → 50 values
Bin 2 → 20 values
Bin 3 → 5 values
Bin 4 → 3 values
Bin 5 → 2 values
```

This can happen when the data is highly skewed.

---

# 2.2 Equal Frequency Binning (Quantile)

In **equal frequency binning**, the data is divided so that each bin contains approximately the same number of observations.

It is also called **quantile binning**.

### Working

1. Sort the numerical values.
2. Decide the number of bins.
3. Divide the observations approximately equally among the bins.
4. Use the resulting ranges as the bins.

### Example

Consider:

```text
Data = [10, 20, 30, 40, 50, 60, 70, 80, 90, 100]
```

Suppose we want 5 bins.

There are 10 observations and 5 bins:

[
\frac{10}{5}=2
]

So each bin contains approximately 2 observations.

```text
Bin 1 → 10, 20
Bin 2 → 30, 40
Bin 3 → 50, 60
Bin 4 → 70, 80
Bin 5 → 90, 100
```

### Benefits

* Helps reduce the influence of outliers.
* Produces a more uniform number of observations across bins.
* Useful for skewed data.
* Can improve the spread of observations across bins.

### Limitation

The width of each bin is **not necessarily equal**.

For example:

```text
Bin 1 → 1–5
Bin 2 → 6–7
Bin 3 → 8–20
Bin 4 → 21–100
```

Each bin may contain a similar number of observations, but the numerical ranges are very different.

---

# 2.3 K-Means Binning

**K-Means binning** uses the K-Means clustering algorithm to divide numerical values into groups.

Instead of creating bins based only on fixed ranges or quantiles, K-Means groups values based on their similarity.

### Working

Suppose:

```text
Data = [1, 2, 3, 10, 11, 12, 50, 51, 52]
```

We want 3 bins.

K-Means can identify three natural groups:

```text
Cluster 1 → 1, 2, 3
Cluster 2 → 10, 11, 12
Cluster 3 → 50, 51, 52
```

The approximate cluster centers are:

```text
Cluster 1 center ≈ 2
Cluster 2 center ≈ 11
Cluster 3 center ≈ 51
```

These clusters can then be converted into bins.

### Working Steps

1. Select the number of bins/clusters `k`.
2. Initialize `k` cluster centers.
3. Assign each value to the nearest cluster center.
4. Calculate new cluster centers.
5. Repeat until the clusters stabilize.
6. Treat the resulting clusters as bins.

### Advantage

K-Means binning can discover **natural groups** in the data.

### Limitation

* Requires selecting `k`.
* Sensitive to the scale of the data.
* Can be affected by extreme outliers.
* More computationally expensive than simple binning methods.

---

# 3. Supervised Discretization

In **supervised discretization**, the target variable is considered while creating the bins.

One common technique is:

## Decision Tree Binning

A Decision Tree can find useful split points in a numerical feature based on the target variable.

### Example

Suppose we have:

| Age | Purchased |
| --: | --------: |
|  18 |        No |
|  22 |        No |
|  25 |        No |
|  35 |       Yes |
|  40 |       Yes |
|  45 |       Yes |
|  60 |        No |

A decision tree may find a useful split such as:

```text
Age <= 30
Age > 30
```

The numerical feature is therefore transformed into:

```text
Age <= 30 → Bin 1
Age > 30  → Bin 2
```

The important difference is that the target variable (`Purchased`) is used to determine the split.

### Advantage

* Creates bins that can be highly useful for prediction.
* Uses the relationship between the feature and target.

### Limitation

* Requires a target variable.
* Can overfit if not properly controlled.

---

# 4. Custom Binning

**Custom binning** means manually defining the bin boundaries based on domain knowledge or business requirements.

It is also called **domain-based binning**.

### Working

1. Understand the meaning of the feature.
2. Decide meaningful intervals.
3. Define the bin boundaries.
4. Assign each observation to the appropriate bin.

### Example: Age

Suppose we want to categorize people based on age:

```text
0–12   → Child
13–19  → Teenager
20–59  → Adult
60+    → Senior
```

For example:

| Age | Category |
| --: | -------- |
|  10 | Child    |
|  17 | Teenager |
|  25 | Adult    |
|  65 | Senior   |

This is custom binning because the intervals were defined manually based on domain knowledge.

### Another Example: Income

```text
Income < 30,000
        → Low

30,000–70,000
        → Medium

70,000–150,000
        → High

> 150,000
        → Very High
```

### Advantages

* Easy to understand.
* Business/domain knowledge can be incorporated.
* Produces meaningful categories.
* Useful when industry-specific thresholds already exist.

### Limitation

* Boundaries are subjective.
* Poorly selected bins can lose useful information.

---

# 5. Binarization

**Binarization** is the process of converting numerical values into **binary values**, usually:

```text
0 and 1
```

It is commonly used when we only need to know whether a value is below or above a particular threshold.

> **Binarization = Numerical value → 0 or 1**

---

## Working of Binarization

A threshold is selected.

For example:

```text
Threshold = 50
```

Then:

```text
Value < 50  → 0
Value >= 50 → 1
```

### Example

Original data:

```text
[10, 20, 40, 50, 60, 80]
```

Using threshold `50`:

| Value | Binary |
| ----: | -----: |
|    10 |      0 |
|    20 |      0 |
|    40 |      0 |
|    50 |      1 |
|    60 |      1 |
|    80 |      1 |

Therefore:

```text
[10, 20, 40, 50, 60, 80]

        ↓ Binarization

[0, 0, 0, 1, 1, 1]
```

---

# 6. Discretization vs Binarization

| Feature          | Discretization            | Binarization             |
| ---------------- | ------------------------- | ------------------------ |
| Output           | Multiple categories/bins  | Usually 0 and 1          |
| Number of groups | More than 2 possible      | Usually 2                |
| Example          | Age → Child/Adult/Senior  | Age ≥ 18 → 1             |
| Main idea        | Divide into intervals     | Apply a threshold        |
| Uses             | Grouping numerical values | Creating binary features |

### Example

For an `Age` feature:

**Discretization:**

```text
0–12   → Child
13–19  → Teenager
20–59  → Adult
60+    → Senior
```

**Binarization:**

```text
Age < 18  → 0
Age >= 18 → 1
```

---

# 7. Summary

```text
Numerical Feature Encoding
│
├── Discretization / Binning
│   │
│   ├── Unsupervised
│   │   ├── Equal Width
│   │   ├── Equal Frequency / Quantile
│   │   └── K-Means
│   │
│   ├── Supervised
│   │   └── Decision Tree
│   │
│   └── Custom
│
└── Binarization
    └── Threshold → 0 / 1
```

### Quick Comparison

| Method          | How bins are created           | Target required? |
| --------------- | ------------------------------ | ---------------- |
| Equal Width     | Equal numerical width          | No               |
| Equal Frequency | Equal number of observations   | No               |
| K-Means         | Similarity between values      | No               |
| Decision Tree   | Best splits based on target    | Yes              |
| Custom          | Manually defined boundaries    | No               |
| Binarization    | Threshold-based 0/1 conversion | No               |

---

## Key Points to Remember

* **Discretization** converts continuous numerical data into intervals.
* **Binning** is another name for discretization.
* **Equal Width** → same bin width.
* **Equal Frequency** → approximately same number of observations per bin.
* **K-Means Binning** → groups similar values using clustering.
* **Decision Tree Binning** → uses the target variable to find useful splits.
* **Custom Binning** → bins are created using domain/business knowledge.
* **Binarization** → converts values into binary values such as `0` and `1`.
* Discretization can reduce the effect of extreme values, but it also causes some loss of numerical information.
