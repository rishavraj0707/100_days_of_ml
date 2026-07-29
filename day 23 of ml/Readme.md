# What is feature engineering 
Feature engineering is the process of creating, transforming, selecting, and extracting features from raw data to improve the performance of machine learning models.

## Types of Feature Engineering

Feature Engineering
│
├── 1. Feature Transformation
│   ├── Missing Value Imputation
│   ├── Handling Categorical Features
│   ├── Outlier Detection
│   └── Feature Scaling
├── 2. Feature Construction
├── 3. Feature Selection
└── 4. Feature Extraction

## 1. Feature Transformation

Modifying existing features into a format that is more suitable for machine learning models without changing their underlying meaning.

### a. Missing Value Imputation: 
Replacing missing data with estimated values (e.g., mean, median, or most frequent value) so the dataset is complete.
### b. Handling Categorical Features: 
Converting categorical (text) data into numerical form using techniques like label encoding or one-hot encoding.
### c. Outlier Detection: 
Identifying and handling unusually large or small values that may negatively affect model performance.
### d. Feature Scaling: 
Rescaling numerical features to a common range or distribution so that no feature dominates because of its magnitude.

## 2. Feature Construction

Creating new features from existing features to provide additional information that helps the model learn patterns more effectively.

## 3. Feature Selection

Selecting the most relevant features while removing irrelevant or redundant ones to improve model performance, reduce overfitting, and decrease training time.

## 4. Feature Extraction

Transforming high-dimensional data into a smaller set of informative features while preserving the most important information (e.g., using PCA).

## Summary table

| Technique              | Purpose                                                |
| ---------------------- | ------------------------------------------------------ |
| Feature Transformation | Modify existing features into a suitable format        |
| Feature Construction   | Create new features from existing ones                 |
| Feature Selection      | Keep only the most relevant features                   |
| Feature Extraction     | Reduce feature dimensions while preserving information |

## Add examples 

| Topic                    | Example                                             |
| ------------------------ | --------------------------------------------------- |
| Missing Value Imputation | Fill missing age with the median age                |
| Categorical Features     | Gender → Male=0, Female=1                           |
| Outlier Detection        | Remove salaries greater than ₹10,000,000            |
| Feature Scaling          | Scale age from 0–100 to 0–1                         |
| Feature Construction     | BMI = Weight / Height²                              |
| Feature Selection        | Remove duplicate or highly correlated features      |
| Feature Extraction       | PCA reduces 100 features to 10 principal components |
