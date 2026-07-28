# Titanic Dataset Analysis Using Graphs
## Google colab code file - 

https://colab.research.google.com/drive/18-5LRqHf2xgIHMC7DzAqeS9lWOhKHCio?usp=sharing

**Dataset:** `train.csv` (Titanic Dataset)

## Libraries Used

- `pandas` – Data manipulation and analysis
- `matplotlib` – Data visualization
- `seaborn` – Statistical data visualization

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

---

# Types of Data

There are two main types of data in the Titanic dataset:

1. **Categorical Data**
2. **Numerical Data**

---

# 1. Categorical Data Analysis

Categorical variables represent groups or categories such as **Sex**, **Survived**, **Embarked**, and **Pclass**.

## A. Count Plot

A count plot shows the frequency of each category.

```python
sns.countplot(x='Sex', data=df)
plt.show()
```
---

## B. Pie Chart

A pie chart displays the percentage distribution of categories.

```python
df['Sex'].value_counts().plot(
    kind='pie',
    autopct='%1.1f%%',
    figsize=(5,5)
)
plt.ylabel('')
plt.show()
```

---

# 2. Numerical Data Analysis

Numerical variables include:

- Age
- Fare
- SibSp
- Parch

---

## A. Histogram

A histogram shows the distribution of numerical data.

```python
plt.hist(df['Age'], bins=20)
plt.xlabel("Age")
plt.ylabel("Frequency")
plt.show()
```

---

## B. Distribution Plot (Distplot)

Visualize the data distribution along with the density curve.

> **Note:** `sns.distplot()` is deprecated. Use `histplot()` or `displot()` instead.

```python
sns.histplot(df['Fare'], kde=True)
plt.show()
```

---

## C. Box Plot

A box plot helps detect outliers and understand data spread.

```python
sns.boxplot(x=df['Age'])
plt.show()
```

---

# Statistical Analysis

Use descriptive statistics to better understand the dataset.

## Mean

Average value of a numerical column.

```python
df['Age'].mean()
```

---

## Median

Middle value after sorting the data.

```python
df['Age'].median()
```

---

## Maximum Value

Largest value in the column.

```python
df['Age'].max()
```

---

## Minimum Value

Smallest value in the column.

```python
df['Age'].min()
```

---

## Skewness

Measures the symmetry of the data distribution.

```python
df['Age'].skew()
```

- **Skewness = 0** → Symmetric distribution
- **Skewness > 0** → Right-skewed (Positive skew)
- **Skewness < 0** → Left-skewed (Negative skew)

---

# Key Statistical Functions
- `mean()` 
- `median()` 
- `min()` 
- `max()` 
- `skew()` 
- `describe()` 

## Author 
*Rishav Raj*
