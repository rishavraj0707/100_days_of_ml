## Google Colab code file link : 
https://colab.research.google.com/drive/1y4icsdm4TQ3zxxQd1WwqWS9MpSeqFyy6?usp=sharing
---
# Handling Missing Values

### Techniques

1. **Remove rows**

   * Remove observations (rows) that contain missing values.
   * Example: **Complete-Case Analysis (CCA)** / **List-wise Deletion**

2. **Impute missing values**

   * **Univariate imputation** — uses information from the same variable.
   * **Multivariate imputation** — uses information from multiple variables to estimate the missing value.

---

## Complete-Case Analysis (CCA)

**Complete-Case Analysis (CCA)**, also called **list-wise deletion**, consists of discarding observations (rows) where values in **any of the variables (columns)** are missing.

In other words, CCA analyzes only those observations for which **complete information is available for all variables** used in the analysis.

### Assumption of CCA

CCA is most appropriate when the data are **Missing Completely At Random (MCAR)**.

**MCAR** means that the probability of a value being missing is unrelated to both the observed and unobserved data.

### Advantages of CCA

1. **Easy to implement** because no data imputation or manipulation is required.
2. **Preserves the variable distributions** when data are MCAR. The distributions in the reduced dataset should, on average, be similar to those in the original dataset.
3. **Simple to understand and apply.**

### Disadvantages of CCA

1. It can **exclude a large fraction of the original dataset** when missing data are abundant.
2. The excluded observations may contain **important information**, especially when the data are not MCAR.
3. **Loss of statistical power** can occur because the sample size is reduced.
4. If missing values occur in new/production data, the model may **not know how to handle missing values** unless missing-value handling is included in the preprocessing pipeline.

### When to Use CCA

CCA can be considered when:

1. The data are **MCAR**.
2. The amount of missing data is **small**, commonly around **less than 5%**.
3. Removing incomplete observations does not substantially reduce the sample size.
4. The missing observations are not systematically different from the complete observations.
