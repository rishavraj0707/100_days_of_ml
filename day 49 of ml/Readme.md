# Regression Metrics — MSE, MAE, RMSE, R² Score & Adjusted R² Score

Regression metrics are used to evaluate how well a regression model predicts continuous numerical values.

The main metrics covered here are:

* MAE — Mean Absolute Error
* MSE — Mean Squared Error
* RMSE — Root Mean Squared Error
* R² Score — R-Squared / Coefficient of Determination
* Adjusted R² Score

---

## 1. MAE — Mean Absolute Error

**MAE** measures the average absolute difference between the actual values and predicted values.

### Formula

$$
MAE = \frac{1}{n}\sum_{i=1}^{n}|y_i-\hat{y}_i|
$$

Where:

* \(y_i\) = actual value
* \(\hat{y}_i\) = predicted value
* \(n\) = number of observations

### Example

Actual values:

```text
[10, 20, 30]
```

Predicted values:

```text
[12, 18, 33]
```

Absolute errors:

```text
|10 - 12| = 2
|20 - 18| = 2
|30 - 33| = 3
```

Therefore:

$$
MAE = \frac{2+2+3}{3}=2.33
$$

### Advantages

* **Same unit as the target variable**

  * If the target is measured in dollars, MAE is also measured in dollars.
* **More robust to outliers than MSE and RMSE**

  * Large errors are not squared.

### Disadvantages

* **Not differentiable at zero**

  * The absolute-value function has a sharp point at zero.
* Gives the same linear penalty to errors regardless of their size.

### Scikit-learn

```python
from sklearn.metrics import mean_absolute_error

mae = mean_absolute_error(y_true, y_pred)
```

---

# 2. MSE — Mean Squared Error

**MSE** calculates the average of the squared differences between actual and predicted values.

### Formula

$$
MSE = \frac{1}{n}\sum_{i=1}^{n}(y_i-\hat{y}_i)^2
$$

### Example

Using:

```text
Actual:    [10, 20, 30]
Predicted: [12, 18, 33]
```

Squared errors:

```text
(10 - 12)² = 4
(20 - 18)² = 4
(30 - 33)² = 9
```

Therefore:

$$
MSE = \frac{4+4+9}{3}=5.67
$$

### Advantages

* **Useful as a loss function**

  * MSE is differentiable, making it convenient for optimization.
* **Strongly penalizes large errors**

  * Squaring the error gives more importance to large mistakes.

### Disadvantages

* **Not in the same unit as the target**

  * If the target is measured in dollars, MSE is measured in dollars².
* **Sensitive to outliers**

  * Large errors become very large after squaring.

### Scikit-learn

```python
from sklearn.metrics import mean_squared_error

mse = mean_squared_error(y_true, y_pred)
```

---

# 3. RMSE — Root Mean Squared Error

**RMSE** is the square root of MSE.

### Formula

$$
RMSE = \sqrt{\frac{1}{n}\sum_{i=1}^{n}(y_i-\hat{y}_i)^2}
$$

Or:

$$
RMSE = \sqrt{MSE}
$$

### Advantages

* **Same unit as the target variable**
* **Strongly penalizes large errors**
* Easier to interpret than MSE because it is expressed in the original unit.

### Disadvantages

* **Not robust to outliers**

  * Like MSE, errors are squared.
* Can be strongly affected by a few very large prediction errors.

### Scikit-learn

```python
from sklearn.metrics import root_mean_squared_error

rmse = root_mean_squared_error(y_true, y_pred)
```

For older versions of scikit-learn:

```python
from sklearn.metrics import mean_squared_error
import numpy as np

rmse = np.sqrt(mean_squared_error(y_true, y_pred))
```

---

# 4. R² Score — R-Squared

R² measures how well the regression model explains the variation in the target variable.

It is also called the **coefficient of determination**.

### Formula

$$
R^2 = 1-\frac{SS_{res}}{SS_{tot}}
$$

Where:

### \(SS_{res}\) — Residual Sum of Squares

$$
SS_{res} = \sum_{i=1}^{n}(y_i-\hat{y}_i)^2
$$

This represents the squared prediction errors from the regression model.

### \(SS_{tot}\) — Total Sum of Squares

$$
SS_{tot} = \sum_{i=1}^{n}(y_i-\bar{y})^2
$$

This represents the squared errors obtained by predicting the **mean of the target variable** for every observation.

Therefore:

$$
R^2 = 1-\frac{\sum(y_i-\hat{y}_i)^2}
{\sum(y_i-\bar{y})^2}
$$

---

## Interpretation of R²

### When R² = 1

The model explains **100% of the variation** in the target.

This represents a perfect fit.

```text
R² = 1
→ Perfect predictions
```

### When R² = 0

The model performs approximately as well as simply predicting the **mean of the target variable** for every observation.

```text
R² = 0
→ No improvement over the mean baseline
```

### When R² < 0

The model performs **worse than the mean baseline**.

A negative R² can occur, particularly when evaluating predictions on data that the model did not fit well.

```text
R² < 0
→ Model is worse than predicting the mean
```

---

## What does R² = 0.80 mean?

An R² score of **0.80** means that the regression model explains approximately **80% of the variance in the target variable relative to the mean baseline**.

The remaining **20%** is unexplained by the model under this metric.

> Important: R² = 0.80 does **not** mean that the model is 80% accurate.

R² is not an accuracy percentage.

---

## Advantages of R²

* Easy to interpret as a measure of explained variance.
* Useful for comparing regression models evaluated on the same target/dataset.
* Does not depend on the scale of the target in the same way as MAE, MSE, and RMSE.

## Disadvantages of R²

* A high R² does not necessarily mean the model is good in practical terms.
* R² does not tell you the size of prediction errors in the original units.
* R² can be negative.
* Adding more predictors can increase or leave R² unchanged, even when those predictors are not useful.
* It should not be interpreted as "percentage accuracy."

### Scikit-learn

```python
from sklearn.metrics import r2_score

r2 = r2_score(y_true, y_pred)
```

---

# 5. Adjusted R² Score

Adjusted R² is a modified version of R² that takes the **number of predictors/features** into account.

It is especially useful when comparing regression models with different numbers of features.

### Formula

$$
Adjusted\ R^2
=
1-
\frac{(1-R^2)(n-1)}
{n-k-1}
$$

Where:

* **R²** = R² score of the model
* **n** = number of observations/samples
* **k** = number of independent variables/features

---

## What happens when we add an irrelevant column?

Suppose we have:

```text
Model 1:
X1, X2
```

Then we add an irrelevant feature:

```text
Model 2:
X1, X2, X3
```

R² will generally **increase or remain the same**, because adding predictors cannot decrease the training R².

Adjusted R² is different.

If the newly added feature does not provide enough useful information, **Adjusted R² will decrease**.

This helps penalize unnecessary features.

---

## What happens when we add a relevant column?

If the new feature provides meaningful information and improves the model sufficiently:

```text
Adjusted R² ↑
```

If the feature provides little or no useful information:

```text
Adjusted R² ↓
```

Therefore, Adjusted R² helps determine whether adding another feature actually improves the model enough to justify its inclusion.

---

## R² vs Adjusted R²

| Metric      | Effect of adding features   | Penalizes unnecessary features? |
| ----------- | --------------------------- | ------------------------------- |
| R²          | Increases or stays the same | ❌ No                            |
| Adjusted R² | Can increase or decrease    | ✅ Yes                           |

### Important point

Adjusted R² is **not a feature-selection algorithm by itself**. It is a model-comparison metric that accounts for model complexity.

---

## Scikit-learn

Scikit-learn provides `r2_score`, but it does **not** have a separate standard `adjusted_r2_score` metric.

You can calculate Adjusted R² yourself:

```python
from sklearn.metrics import r2_score

r2 = r2_score(y_true, y_pred)

n = len(y_true)
k = X.shape[1]

adjusted_r2 = 1 - ((1 - r2) * (n - 1) / (n - k - 1))
```

---

# 6. Quick Comparison

| Metric      | Measures                                     | Same unit as target? | Sensitive to outliers? |
| ----------- | -------------------------------------------- | -------------------: | ---------------------: |
| MAE         | Average absolute error                       |                ✅ Yes |         Less sensitive |
| MSE         | Average squared error                        |                 ❌ No |       ✅ Very sensitive |
| RMSE        | Square root of MSE                           |                ✅ Yes |            ✅ Sensitive |
| R²          | Explained variance relative to mean baseline |              No unit |    Not an error metric |
| Adjusted R² | R² adjusted for number of predictors         |              No unit |    Not an error metric |

---

# 7. Which Metric Should You Use?

### Use MAE when:

* You want an easy-to-understand error in the original unit.
* You want less sensitivity to outliers.
* Every error should have a roughly linear penalty.

### Use MSE when:

* Large errors should be penalized heavily.
* You need a differentiable loss function.
* Outliers are important rather than something you want to ignore.

### Use RMSE when:

* You want the same unit as the target.
* Large errors should receive greater penalties.
* You want an interpretable version of MSE.

### Use R² when:

* You want to measure how much variation your model explains relative to a mean baseline.
* You want a scale-free goodness-of-fit measure.

### Use Adjusted R² when:

* Comparing regression models with different numbers of predictors.
* You want to account for model complexity.
* You want to see whether adding features actually improves the model enough.

---

# 8. Scikit-learn Metrics Summary

```python
from sklearn.metrics import (
    mean_absolute_error,
    mean_squared_error,
    root_mean_squared_error,
    r2_score
)

mae = mean_absolute_error(y_true, y_pred)

mse = mean_squared_error(y_true, y_pred)

rmse = root_mean_squared_error(y_true, y_pred)

r2 = r2_score(y_true, y_pred)
```

For compatibility with older scikit-learn versions:

```python
import numpy as np
from sklearn.metrics import mean_squared_error

rmse = np.sqrt(mean_squared_error(y_true, y_pred))
```

---

# 9. One-Line Revision

```text
MAE  → Average absolute error → Same unit → Less affected by outliers

MSE  → Average squared error → Squared unit → Highly affected by outliers

RMSE → √MSE → Same unit → Highly affected by outliers

R²   → Variance explained relative to mean baseline

Adjusted R² → R² + penalty for unnecessary predictors
```

---

## Conclusion

For regression problems, no single metric is always the best.

* **MAE** is useful when you want a simple and relatively outlier-robust error measure.
* **MSE** is useful when large errors should be penalized heavily and when a differentiable loss is needed.
* **RMSE** provides the benefits of squared-error penalization while returning to the target's original unit.
* **R²** measures how much variation the model explains compared with a mean-prediction baseline.
* **Adjusted R²** accounts for the number of predictors and is useful when comparing models with different feature counts.

A good regression evaluation often uses **more than one metric** rather than relying on R² alone.
