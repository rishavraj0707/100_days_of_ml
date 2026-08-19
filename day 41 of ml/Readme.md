# Outliers and Outlier Removal Techniques

A simple and clean guide to understanding **outliers**, why they matter, and common techniques for detecting and removing them.

## What is an Outlier?

An **outlier** is a data point that is significantly different from most other values in a dataset.

### Example

```text
10, 12, 11, 13, 12, 14, 100
                  ↑
               Outlier
```

Most values are between `10` and `14`, while `100` is very far away.

---

## Why Do Outliers Matter?

Outliers can affect:

* Mean and standard deviation
* Machine learning models
* Statistical analysis
* Data visualization
* Model accuracy

However, **not every outlier should be removed**.

An outlier can be:

1. A data-entry error
2. A measurement error
3. A rare but valid observation
4. An important event

Always understand the data before removing an outlier.

---

# Common Outlier Detection Techniques

## 1. IQR Method

The **Interquartile Range (IQR)** method is one of the most commonly used techniques.

### Formula

```text
IQR = Q3 - Q1
```

Where:

* `Q1` = 25th percentile
* `Q3` = 75th percentile

An observation is commonly considered an outlier if:

```text
Value < Q1 - 1.5 × IQR
```

or

```text
Value > Q3 + 1.5 × IQR
```

### Example

```text
Q1 = 20
Q3 = 40

IQR = 40 - 20
    = 20
```

Lower boundary:

```text
20 - (1.5 × 20) = -10
```

Upper boundary:

```text
40 + (1.5 × 20) = 70
```

Therefore, values below `-10` or above `70` are treated as outliers.

---

## 2. Z-Score Method

The **Z-score** measures how far a value is from the mean in terms of standard deviations.

### Formula

```text
Z = (X - Mean) / Standard Deviation
```

A common rule is:

```text
|Z| > 3
```

means the value may be an outlier.

### Example

```text
Mean = 50
Standard Deviation = 10
Value = 90

Z = (90 - 50) / 10
  = 4
```

Since `4 > 3`, the value can be considered an outlier.

---

## 3. Box Plot Method

A **box plot** provides a visual way to identify outliers.

```text
       ┌───────────────┐
───────┤      Box      ├───────
       └───────────────┘
                           •
                           ↑
                        Outlier
```

Points outside the normal whisker range are potential outliers.

---

# Outlier Removal Techniques

Once outliers are identified, there are several ways to handle them.

## 1. Remove the Rows

If the outlier is caused by an error or is not useful for the analysis, the entire row can be removed.

```text
Before:
10, 12, 11, 13, 100

After:
10, 12, 11, 13
```

**Use when:** the outlier is clearly invalid or represents a data error.

---

## 2. Capping / Winsorization

Instead of deleting the outlier, replace it with a boundary value.

```text
Before:
10, 12, 11, 13, 100

Upper limit = 20

After:
10, 12, 11, 13, 20
```

This keeps the observation while reducing its influence.

---

## 3. Transformation

A transformation can reduce the effect of extreme values.

For example, a **log transformation** can compress large values:

```text
Original:
10, 100, 1000, 10000

Log transformed:
1, 2, 3, 4
```

This is especially useful for heavily right-skewed data.

---

## 4. Replace with Median

For some datasets, an extreme value can be replaced with the **median**.

```text
Before:
10, 12, 13, 14, 100

Median = 13

After:
10, 12, 13, 14, 13
```

The median is less affected by extreme values than the mean.

---

# Which Technique Should You Use?

| Technique          | Best Use                                |
| ------------------ | --------------------------------------- |
| IQR                | General-purpose outlier detection       |
| Z-Score            | Approximately normally distributed data |
| Box Plot           | Quick visual detection                  |
| Remove Rows        | Clearly incorrect observations          |
| Capping            | Keep data but reduce extreme influence  |
| Transformation     | Skewed distributions                    |
| Median Replacement | Simple robust handling                  |

---

# Important Note

**Do not automatically remove every outlier.**

For example:

```text
Age: 25, 26, 27, 28, 100
```

If `100` is a valid age, it is not a data error.

But:

```text
Age: 25, 26, 27, 28, 250
```

`250` is likely an invalid value.

The correct approach is:

```text
Detect → Understand → Decide → Handle
```

---

# Simple Workflow

```text
          Dataset
             ↓
      Detect Outliers
             ↓
      Understand Cause
             ↓
    ┌────────┴────────┐
    ↓                 ↓
 Valid Outlier     Invalid Outlier
    ↓                 ↓
   Keep        Remove / Transform
```

## Summary

* An **outlier** is a value that is unusually different from other observations.
* Common detection methods include **IQR, Z-score, and box plots**.
* Common handling methods include **removal, capping, transformation, and median replacement**.
* Always investigate an outlier before removing it.
* A valid outlier may contain important information and should not necessarily be deleted.
