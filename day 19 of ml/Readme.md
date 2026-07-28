# Understanding the Data

Before performing any analysis, it's important to understand the dataset. Below are some common questions and the corresponding Pandas functions used to answer them.

## 1. How big is the dataset?

Get the number of rows and columns:

```python
df.shape
```

## 2. What does the data look like?

View a few sample records:

```python
df.sample()   # Random sample of rows
df.head()     # First 5 rows
df.tail()     # Last 5 rows
```

## 3. What are the data types of the columns?

Display column names, data types, and non-null counts:

```python
df.info()
```

## 4. Are there any missing values?

Count missing values in each column:

```python
df.isnull().sum()
```

## 5. What are the statistical summaries of the data?

Generate descriptive statistics for numerical columns:

```python
df.describe()
```

## 6. Are there any duplicate rows?

Count the number of duplicate records:

```python
df.duplicated().sum()
```

## 7. What is the correlation between numerical columns?

Calculate the correlation matrix:

```python
df.corr(numeric_only=True)
```

### Author 
*Rishav Raj*
