# Multiple Linear Regression

Multiple Linear Regression is a supervised machine learning algorithm used to predict a **continuous dependent variable** using **two or more independent variables**.

---

## Formula

The general formula for Multiple Linear Regression is:

$$
\hat{y}=b_0+b_1x_1+b_2x_2+b_3x_3+\cdots+b_kx_k
$$

Where:

$$\ 
\hat{y}\ :predicted value of the dependent variable
$$ 

$$ 
b_0\ :intercept
$$  

$$ 
b_1,b_2,\ldots,b_k\ = coefficients
$$

$$ 
x_1,x_2,\ldots,x_k\ = independent variables/features 
$$

$$
k\ = number of independent variables
$$

The statistical form can also be written as:

$$
y=\beta_0+\beta_1X_1+\beta_2X_2+\cdots+\beta_kX_k+\epsilon
$$

Where:

* \(y\) = actual dependent variable
* \(\beta_0\) = intercept
* \(\beta_i\) = coefficient of the $$\(i^{th}\) feature
* \(X_i\) = independent variable
* \(\epsilon\) = error/residual

---

## Example

Suppose we want to predict a person's **salary** using:

* Experience
* Education
* Age

The model can be represented as:

$$
\hat{salary}
=
b_0+
b_1(experience)+
b_2(education)+
b_3(age)
$$

For example:

$$
\hat{salary}
=
30000+
5000(experience)+
3000(education)+
500(age)
$$

The coefficients are learned by the model from the training data.

---

## Objective

The main objective is to find the coefficients that minimize the prediction error.

Usually, **Ordinary Least Squares (OLS)** is used.

The objective is to minimize the Sum of Squared Errors:

$$
SSE=\sum_{i=1}^{n}(y_i-\hat{y}_i)^2
$$

Therefore, the model tries to find the best-fitting hyperplane that minimizes the squared residuals.

---

## Simple Linear vs Multiple Linear Regression

### Simple Linear Regression

Uses **one independent variable**:

$$
\hat{y}=b_0+b_1x_1
$$

Example:

```text
Salary = b0 + b1 × Experience
```

### Multiple Linear Regression

Uses **two or more independent variables**:

$$
\hat{y}=b_0+b_1x_1+b_2x_2+\cdots+b_kx_k
$$

Example:

```text
Salary = b0
       + b1 × Experience
       + b2 × Education
       + b3 × Age
```

---

## Important Assumptions

Multiple Linear Regression commonly assumes:

1. **Linearity**

   * The relationship between predictors and the target is approximately linear.

2. **Independence**

   * Observations/errors should be independent.

3. **Homoscedasticity**

   * The variance of residuals should be approximately constant.

4. **Normality of residuals**

   * Residuals are approximately normally distributed, particularly for classical statistical inference.

5. **No severe multicollinearity**

   * Independent variables should not be highly correlated with each other.

---

## Advantages

* Simple and easy to interpret.
* Can use multiple features to make predictions.
* Computationally efficient.
* Coefficients provide information about the relationship between features and the target.
* Works well when the relationship is approximately linear.

---

## Disadvantages

* Sensitive to outliers.
* Sensitive to multicollinearity.
* Assumes a linear relationship.
* Performance can be poor when the true relationship is highly nonlinear.
* Irrelevant features can reduce model usefulness and interpretability.

---
