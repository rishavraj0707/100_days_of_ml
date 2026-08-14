# AI vs Machine Learning vs Deep Learning

## Artificial Intelligence (AI)

**Artificial Intelligence (AI)** is the broader concept of making machines capable of performing tasks that normally require human intelligence.

Human intelligence includes:

* Problem solving
* Decision making
* Reasoning
* Creativity
* Learning
* Understanding language

AI aims to build systems that can perform some of these tasks.

## Machine Learning (ML)

**Machine Learning is a subset of AI.**

Instead of explicitly programming rules for every situation, ML systems learn patterns from data.

### Example: Dog Classification

Instead of writing rules for every possible dog breed, we provide the model with many images of dogs and non-dogs.

The model learns patterns from the data and can then classify new images.

```text
Data → ML Algorithm → Model → Prediction
```

## Deep Learning (DL)

**Deep Learning is a subset of Machine Learning.**

Deep Learning uses **neural networks with multiple layers** to automatically learn useful features from data.

This is especially useful for complex problems such as:

* Image classification
* Speech recognition
* Natural Language Processing
* Computer vision

## ML vs Deep Learning

The main difference is **feature extraction**.

### Machine Learning

In traditional ML, we often need to identify and provide useful features to the model.

```text
Raw Data
   ↓
Feature Engineering
   ↓
ML Model
   ↓
Prediction
```

### Deep Learning

Deep Learning can automatically learn useful features from raw data.

```text
Raw Data
   ↓
Neural Network
   ↓
Automatically Learned Features
   ↓
Prediction
```

## Why Deep Learning?

Deep Learning is particularly useful when:

* The problem is highly complex.
* Large amounts of data are available.
* Useful features are difficult to define manually.
* Traditional ML is not producing good results.

As more data is provided, deep learning models can often improve their performance.

## Limitations

Deep Learning is **not always better than Machine Learning**.

It generally requires:

* More data
* More computational resources
* More training time

For smaller datasets or simpler problems, traditional Machine Learning can be a better choice.

## Relationship

```text
Artificial Intelligence
        │
        └── Machine Learning
                │
                └── Deep Learning
```

---
