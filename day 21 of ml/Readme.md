# Seaborn Data Visualization

## Overview

This project demonstrates the basics of **data visualization using Seaborn**. Different types of plots are used to understand relationships, distributions, and patterns in datasets.

### Libraries Used

- **Pandas** – Data loading and manipulation.
- **Seaborn** – Statistical data visualization.
- **Matplotlib** – Plot customization and display.

---

## Datasets

The following datasets are used:

- **Tips** – Restaurant bill and tip information.
- **Titanic** – Passenger details and survival status.
- **Flights** – Monthly airline passenger data.
- **Iris** – Flower measurements for three species.

Example:

```python
tips = sns.load_dataset("tips")
iris = sns.load_dataset("iris")
```

---

# Visualization Types

## 1. Scatter Plot

**Purpose:** Shows the relationship between two numerical variables.

Useful for:
- Finding trends
- Detecting outliers
- Comparing categories using colors (`hue`)

Example:

```python
sns.scatterplot(data=tips, x="total_bill", y="tip", hue="sex")
```

---

## 2. Bar Plot

**Purpose:** Compares the average value of a numerical variable across different categories.

Example:

```python
sns.barplot(data=titanic, x="Pclass", y="Fare")
```

---

## 3. Box Plot

**Purpose:** Displays the distribution of data.

Shows:
- Median
- Quartiles
- Outliers

Example:

```python
sns.boxplot(data=titanic, x="Sex", y="Age", hue="Survived")
```

---

## 4. Distribution Plot

**Purpose:** Understands how numerical data is distributed.

Common plots:
- Histogram
- KDE (Kernel Density Estimate)

Example:

```python
sns.histplot(data=titanic, x="Age", kde=True)
```

---

## 5. Heatmap

**Purpose:** Displays values in a matrix using colors.

Often used to visualize:
- Correlation
- Frequency tables
- Pivot tables

Example:

```python
sns.heatmap(pd.crosstab(titanic["Pclass"], titanic["Survived"]))
```

---

## 6. Clustermap

**Purpose:** Similar to a heatmap but automatically groups similar rows and columns.

Example:

```python
sns.clustermap(pd.crosstab(titanic["Parch"], titanic["Survived"]))
```

---

## 7. Pair Plot

**Purpose:** Compares all numerical features in a dataset at once.

Useful for:
- Identifying relationships
- Understanding feature distributions

Example:

```python
sns.pairplot(iris, hue="species")
```

---

## 8. Line Plot

**Purpose:** Shows changes or trends over time.

Example:

```python
sns.lineplot(data=new, x="year", y="passengers")
```

---

# Important Concepts

- **hue** → Adds color based on categories.
- **style** → Changes marker style.
- **size** → Changes marker size.
- **palette** → Sets custom colors.
- **kde=True** → Adds a smooth density curve.
- **pivot_table()** → Converts data into matrix form for heatmaps.
- **groupby()** → Aggregates data before plotting.

Example:

```python
new = flights.groupby("year")["passengers"].sum().reset_index()
```

---
