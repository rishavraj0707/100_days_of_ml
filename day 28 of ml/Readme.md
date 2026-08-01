# Column Transformer in Scikit-learn

## Overview

Machine learning datasets often contain different types of features:

* Numerical Features (Age, Salary, Marks)
* Categorical Features (Gender, City, Department)

Since different preprocessing techniques are required for different feature types, **ColumnTransformer** allows us to apply separate transformations to different columns in a single pipeline.

---

# Why Do We Need ColumnTransformer?

Suppose we have the following dataset:

| Age | Salary | Gender | City    |
| --: | -----: | ------ | ------- |
|  25 |  50000 | Male   | Delhi   |
|  30 |  70000 | Female | Mumbai  |
|  35 |  90000 | Male   | Kolkata |

Here,

* **Age** and **Salary** should be standardized.
* **Gender** and **City** should be one-hot encoded.

Instead of preprocessing each column manually, ColumnTransformer performs all transformations together.

---

# Using ColumnTransformer

```python
from sklearn.compose import ColumnTransformer
from sklearn.preprocessing import StandardScaler, OneHotEncoder

preprocessor = ColumnTransformer(
    transformers=[
        ("num", StandardScaler(), ["Age", "Salary"]),
        ("cat", OneHotEncoder(), ["Gender", "City"])
    ]
)

X_train = preprocessor.fit_transform(X_train)
X_test = preprocessor.transform(X_test)
```

---

# How fit_transform() Works

```python
preprocessor.fit_transform(X_train)
```

This performs two operations:

1. Learns preprocessing parameters from the training data.
2. Applies those transformations to the training data.

For example,

* StandardScaler learns the mean and standard deviation.
* OneHotEncoder learns all unique categories.

Then it transforms the training dataset.

---

# How transform() Works

```python
preprocessor.transform(X_test)
```

This **does not learn anything** from the test data.

It only applies the transformations learned from the training data.

This prevents **data leakage**.

---

# What Happens Without ColumnTransformer?

Without ColumnTransformer, we need to preprocess every type of column separately.

### Step 1: Split Numerical and Categorical Columns

```python
num_cols = ["Age", "Salary"]
cat_cols = ["Gender", "City"]
```

### Step 2: Scale Numerical Features

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()

X_train_num = scaler.fit_transform(X_train[num_cols])
X_test_num = scaler.transform(X_test[num_cols])
```

### Step 3: Encode Categorical Features

```python
from sklearn.preprocessing import OneHotEncoder

encoder = OneHotEncoder(handle_unknown="ignore")

X_train_cat = encoder.fit_transform(X_train[cat_cols])
X_test_cat = encoder.transform(X_test[cat_cols])
```

### Step 4: Combine Everything

```python
from scipy.sparse import hstack

X_train_final = hstack((X_train_num, X_train_cat))
X_test_final = hstack((X_test_num, X_test_cat))
```

Now the numerical and categorical features are merged manually.

---

# Problems Without ColumnTransformer

* More code to write.
* Easy to make mistakes.
* Need to remember which transformer belongs to which columns.
* Manual concatenation of transformed features.
* Harder to maintain as the dataset grows.

---

# Advantages of ColumnTransformer

* Clean and readable code.
* Applies different preprocessing to different columns automatically.
* Prevents preprocessing mistakes.
* Easily integrates with Scikit-learn Pipelines.
* Makes machine learning workflows reproducible.
* Simplifies deployment because preprocessing is stored in one object.

---

# Workflow Comparison

### Without ColumnTransformer

```
Dataset
   │
   ├── Select Numerical Columns
   │       │
   │       └── StandardScaler
   │
   ├── Select Categorical Columns
   │       │
   │       └── OneHotEncoder
   │
   └── Manually Combine Features
            │
            ▼
      Train Model
```

---

### With ColumnTransformer

```
Dataset
      │
      ▼
ColumnTransformer
      │
      ├── StandardScaler → Numerical Columns
      └── OneHotEncoder → Categorical Columns
      │
      ▼
Processed Dataset
      │
      ▼
Train Model
```

---

# Key Takeaways

* Use **`fit_transform()`** on the training dataset.
* Use **`transform()`** on validation or test datasets.
* ColumnTransformer allows different preprocessing steps for different columns in one place.
* It eliminates manual preprocessing and makes machine learning pipelines cleaner, safer, and easier to maintain.
