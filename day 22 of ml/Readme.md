# Automated Exploratory Data Analysis (EDA) with YData Profiling

## Overview

This project demonstrates how to generate an **automated Exploratory Data Analysis (EDA) report** using the **YData Profiling** library. Instead of manually checking each column, the library creates a comprehensive HTML report containing statistics, distributions, missing values, correlations, and data quality insights.

---

## Libraries Used

- **Pandas** – Load and manipulate datasets.
- **YData Profiling** – Generate an automated EDA report.

```python
import pandas as pd
from ydata_profiling import ProfileReport
```

---

## Dataset

The Titanic training dataset is loaded using Pandas.

Example:

```python
df = pd.read_csv("/content/train.csv")
df.head()
```

---

## Installing the Library

If YData Profiling is not installed, install it using pip.

```python
!pip install ydata-profiling
```

> **Note:** `ydata-profiling` is the updated version of the older `pandas-profiling` package.

---

## Creating the Profile Report

Create a profiling report for the dataset.

```python
prof = ProfileReport(df)
```

The report automatically analyzes:
- Dataset overview
- Column statistics
- Missing values
- Duplicate records
- Correlations
- Data types
- Distributions
- Alerts and warnings

---

## Exporting the Report

Save the report as an HTML file.

```python
prof.to_file("output.html")
```

The generated `output.html` can be opened in any web browser to explore the dataset interactively.

---

## Key Features

- Generates a complete EDA report with one command.
- Detects missing values and duplicate rows.
- Provides summary statistics for numerical and categorical features.
- Shows feature correlations.
- Highlights potential data quality issues.
- Creates interactive visualizations.

---

## Advantages

- Saves time during data exploration.
- No need to write multiple analysis commands manually.
- Helps identify data quality issues quickly.
- Useful before data preprocessing and machine learning.

---
