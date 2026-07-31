# One-Hot Encoding

One-Hot Encoding converts categorical values into numerical columns containing **0** and **1**.

## Example

Original data:

| Color |
| ----- |
| Red   |
| Blue  |
| Green |
| Red   |

After One-Hot Encoding:

| Red | Blue | Green |
| --: | ---: | ----: |
|   1 |    0 |     0 |
|   0 |    1 |     0 |
|   0 |    0 |     1 |
|   1 |    0 |     0 |

---

## Dummy Variable Trap

After One-Hot Encoding, one category can be predicted from the remaining categories.

### Example

| Red | Blue | Green |
| --: | ---: | ----: |
|   1 |    0 |     0 |
|   0 |    1 |     0 |
|   0 |    0 |     1 |

If **Red = 0** and **Blue = 0**, then the value must be **Green = 1**.

This creates **multicollinearity**, known as the **Dummy Variable Trap**.

### Solution

Drop one dummy column.

Using **scikit-learn**:

```python
OneHotEncoder(drop='first')
```

Using **pandas**:

```python
pd.get_dummies(df, drop_first=True)
```

---

## What if we have many categories?

Sometimes a feature contains a large number of unique categories.

### Example

```text
Brand
├── Maruti
├── Hyundai
├── Honda
├── BMW
├── Audi
├── Toyota
├── Tata
├── Mahindra
├── ...
```

Applying One-Hot Encoding creates one new column for every category.

If there are **100 unique brands**, the encoder creates **100 columns**.

### Problems

* High memory usage
* More computation time
* Curse of dimensionality
* Model becomes slower

---

## Common Solutions

* Keep only the **top N most frequent categories**.
* Replace rare categories with **"Other"** or **"Uncommon"**.
* Use **Feature Hashing** for very high-cardinality features.
* Use **Target Encoding** or **Frequency Encoding** when appropriate.

---

## Summary

| Situation       | Recommended Approach                                      |
| --------------- | --------------------------------------------------------- |
| Few categories  | One-Hot Encoding                                          |
| Linear models   | Drop one dummy column (`drop='first'`)                    |
| Many categories | Group rare categories or use advanced encoding techniques |
