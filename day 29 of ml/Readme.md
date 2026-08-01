# Scikit-learn Pipeline

## Overview

A **Pipeline** in Scikit-learn chains together multiple machine learning steps so that the output of one step becomes the input to the next step.

A pipeline typically includes:

1. Data preprocessing (e.g., scaling, encoding, imputation)
2. Model training (e.g., Linear Regression, Decision Tree, Random Forest)

Using a pipeline ensures that the same preprocessing is automatically applied to both the training and test datasets, reducing the chance of errors and preventing data leakage.

---

# Why Use a Pipeline?

Without a pipeline, you need to manually perform each preprocessing step before training the model.

With a pipeline:

* Code is cleaner and easier to read.
* The preprocessing sequence is executed automatically.
* The same transformations are applied consistently to training and testing data.
* It integrates seamlessly with cross-validation and hyperparameter tuning.

---

# Without Pipeline

### Step 1: Scale the Training Data

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()

X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)
```

### Step 2: Train the Model

```python
from sklearn.linear_model import LogisticRegression

model = LogisticRegression()

model.fit(X_train_scaled, y_train)
```

### Step 3: Make Predictions

```python
y_pred = model.predict(X_test_scaled)
```

### Workflow

```
Training Data
      │
      ▼
StandardScaler
      │
      ▼
Scaled Data
      │
      ▼
Logistic Regression
      │
      ▼
Predictions
```

---

# With Pipeline

```python
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import LogisticRegression

pipeline = Pipeline([
    ("scaler", StandardScaler()),
    ("classifier", LogisticRegression())
])

pipeline.fit(X_train, y_train)

y_pred = pipeline.predict(X_test)
```

Notice that the test data is **not manually scaled**. The pipeline automatically applies the same scaling learned from the training data before making predictions.

---

# Workflow

```
Training Data
      │
      ▼
Pipeline
      │
      ├── StandardScaler
      └── Logistic Regression
      │
      ▼
Trained Model
      │
      ▼
Predict(Test Data)
```

During prediction:

```
Test Data
      │
      ▼
StandardScaler (uses training statistics)
      │
      ▼
Logistic Regression
      │
      ▼
Predictions
```

---

# Advantages of Pipeline

* Reduces repetitive code.
* Automatically applies preprocessing during prediction.
* Prevents data leakage.
* Easier to maintain and debug.
* Works seamlessly with `GridSearchCV` and `cross_val_score`.
* Makes machine learning workflows more organized and reproducible.

---

# Pipeline vs Without Pipeline

| Without Pipeline                          | With Pipeline                      |
| ----------------------------------------- | ---------------------------------- |
| Manual preprocessing                      | Automatic preprocessing            |
| More lines of code                        | Cleaner and shorter code           |
| Higher chance of mistakes                 | Less error-prone                   |
| Need to remember every preprocessing step | Everything is stored in one object |
| Harder to reuse                           | Easy to reuse and deploy           |
| Separate scaler and model objects         | Single pipeline object             |

---

# Key Takeaways

* A **Pipeline** connects multiple machine learning steps into a single workflow.
* The output of one step becomes the input to the next step.
* Call `pipeline.fit(X_train, y_train)` to train the preprocessing steps and the model together.
* Call `pipeline.predict(X_test)` to automatically preprocess the test data and generate predictions.
* Pipelines make machine learning code cleaner, more reliable, and easier to deploy.
