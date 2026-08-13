# Handle Date and Time Dataset

## Overview

This project demonstrates how to handle and process date and time data using Python.

## Libraries Used

```python
import pandas as pd
import numpy as np
from datetime import datetime
```

## Main Tasks

* Load the dataset using Pandas.
* Convert date/time columns into a standard format.
* Handle missing or invalid date/time values.
* Extract useful information such as year, month, day, and time.
* Perform date and time calculations.

## Example

```python
import pandas as pd

df = pd.read_csv("dataset.csv")

df["date"] = pd.to_datetime(df["date"], errors="coerce")

print(df.head())
```
