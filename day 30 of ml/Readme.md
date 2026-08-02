# Mathematical Transformations in Data Preprocessing

Mathematical transformations are used to reduce skewness, stabilize variance, and make data closer to a normal distribution. This helps many machine learning algorithms perform better.

---

# Common Mathematical Transformations

## 1. Log Transformation

### Formula
```python
import numpy as np

X_log = np.log(X)
```

If the dataset contains zeros:

```python
X_log = np.log1p(X)    # log(1 + X)
```

### What happens after Log Transformation?

- Reduces right skewness.
- Compresses large values.
- Makes the distribution more symmetric.
- Reduces the effect of outliers.

### Best for

- Right-skewed data
- Positive values only

---

## 2. Reciprocal Transformation

### Formula

```python
X_reciprocal = 1 / X
```

### What happens?

- Strongly compresses large values.
- Makes extremely large observations much smaller.
- Can reduce right skewness.

### Best for

- Highly right-skewed data
- Positive values only
- Avoid if zeros exist.

---

## 3. Power Transformation

Power transformations apply different mathematical powers to reduce skewness.

Examples:

### Square Root

```python
X_sqrt = np.sqrt(X)
```

### Cube Root

```python
X_cbrt = np.cbrt(X)
```

### Square

```python
X_square = X**2
```

### Cube

```python
X_cube = X**3
```

### What happens?

- Square Root → reduces moderate right skewness.
- Cube Root → works with positive and negative values.
- Square/Cube → useful for left-skewed data.

---

# Function Transformations Summary

| Transformation | Effect |
|---------------|--------|
| Log | Compresses large values, reduces right skew |
| Log1p | Same as log but works with zeros |
| Reciprocal | Strongly compresses large values |
| Square Root | Mild reduction of right skew |
| Cube Root | Handles positive & negative values |
| Square | Reduces left skew |
| Cube | Reduces left skew |

---

# How to Check Whether Data is Normal

## 1. Distribution Plot

```python
import seaborn as sns

sns.histplot(df["feature"], kde=True)
```

or

```python
sns.distplot(df["feature"])
```

> **Note:** `distplot()` is deprecated. Use `histplot()` or `displot()` instead.

---

## 2. Skewness

```python
df["feature"].skew()
```

or

```python
import pandas as pd

pd.Series(df["feature"]).skew()
```

### Interpretation

| Skewness | Meaning |
|----------|---------|
| 0 | Perfectly Normal |
| -0.5 to 0.5 | Approximately Normal |
| > 0.5 | Right Skewed |
| < -0.5 | Left Skewed |

---

## 3. QQ Plot

```python
import scipy.stats as stats
import matplotlib.pyplot as plt

stats.probplot(df["feature"], dist="norm", plot=plt)
plt.show()
```

### Interpretation

- Points follow straight line → Data is approximately normal.
- Points deviate from line → Data is not normal.

---

# Which Transformation Should Be Applied?

## Right-Skewed Data (Positive Skew)

Use:

- Log Transformation
- Log1p Transformation
- Square Root Transformation
- Box-Cox Transformation (Positive values only)
- Yeo-Johnson Transformation (Positive & Negative values)

---

## Left-Skewed Data (Negative Skew)

Use:

- Square Transformation
- Cube Transformation
- Exponential Transformation

---

# np.log() vs np.log1p()

## np.log()

Computes:

```python
log(x)
```

Example

```python
np.log(10)
```

Output

```python
2.302585
```

### Limitation

```python
np.log(0)
```

Output

```
-inf
```

Cannot handle zero values.

---

## np.log1p()

Computes:

```python
log(1 + x)
```

Example

```python
np.log1p(0)
```

Output

```python
0.0
```

Example

```python
np.log1p(9)
```

Output

```python
2.302585
```

### Advantage

Safely handles zero values.

---

# Summary Table

| Transformation | Used For | Handles Zero? |
|---------------|----------|---------------|
| np.log() | Right-skewed data | ❌ No |
| np.log1p() | Right-skewed data with zeros | ✅ Yes |
| Square Root | Moderate right skew | ✅ Yes |
| Cube Root | Positive & negative values | ✅ Yes |
| Reciprocal | Highly right-skewed data | ❌ No |
| Box-Cox | Positive data | ❌ No |
| Yeo-Johnson | Positive & negative data | ✅ Yes |

---

# Quick Revision

### Right-Skewed Data

✅ Log Transformation

✅ Log1p

✅ Square Root

✅ Box-Cox

---

### Left-Skewed Data

✅ Square

✅ Cube

✅ Exponential

---

### Check Normality

- Histogram (`sns.histplot()`)
- KDE Plot
- Skewness (`.skew()`)
- QQ Plot

---

# Key Takeaways

- Transformations help make data closer to a normal distribution.
- Log transformation is the most common method for right-skewed data.
- Use `np.log1p()` when your data contains zeros.
- Always check the distribution before and after transformation using histogram, skewness, and QQ plot.