# Encoding Categorical Data

Categorical data contains values that represent categories instead of numbers.

### Google colab code file: https://colab.research.google.com/drive/1_7YLK3l_OiRA058hkHqmJxyXEl6Y0d9a?usp=sharing
## Types of Data

```text
Data
├── Numerical
└── Categorical
    ├── Nominal
    └── Ordinal
```

## Nominal Encoding

Nominal data has **no natural order**.

**Examples:**

* Red, Blue, Green
* India, USA, Japan

**Common encoding methods:**

* One-Hot Encoding
* Dummy Encoding

---

## Ordinal Encoding

Ordinal data has a **meaningful order**.

**Examples:**

* Small < Medium < Large
* Low < Medium < High

**Common encoding method:**

* Ordinal Encoding

---

## Label Encoding

Label Encoding converts each category into a unique integer.

**Example:**

| Category | Encoded Value |
| -------- | ------------: |
| Cat      |             0 |
| Dog      |             1 |
| Bird     |             2 |

> **Note:** Label Encoding is mainly used for the **target (y)** or for **ordinal features**. It is generally **not recommended for nominal features** because it introduces an artificial order.

---

## Summary

| Data Type        | Has Order? | Recommended Encoding |
| ---------------- | :--------: | -------------------- |
| Nominal          |    ❌ No    | One-Hot Encoding     |
| Ordinal          |    ✅ Yes   | Ordinal Encoding     |
| Target Label (y) |   Depends  | Label Encoding       |
