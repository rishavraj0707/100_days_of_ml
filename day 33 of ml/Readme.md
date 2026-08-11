# Mixed Data

## Introduction

**Mixed data** refers to a dataset that contains different types of values or variables, such as:

- Numerical data
- Categorical data
- Missing values

In Machine Learning and Data Science, datasets commonly contain a combination of these data types. Before using such data for analysis or model training, we need to identify and preprocess each type correctly.

---
## Google Colab code file - https://colab.research.google.com/drive/1y9tddyzU7dUQaOnsHouoqguxCh-UXH6A?usp=sharing
---


## Example 1: Mixed Data in a Single Column

Consider a dataset containing information about passengers:

### Original Data

| Cabin |
| ----- |
| B5    |
| C23   |
| D41   |

The `Cabin` column contains **mixed data** because each value consists of:

1. A **categorical** part — `B`, `C`, `D`
2. A **numerical** part — `5`, `23`, `41`

We can split this single column into two separate columns.

### Separated Data

| Category | Number |
| -------- | ------ |
| B        | 5      |
| C        | 23     |
| D        | 41     |

Here:

- `Cabin` is **mixed data**.
- The mixed data can be separated into two types:
  1. **Categorical data** — `B`, `C`, `D`
  2. **Numerical data** — `5`, `23`, `41`

---

## Example 2: Mixed Data in a Column

Consider a column containing both numerical and categorical values:

### Original Data

| No. of Family |
| ------------- |
| 7             |
| 8             |
| 3             |
| 2             |
| A             |
| 1             |
| B             |

This column contains **mixed data** because it includes both numerical values and categorical values.

We can separate them into two columns.

### Separated Data

| Number | Categorical |
| ------ | ----------- |
| 7      | NaN         |
| 8      | NaN         |
| 3      | NaN         |
| 2      | NaN         |
| NaN    | A           |
| 1      | NaN         |
| NaN    | B           |

Here:

- Numerical values are stored in the **Number** column.
- Alphabetical values are stored in the **Categorical** column.
- `NaN` represents a **missing value**.

---

## Key Point

Mixed data occurs when a single column contains **different types of information**.

To make the data easier to analyze and use in Machine Learning, we can separate the values into appropriate **numerical** and **categorical** columns.

---

## Summary

| Type | Example | Description |
| ---- | ------- | ----------- |
| Numerical | `5`, `23`, `41` | Represents numbers or quantities |
| Categorical | `A`, `B`, `C` | Represents categories or groups |
| Mixed | `B5`, `C23`, `D41` | Contains both categorical and numerical information |
| Missing | `NaN` | Represents a missing value |

### Important

**Mixed Data → Separate the data → Numerical + Categorical → Handle missing values → Ready for analysis or Machine Learning**
