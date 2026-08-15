# Online Machine Learning

## 1. What is Online Learning?

**Online Learning** is a machine learning approach where the model is trained **incrementally** as new data arrives.

Instead of training the model on the entire dataset at once:

```text
New Data → Train/Update Model → New Data → Train/Update Model
```

The model continuously learns and improves from incoming data.

### Key Idea

* Data arrives continuously.
* Data is processed in small batches or individual samples.
* The model is updated after receiving new data.
* The updated model can continue making predictions in production.

---

## 2. How Online Learning Works

Basic workflow:

```text
Initial Data
     ↓
Train ML Model
     ↓
Deploy Model
     ↓
New Data Arrives
     ↓
Update/Train Model
     ↓
Improved Model
     ↓
New Data Arrives
     ↓
Continue...
```

This makes Online Learning suitable for systems where data keeps changing over time.

---

## 3. Batch Learning vs Online Learning

| Batch Learning                              | Online Learning                         |
| ------------------------------------------- | --------------------------------------- |
| Trains on a large dataset at once           | Trains incrementally                    |
| Model is usually retrained periodically     | Model can continuously update           |
| Requires more data/storage at training time | Can work with small batches             |
| Retraining can be expensive                 | Can reduce retraining cost              |
| Suitable for relatively stable data         | Suitable for continuously changing data |
| Simpler to implement                        | More difficult to monitor and maintain  |

---

## 4. Examples of Online Learning

Online Learning can be useful in applications where user behavior or incoming data changes continuously.

Examples:

* **Chatbots** — improve based on new interactions.
* **Recommendation systems** — recommendations can change based on user activity.
* **YouTube** — recommendations can adapt based on videos users watch and interact with.
* **Keyboard prediction** — suggestions can improve based on typing behavior.
* **E-commerce** — customer preferences and behavior change over time.

---

## 5. When Should We Use Online Learning?

Online Learning is useful when:

### 1. Data changes quickly

If the nature of the problem changes over time, the model needs to adapt.

Examples:

* Recommendation systems
* E-commerce platforms
* User behavior prediction

### 2. New data arrives continuously

If data is generated continuously, Online Learning allows the model to learn from the latest data.

### 3. Dataset is too large

If the complete dataset cannot fit into memory, it can be divided into smaller batches and processed sequentially.

### 4. Fast model updates are required

The model can be updated without completely retraining it from scratch.

---

## 6. Incremental Learning

Online Learning is also called **incremental learning** because the model learns gradually from new data.

For example, instead of:

```text
1 million records → Train Model
```

we can use:

```text
1000 records → Update Model
1000 records → Update Model
1000 records → Update Model
...
```

This is particularly useful when dealing with very large datasets.

---

## 7. Learning Rate

The **learning rate** determines how strongly new data changes the model.

* **High learning rate** → Model adapts quickly to new data but may forget older patterns.
* **Low learning rate** → Model changes slowly and retains more information from previous data.

The learning rate should be chosen carefully so that the model can:

> Learn new patterns while still remembering useful old patterns.

An inappropriate learning rate can cause the model to behave poorly.

---

## 8. Online Learning with Large Datasets

Suppose:

* Dataset size = **50 GB**
* Available memory = **8 GB**

The complete dataset cannot be loaded into memory at once.

Instead, divide it into smaller batches:

```text
50 GB Dataset
      ↓
Batch 1 → Train
Batch 2 → Update Model
Batch 3 → Update Model
Batch 4 → Update Model
...
```

This allows the model to process very large datasets incrementally.

---

## 9. Implementing Online Learning

Some machine learning algorithms support incremental training.

In **Scikit-learn**, algorithms such as `SGDClassifier` and `SGDRegressor` provide the `partial_fit()` method.

Example:

```python
model.partial_fit(X_batch, y_batch)
```

This allows training to continue from the existing model instead of starting from scratch.

---

## 10. Libraries

### River

**River** is a Python library specifically designed for **online machine learning** and learning from streaming data.

It is useful when data arrives continuously and the model needs to adapt in real time.

### Other Libraries

Some machine learning libraries also provide support for incremental learning through methods such as `partial_fit()`.

---

## 11. Problems with Online Learning

Online Learning provides flexibility, but it also introduces challenges.

### 1. Bad Incoming Data

If incorrect or biased data continuously enters the system, the model can learn those incorrect patterns.

```text
Bad Data
   ↓
Model Update
   ↓
Biased/Incorrect Model
```

### 2. Data Poisoning

An attacker could potentially send malicious or incorrect data to influence the model.

Therefore, incoming data needs to be monitored and validated.

### 3. Monitoring is Important

A production Online Learning system should have:

* Data validation
* Monitoring
* Anomaly detection
* Model performance monitoring
* A way to reject suspicious data
* A way to roll back to a previous model

---

## 12. Model Rollback

Since the model changes continuously, there should be a backup or previous stable version.

If something goes wrong:

```text
Current Model
     ↓
Problem Detected
     ↓
Rollback
     ↓
Previous Stable Model
```

This is important for production systems.

---

## 13. Online Learning vs Batch Learning

### Complexity

* **Batch Learning:** Generally simpler.
* **Online Learning:** More complex because continuous updates and monitoring are required.

### Computation

* **Batch Learning:** Requires larger computation during retraining.
* **Online Learning:** Spreads computation over time through incremental updates.

### Maintenance

* **Batch Learning:** Easier to implement and maintain.
* **Online Learning:** Requires continuous monitoring.

### Best Suited For

* **Batch Learning:** Stable problems where data does not change rapidly.
* **Online Learning:** Dynamic problems where data changes continuously.

---

