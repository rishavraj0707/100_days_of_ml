## Google colab code file: 
day_38_of_ml_random_sample_imputation : https://colab.research.google.com/drive/1_rj1Xx1yiKJ1qFppBZvm2WLEhSXkpFhd?usp=sharing  
day_38_of_ml_missing_indicator : https://colab.research.google.com/drive/1OAtX6c1a7RzGgVGj4eJNwpu0-n6KapPo?usp=sharing  
day_38_of_ml_automatically_select_imputer_parameters : https://colab.research.google.com/drive/1yqTyJJJi-t1WN_0XCtul92tV4o0IKX_M?usp=sharing  


# Missing Data Imputation Techniques

This README explains three useful approaches for handling missing values in machine learning datasets:

1. Random Imputation
2. Missing Indicator
3. Automatically selecting the best imputation strategy using GridSearchCV

---

## 1. Random Imputation

**Random Imputation** replaces each missing value with a randomly selected value from the observed values of the same variable.

### How it works

Suppose we have:

```text
Age = [20, 25, NA, 30, NA, 40]
```

The observed values are:

```text
[20, 25, 30, 40]
```

For each `NA`, we randomly select one of these observed values.

For example:

```text
Age = [20, 25, 30, 30, 40, 40]
```

The exact values selected will vary because the replacement is random.

### Why does random imputation preserve variance?

Mean imputation tends to reduce variance because all missing observations are replaced by the same value—the mean.

For example:

```text
Original:
10, 20, 30, 40, 50

Mean = 30
```

If the missing values are replaced by `30`, several observations become identical. This reduces the spread of the data and therefore reduces variance.

Random imputation instead samples values from the **original observed distribution**. Therefore, the imputed values have approximately the same variability as the observed values.

In other words:

> Random imputation adds values with a distribution similar to the original variable instead of putting all missing observations at one fixed point.

Because the values are sampled randomly, the variance is not guaranteed to be exactly identical in every sample, but it is generally much better preserved than with mean/median imputation.

### Advantages

* Simple and easy to understand
* Preserves the approximate distribution of the variable
* Preserves variance better than mean/median imputation
* Can work well when the missingness mechanism is appropriate

### Disadvantages

* The result is random unless a random seed is fixed
* Different runs can produce different datasets
* It may introduce additional sampling noise
* It can be **memory-heavy during deployment**

### Why is it memory-heavy during deployment?

To randomly select values for a new missing observation, we need access to the values that were observed during training.

For example, if the training data contains:

```text
Age = [20, 25, 30, 35, 40, ...]
```

and a new observation arrives with:

```text
Age = NA
```

the imputer needs to randomly select a value from the training values.

Therefore, the original observed values (or an equivalent stored representation) need to be retained.

This can increase memory requirements, especially for:

* Large datasets
* High-cardinality variables
* Many columns
* Production systems processing large numbers of features

---

# 2. Missing Indicator

A **Missing Indicator** creates an additional binary feature that records whether the original value was missing.

For example:

```text
Age = [20, NA, 30, NA, 40]
```

After creating a missing indicator:

```text
Age          Age_missing
20           false
NA           true
30           false
NA           true
40           false
```

The missing values in `Age` can then be imputed using another strategy such as mean or median imputation.

For example:

```text
Age          Age_missing
20           false
30           true
30           false
30           true
40           false
```

Here:

* `Age` contains the imputed value.
* `Age_missing` tells the model whether the original value was missing.

### Why is this useful?

Sometimes **the fact that a value is missing contains information**.

For example, suppose income is missing more frequently for a particular type of customer. Even after imputing the missing income, the model may benefit from knowing that the original income was missing.

The missing indicator allows the model to learn this relationship.

### Benefits

* Preserves information about missingness
* Easy to implement
* Can improve model performance when missingness itself is predictive
* Works well with many machine learning algorithms
* Can be combined with mean, median, or other imputation methods

### Disadvantage

It adds an additional feature for every variable for which a missing indicator is created.

---

# 3. Automatically Selecting the Imputation Strategy

There is no single imputation technique that is guaranteed to work best for every dataset.

Possible strategies include:

* Mean imputation
* Median imputation
* Most-frequent imputation
* Constant-value imputation
* Random imputation
* Missing indicator + imputation

Instead of manually choosing one, we can use **GridSearchCV** to evaluate different strategies.

## Using GridSearchCV

The basic idea is:

```text
Dataset
   ↓
Pipeline
   ↓
Different imputation strategies
   ↓
Train model
   ↓
Cross-validation
   ↓
Compare performance
   ↓
Select best strategy
```

For example, we could test:

```text
Strategy 1 → Mean Imputation
Strategy 2 → Median Imputation
Strategy 3 → Most Frequent Imputation
```

GridSearchCV evaluates each configuration using cross-validation and selects the configuration that gives the best validation score.

### Why use a Pipeline?

The imputation step should be inside the machine learning pipeline.

For example:

```python
Pipeline([
    ("imputer", SimpleImputer()),
    ("model", LogisticRegression())
])
```

Then GridSearchCV can test different imputation parameters:

```python
param_grid = {
    "imputer__strategy": ["mean", "median", "most_frequent"]
}
```

This is important because the imputer should be fitted **only on the training portion of each cross-validation fold**.

Otherwise, information from the validation data can leak into the training process.

---

# Summary

| Technique         | Main Benefit                                    | Main Limitation                                     |
| ----------------- | ----------------------------------------------- | --------------------------------------------------- |
| Random Imputation | Preserves approximate distribution and variance | Requires access to observed training values; random |
| Missing Indicator | Captures information contained in missingness   | Adds extra features                                 |
| GridSearchCV      | Automatically finds a good imputation strategy  | Computationally more expensive                      |

## Key Takeaways

### Random Imputation

> Randomly samples observed values to replace missing values, helping preserve the original distribution and variance better than fixed-value imputation.

### Missing Indicator

> Adds a feature that tells the model whether the original observation was missing.

### GridSearchCV

> Allows us to compare different imputation strategies systematically and select the one that performs best according to cross-validation.

## Benefits of Imputation in General

* Simple to implement
* Allows models that cannot directly handle `NaN` values to use the dataset
* Can preserve useful information when the appropriate strategy is selected
* Can be combined with missing indicators
* Can be optimized using cross-validation
