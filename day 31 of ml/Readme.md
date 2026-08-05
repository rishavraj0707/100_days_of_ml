# Power Transformers

Power transformations are statistical techniques used to make data more normally distributed, reduce skewness, and stabilize variance. Two of the most commonly used power transformations are the **Box-Cox Transformation** and the **Yeo-Johnson Transformation**.

---

# 1. Box-Cox Transformation

The **Box-Cox transformation** is designed for **strictly positive** data (values must be greater than 0). It helps improve normality and is commonly used before applying statistical models that assume normally distributed data.

## Formula

For a variable \(x > 0\):

\[
y(\lambda)=
\begin{cases}
\dfrac{x^\lambda-1}{\lambda}, & \lambda \neq 0 \\
\ln(x), & \lambda = 0
\end{cases}
\]

Where:

- **\(x\)** = Original value
- **\(\lambda\)** = Transformation parameter

## Choosing the Lambda (λ)

- The exponent **λ (lambda)** is not fixed.
- It is typically searched over a range such as **-5 to 5**.
- For each candidate value of λ, the transformed data is evaluated.
- The **optimal λ** is the one that produces data closest to a **normal distribution**, usually determined using **maximum likelihood estimation (MLE)**.

## Advantages

- Reduces skewness
- Stabilizes variance
- Improves normality
- Can improve the performance of machine learning and statistical models

## Limitation

- Cannot be applied to **zero or negative values**.

---

# 2. Yeo-Johnson Transformation

The **Yeo-Johnson transformation** is an extension of the Box-Cox transformation that can be applied to **positive, zero, and negative values**.

It provides similar benefits while removing the restriction that data must be strictly positive.

## Formula

For a variable \(x\):

\[
y(\lambda)=
\begin{cases}
\dfrac{(x+1)^\lambda-1}{\lambda}, & x \ge 0,\ \lambda \neq 0 \\[8pt]
\ln(x+1), & x \ge 0,\ \lambda = 0 \\[8pt]
-\dfrac{(-x+1)^{2-\lambda}-1}{2-\lambda}, & x < 0,\ \lambda \neq 2 \\[8pt]
-\ln(-x+1), & x < 0,\ \lambda = 2
\end{cases}
\]

## Advantages

- Works with **negative values**
- Handles **zero values**
- Reduces skewness
- Stabilizes variance
- Often preferred when datasets contain both positive and negative numbers

---

# Comparison

| Feature | Box-Cox | Yeo-Johnson |
|----------|----------|-------------|
| Positive values | ✅ | ✅ |
| Zero values | ❌ | ✅ |
| Negative values | ❌ | ✅ |
| Improves normality | ✅ | ✅ |
| Stabilizes variance | ✅ | ✅ |
| Requires strictly positive data | ✅ | ❌ |

---

# When to Use

### Use **Box-Cox** when:

- All data values are positive.
- You want maximum normalization for positive-only data.

### Use **Yeo-Johnson** when:

- Your dataset contains negative values.
- Your dataset contains zeros.
- You need a transformation without removing or shifting the data.

---

# Summary

- **Box-Cox** is suitable for **strictly positive** data.
- **Yeo-Johnson** extends Box-Cox to support **positive, zero, and negative** values.
- Both transformations search for an optimal **λ (lambda)** value that makes the transformed data as close to a **normal distribution** as possible.
- These transformations are widely used in **machine learning**, **statistics**, and **data preprocessing**.