# Curse of Dimensionality

The **Curse of Dimensionality** refers to the problems that arise when the number of features (dimensions) in a dataset becomes very large. As dimensionality increases, machine learning models often require more computational resources and may experience reduced performance.

## Disadvantages

1. **Performance Decrease**

   * High-dimensional data can make models slower and less accurate.
   * It can also lead to overfitting because of the large number of features.

2. **Increased Computational Power**

   * More dimensions require more memory and processing power.
   * Training and prediction can become computationally expensive.

## Solution: Dimensionality Reduction

**Dimensionality reduction** reduces the number of features while preserving the most important information in the dataset.

### 1. Feature Selection

Feature selection chooses the most relevant features from the original dataset.

#### a. Forward Selection

* Starts with no features.
* Adds features one by one.
* At each step, the feature that improves model performance the most is selected.

#### b. Backward Elimination

* Starts with all available features.
* Removes the least useful feature at each step.
* Continues until only the most relevant features remain.

### 2. Feature Extraction

Feature extraction creates new, smaller sets of features by transforming the original features.

#### a. PCA — Principal Component Analysis

* Converts correlated features into a smaller number of uncorrelated components.
* Preserves as much variance as possible.
* Commonly used for visualization and preprocessing.

#### b. LDA — Linear Discriminant Analysis

* Reduces dimensions while considering class information.
* Tries to maximize the separation between different classes.
* Mainly used for supervised dimensionality reduction.

#### c. t-SNE — t-Distributed Stochastic Neighbor Embedding

* Primarily used to visualize high-dimensional data in 2D or 3D.
* Preserves local relationships between data points.
* Commonly used for exploring clusters and patterns.

## Summary

| Category           | Technique            | Main Idea                                |
| ------------------ | -------------------- | ---------------------------------------- |
| Feature Selection  | Forward Selection    | Add useful features step by step         |
| Feature Selection  | Backward Elimination | Remove less useful features step by step |
| Feature Extraction | PCA                  | Preserve maximum variance                |
| Feature Extraction | LDA                  | Maximize class separation                |
| Feature Extraction | t-SNE                | Visualize high-dimensional data          |

### Conclusion

The **Curse of Dimensionality** can negatively affect machine learning performance and increase computational requirements. **Dimensionality reduction**, through feature selection and feature extraction techniques such as **PCA, LDA, and t-SNE**, helps reduce these problems and makes high-dimensional datasets easier to work with.
