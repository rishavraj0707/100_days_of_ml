## Google Colab code file: 
https://colab.research.google.com/drive/1MJGxOj8gHub7HcRfq7QLUS4KDUPPCtSO?usp=sharing  


# Iterative Imputer (MICE)

A simple explanation of how **Iterative Imputer / MICE (Multiple Imputation by Chained Equations)** works.

## What is MICE?

MICE is a method for filling in missing values in a dataset.

Instead of replacing missing values with a simple value like the **mean** or **median**, MICE uses the other columns to make a better prediction.

For example:

| Age | Income | Score |
| --: | -----: | ----: |
|  25 |  30000 |    70 |
|  30 |      ? |    80 |
|  40 |  50000 |    90 |

MICE can use **Age** and **Score** to estimate the missing **Income**.

---

## How MICE Works

MICE works **iteratively**, meaning it repeatedly improves the missing-value estimates.

### Step 1 — Fill missing values temporarily

First, missing values are given simple initial values, such as the mean.

```text
Income:
30000
35000  ← temporary value
50000
```

### Step 2 — Choose one column with missing values

Suppose `Income` has missing values.

MICE treats `Income` as the target and uses the other columns as predictors.

```text
Age + Score → predict Income
```

### Step 3 — Predict the missing values

A model is trained using the rows where `Income` is known.

It then predicts the missing `Income` values.

```text
Age = 30, Score = 80
        ↓
   Prediction Model
        ↓
Income = 40000
```

### Step 4 — Move to the next column

MICE repeats the same process for another column with missing values.

```text
Income → Age
Age → Score
Score → Income
```

Each variable is predicted using the other variables.

### Step 5 — Repeat the process

MICE goes through the columns multiple times.

Each iteration uses the **updated values from the previous iteration**.

```text
Initial values
      ↓
Iteration 1
      ↓
Iteration 2
      ↓
Iteration 3
      ↓
   Final values
```

The estimates usually become more stable after several iterations.

---

## Why is it called "Chained Equations"?

Because each variable is modeled using the other variables, creating a chain:

```text
X1 → X2
X2 → X3
X3 → X4
X4 → X1
```

The process keeps cycling through these equations.

---

## Simple Example

Imagine this dataset:

```text
Age    Income    Score
25     30000     70
30     ?         80
40     50000     90
```

MICE might do:

```text
1. Temporarily fill Income = 40000

2. Learn:
   Age + Score → Income

3. Predict missing Income:
   Income = 39000

4. Use the updated Income values in the next models.

5. Repeat for several iterations.
```

The final value is an estimate based on relationships between the variables rather than just a single overall average.

---

## MICE vs Mean Imputation

### Mean Imputation

```text
Missing value → Mean
```

Simple, but it ignores relationships between columns.

### MICE

```text
Other variables
       ↓
Prediction model
       ↓
Missing value
```

MICE can preserve relationships between variables better than simple mean imputation.

---

## Key Idea

> **MICE fills missing values by repeatedly predicting each incomplete variable from the other variables.**

In short:

```text
Missing Data
     ↓
Initial Values
     ↓
Predict Missing Values
     ↓
Update Values
     ↓
Repeat
     ↓
Completed Dataset
```

## Summary

* **MICE** = Multiple Imputation by Chained Equations.
* It is used to handle missing data.
* Each incomplete column is predicted using other columns.
* The process is repeated for multiple iterations.
* The estimates improve as the algorithm cycles through the variables.
* It is generally more informative than simply replacing missing values with the mean.
