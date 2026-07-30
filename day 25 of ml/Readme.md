# Feature Scaling

### Google colab code file: https://colab.research.google.com/drive/1qKjj19R0cp-FapWvJ7HasQeLcxUDIWlY?usp=sharing
---

## Normalization

**Normalization** is a feature scaling technique that transforms numerical features to a common scale without distorting the relationships between their values. It is commonly used when features have different ranges.

### Types of Normalization

1. Min-Max Scaling
2. Mean Normalization
3. Max Absolute Scaling
4. Robust Scaling

---

## 1. Min-Max Scaling

Scales the data to a fixed range, usually **[0, 1]**.

### Formula

\[
X_{scaled} = \frac{X - X_{min}}{X_{max} - X_{min}}
\]

**When to use:**
- Data has no significant outliers.
- Values need to be within a fixed range (e.g., Neural Networks).

---

## 2. Mean Normalization

Centers the data around the mean and scales it using the data range.

### Formula

\[
X_{scaled} = \frac{X - \mu}{X_{max} - X_{min}}
\]

Where:
- **μ** = Mean of the feature

**When to use:**
- When you want the data centered around zero while considering the range.

---

## 3. Max Absolute Scaling

Scales each value by dividing it by the maximum absolute value.

### Formula

\[
X_{scaled} = \frac{X}{|X|_{max}}
\]

**When to use:**
- Data is already centered around zero.
- Sparse datasets (e.g., text data).

---

## 4. Robust Scaling

Uses the median and Interquartile Range (IQR), making it robust to outliers.

### Formula

\[
X_{scaled} = \frac{X - \text{Median}}{Q_3 - Q_1}
\]

Where:
- **Median** = Middle value
- **IQR** = \(Q_3 - Q_1\)

**When to use:**
- Dataset contains many outliers.

---

# Normalization vs Standardization

| Normalization | Standardization |
|--------------|-----------------|
| Scales data to a fixed range (usually 0–1). | Centers data around mean 0 with standard deviation 1. |
| Sensitive to outliers. | Less sensitive to outliers than Min-Max Scaling. |
| Best for bounded data and Neural Networks. | Best for normally distributed data and many ML algorithms. |

---

## Is Feature Scaling Required?

**Not always.** First, determine whether your machine learning algorithm requires feature scaling.

### Algorithms that require feature scaling

- K-Nearest Neighbours (KNN)
- K-Means Clustering
- Support Vector Machine (SVM)
- Logistic Regression
- Linear Regression (especially with Gradient Descent)
- Principal Component Analysis (PCA)
- Neural Networks

### Algorithms that generally do not require feature scaling

- Decision Tree
- Random Forest
- XGBoost
- LightGBM
- CatBoost

> **Rule of thumb:** First check whether feature scaling is needed for your algorithm. If it is, then choose the appropriate scaling technique based on your data (presence of outliers, data distribution, and algorithm requirements).
