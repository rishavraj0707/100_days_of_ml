## Google colab code file:
day_36_of_ml_end_of_distribution_imputation : https://colab.research.google.com/drive/1fe_IwHEZ-2yf4RmEaaac0DJRasB73iRL?usp=sharing  
day_36_of_ml_arbitrary_value_imputation : https://colab.research.google.com/drive/1Td71fth__Mnw1IYLkYBxvHJPlrDy-cox?usp=sharing  
day_36_of_ml_mean_median_imputation : https://colab.research.google.com/drive/1IDyv6NTUjYKlwi9N-NNTLfCLVPMwkq7g?usp=sharing  
---

# Handling Missing Numerical Values

Missing numerical values can be handled mainly using **univariate imputation** and **multivariate imputation**.

## 1. Univariate Imputation

### Definition

**Univariate imputation** is a missing-value technique in which the missing values of a variable are replaced using information from **the same variable**.

### Types of Univariate Imputation

1. Mean / Median Imputation
2. Arbitrary Value Imputation
3. End of Distribution Imputation
4. Random Imputation

---

## A. Mean / Median Imputation

### Definition

Mean/median imputation replaces missing numerical values with a statistical value calculated from the **non-missing observations of the same variable**.

* **Mean imputation:** Replace missing values with the mean.
* **Median imputation:** Replace missing values with the median.

### Working

Suppose a variable contains:

`10, 20, 30, NaN, 40, 50`

Mean:

`(10 + 20 + 30 + 40 + 50) / 5 = 30`

The missing value is replaced by `30`.

For median imputation, the sorted values are:

`10, 20, 30, 40, 50`

Median = `30`

So the missing value is replaced by `30`.

### When to Use Mean

Mean imputation is generally suitable when:

* The variable is approximately **normally distributed**.
* The data has **few missing values**.
* The missingness is approximately **MCAR (Missing Completely At Random)**.
* There are no significant outliers.

### When to Use Median

Median imputation is generally preferred when:

* The data is **skewed**.
* The variable contains **outliers**.
* There are relatively few missing values.
* The missingness is approximately **MCAR**.

### Benefits

* Simple to understand and implement.
* Fast computationally.
* Useful when the percentage of missing values is small, commonly **less than 5%**.

### Disadvantages

* Can change the **shape of the distribution**.
* Mean imputation is sensitive to **outliers**.
* Can reduce the natural variability of the data.
* Can change **covariance and correlation** between variables.
* Can create an artificial concentration of observations around the mean or median.

---

# B. Arbitrary Value Imputation

### Definition

**Arbitrary value imputation** replaces missing values with a predefined arbitrary value, such as:

* `0`
* `-999`
* `999`
* Another value outside the normal range of the variable

Example:

`10, 20, NaN, 30, 40`

If the chosen arbitrary value is `-999`:

`10, 20, -999, 30, 40`

### When to Use

It can be useful when the missingness itself may contain information, particularly when the data is suspected to be **MNAR (Missing Not At Random)**.

The chosen value should be clearly distinguishable from normal observations.

### Benefits

* Simple and easy to implement.
* Preserves an explicit signal that a value was missing.
* Can be useful when missingness itself is informative.

### Disadvantages

* Can significantly change the **distribution shape**.
* Can affect **covariance and correlation**.
* An inappropriate arbitrary value can introduce bias.
* The model may interpret the arbitrary value as a genuine numerical measurement.

---

# C. End of Distribution Imputation

### Definition

**End of distribution imputation** replaces missing values with a value located at the **extreme end of the observed distribution**.

It is particularly useful when we want to create a value that is clearly different from the usual observations while still being related to the variable's distribution.

## For Normally Distributed Data

For the lower end:

**Mean − 3 × Standard Deviation**

For the upper end:

**Mean + 3 × Standard Deviation**

Therefore:

```text
Lower extreme = Mean - 3σ
Upper extreme = Mean + 3σ
```

where:

* `Mean` = average of the variable
* `σ` = standard deviation

## For Skewed Data

For skewed distributions, the **IQR (Interquartile Range) proximity rule** can be used.

### Formula

```text
IQR = Q3 - Q1
```

Lower extreme:

```text
Q1 - 1.5 × IQR
```

Upper extreme:

```text
Q3 + 1.5 × IQR
```

Where:

* **Q1** = 25th percentile
* **Q3** = 75th percentile
* **IQR** = Q3 − Q1

### Example

Suppose:

* Q1 = 20
* Q3 = 50

Then:

```text
IQR = 50 - 20 = 30
```

Lower extreme:

```text
20 - (1.5 × 30) = -25
```

Upper extreme:

```text
50 + (1.5 × 30) = 95
```

A missing value could therefore be replaced by an appropriate extreme value, depending on the chosen strategy.

### Benefits

* Simple to implement.
* Can preserve a distinction between observed and originally missing values.
* Can be useful when missingness itself is informative.
* Uses information from the distribution rather than an unrelated constant.

### Disadvantages

* Can create artificial outliers.
* Can change the distribution shape.
* Can affect covariance and correlation.
* May negatively affect some machine-learning algorithms.
* The choice of extreme value can be subjective.

### When to Use

End-of-distribution imputation can be considered when:

* The missingness may be **MNAR (Missing Not At Random)**.
* A clear separation between missing and observed values is desirable.
* The variable's distribution is sufficiently understood.

---

# Summary

| Method              | Main Idea                                       | Suitable Situation                            |
| ------------------- | ----------------------------------------------- | --------------------------------------------- |
| Mean                | Replace with mean                               | Approximately normal data, few missing values |
| Median              | Replace with median                             | Skewed data or outliers                       |
| Arbitrary Value     | Replace with a fixed value                      | Missingness may be informative / MNAR         |
| End of Distribution | Replace with an extreme distribution value      | Missingness may be informative / MNAR         |
| Random              | Replace using randomly selected observed values | Preserve variability/distribution             |
| KNN                 | Use similar observations                        | Relationships among variables are useful      |
| Iterative           | Predict missing values using other variables    | Strong relationships among variables          |

## Important Terms

### MCAR — Missing Completely At Random

The probability that a value is missing is unrelated to both observed and unobserved data.

### MAR — Missing At Random

The probability of missingness can depend on other **observed variables**.

### MNAR — Missing Not At Random

The probability of missingness depends on the missing value itself or on information that is not observed.

> **Note:** The choice of imputation method should depend on the missingness mechanism, amount of missing data, distribution of the variable, outliers, and relationships between variables. There is no universal rule that one method is always best.
