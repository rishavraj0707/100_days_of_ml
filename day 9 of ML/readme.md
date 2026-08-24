MACHINE LEARNING DEVELOPMENT LIFE CYCLE (MLDLC)

Definition:
Machine Learning Development Life Cycle (MLDLC) is a systematic process
of developing, training, evaluating, deploying, testing and maintaining
a machine learning based software product.

It is similar to SDLC (Software Development Life Cycle), but MLDLC
specifically focuses on data, machine learning models and their
continuous improvement.


MAIN STEPS OF MLDLC:

1. Problem Framing
2. Data Gathering
3. Data Processing / Preprocessing
4. Exploratory Data Analysis (EDA)
5. Feature Engineering and Feature Selection
6. Model Training
7. Model Evaluation
8. Model Selection and Hyperparameter Tuning
9. Ensemble Learning
10. Model Deployment
11. Testing
12. Monitoring, Optimization and Retraining


--------------------------------------------------
1. PROBLEM FRAMING
--------------------------------------------------

Problem Framing is the first step of MLDLC.

In this step, we clearly define the problem that needs to be solved
using Machine Learning.

We decide:

- What exactly is the problem?
- What is the expected output?
- Who are the users/customers?
- Is it a classification or regression problem?
- What type of ML approach is required?
- What data will be required?
- Where will the data come from?
- What resources and team are required?
- What will be the approximate cost?

Example:

For a diabetes prediction system:

Input:
Age, Glucose, BMI, Blood Pressure, etc.

Output:
Diabetic / Non-diabetic

This is a Binary Classification problem.


--------------------------------------------------
2. DATA GATHERING
--------------------------------------------------

Machine Learning requires data.

Data can be collected from different sources such as:

- CSV files
- Excel files
- Databases
- APIs
- Web Scraping
- Data Warehouses
- Cloud Storage
- Sensors
- Existing company datasets

Example:

A diabetes dataset may contain:

Age
Gender
Glucose
Blood Pressure
BMI
Insulin
Family History
Outcome


API:

API stands for Application Programming Interface.

Sometimes data is obtained through an API.

Example:

Python Program → API → Data


Web Scraping:

Web Scraping is the process of extracting data from websites
using programming techniques.

Example:

Python → Website → Extract Data → Dataset


Data Warehouse:

A data warehouse stores data collected from different sources.
It can then be used for analysis and Machine Learning.


--------------------------------------------------
3. DATA PROCESSING / PREPROCESSING
--------------------------------------------------

Raw data is usually not directly suitable for Machine Learning.

It may contain:

- Missing values
- Duplicate values
- Outliers
- Incorrect values
- Categorical data
- Different formats
- Different scales
- Inconsistent data

Therefore, data preprocessing is performed.

Common preprocessing operations:

1. Removing duplicates
2. Handling missing values
3. Handling outliers
4. Encoding categorical variables
5. Feature scaling
6. Data transformation


Example:

Removing duplicates:

df.drop_duplicates()


Handling missing values:

df.dropna()


Missing values can also be replaced using:

- Mean
- Median
- Mode
- Other imputation techniques


Feature Scaling:

Suppose:

Age = 20–80

Income = 20,000–2,00,000

These features have very different scales.

Scaling techniques include:

- Standardization
- Normalization

Example:

StandardScaler()


Goal of preprocessing:

Convert raw and dirty data into a clean format that can
be properly used by Machine Learning algorithms.


--------------------------------------------------
4. EXPLORATORY DATA ANALYSIS (EDA)
--------------------------------------------------

EDA stands for Exploratory Data Analysis.

EDA is the process of understanding and analyzing the dataset
before building the Machine Learning model.

We study:

- Data distribution
- Relationships between features
- Correlations
- Outliers
- Patterns
- Trends
- Class imbalance
- Relationship between input and output


Types of EDA:

1. Univariate Analysis
2. Bivariate Analysis
3. Multivariate Analysis


Univariate Analysis:

Analysis of one variable at a time.

Example:

Age distribution


Bivariate Analysis:

Analysis of two variables.

Example:

Glucose vs Outcome


Multivariate Analysis:

Analysis of multiple variables.

Example:

Glucose + BMI + Age → Outcome


Common visualization techniques:

- Histogram
- Bar Chart
- Scatter Plot
- Box Plot
- Heatmap


Why is EDA important?

EDA helps us understand:

"What is actually present in our data?"

Example:

If a diabetes dataset contains:

Non-Diabetic = 92%
Diabetic = 8%

then the dataset is imbalanced.

Therefore, simply using accuracy may not be sufficient
for evaluating the model.


--------------------------------------------------
5. FEATURE ENGINEERING
--------------------------------------------------

Feature Engineering means creating new useful features from
existing features.

Example:

Suppose we have:

Number of Rooms
Number of Bathrooms

We can create a new meaningful feature such as:

Rooms_per_Bathroom


Another example:

Date of Birth → Age


The goal of Feature Engineering is to provide the Machine
Learning model with more useful representations of the data.


--------------------------------------------------
6. FEATURE SELECTION
--------------------------------------------------

Feature Selection means selecting the most useful features
from the available features and removing irrelevant features.

Example:

Suppose a dataset has 100 features.

After analysis, only 20 features are useful.

We can select those 20 features and remove the remaining ones.


Advantages:

- Reduces training time
- Reduces model complexity
- Can reduce overfitting
- Improves interpretability
- Removes irrelevant information


Difference:

Feature Engineering:
Creates or transforms features.

Feature Selection:
Selects useful existing features.


--------------------------------------------------
7. MODEL TRAINING
--------------------------------------------------

After preprocessing and feature preparation, the data is used
to train Machine Learning models.

Different algorithms can be tested.

Classification algorithms:

- Logistic Regression
- Decision Tree
- Random Forest
- SVM
- KNN
- XGBoost

Regression algorithms:

- Linear Regression
- Decision Tree Regressor
- Random Forest Regressor
- XGBoost Regressor


Why try multiple algorithms?

Because no single Machine Learning algorithm performs best
on every dataset.

Therefore, different suitable algorithms can be trained
and compared.


--------------------------------------------------
8. MODEL EVALUATION
--------------------------------------------------

Model Evaluation determines how well a trained model performs.

Different evaluation metrics are used depending on the problem.


Classification Metrics:

- Accuracy
- Precision
- Recall
- F1-Score
- ROC-AUC
- Confusion Matrix


Regression Metrics:

- MAE
- MSE
- RMSE
- R²


Important:

Accuracy should not always be used as the only metric.

For example:

Non-Diabetic = 92%
Diabetic = 8%

A model predicting everyone as Non-Diabetic can achieve
approximately 92% accuracy but will fail to detect diabetic cases.

Therefore, for imbalanced datasets, metrics such as:

- Precision
- Recall
- F1-Score
- PR-AUC
- Confusion Matrix

can provide more useful information.


--------------------------------------------------
9. MODEL SELECTION
--------------------------------------------------

After evaluating different models, the best suitable model
is selected.

Example:

Model                 Accuracy    Recall    F1-Score

Logistic Regression      91%        78%       80%
Random Forest            93%        82%       84%
XGBoost                  94%        86%       87%


The model should not necessarily be selected only based
on accuracy.

The selection depends on the requirements of the problem.

For example, in disease detection, Recall may be very important
because missing a positive patient can be costly.


--------------------------------------------------
10. HYPERPARAMETER TUNING
--------------------------------------------------

Hyperparameters are settings that are chosen before/during
model training and are not directly learned from the training data.

Examples for Random Forest:

- n_estimators
- max_depth
- min_samples_split

Examples for XGBoost:

- learning_rate
- max_depth
- n_estimators


Common hyperparameter tuning techniques:

- Grid Search
- Random Search
- Bayesian Optimization


Example:

GridSearchCV()


Goal:

Find suitable hyperparameter values that improve model
performance while avoiding overfitting.


--------------------------------------------------
11. ENSEMBLE LEARNING
--------------------------------------------------

Ensemble Learning combines multiple Machine Learning models
to create a stronger model.

Major techniques:

1. Bagging
2. Boosting
3. Stacking


Bagging:

Multiple models are trained on different samples and their
predictions are combined.

Example:

Random Forest


Boosting:

Models are trained sequentially, where later models focus
more on previous errors.

Examples:

- AdaBoost
- Gradient Boosting
- XGBoost


Stacking:

Predictions from multiple models are combined and given
to another model called the meta-model.

Example:

Random Forest ──┐
                ├──→ Logistic Regression → Final Prediction
XGBoost ────────┘


--------------------------------------------------
12. MODEL DEPLOYMENT
--------------------------------------------------

After training and selecting the model, it needs to be made
available to users.

A Machine Learning model can be deployed in:

- Website
- Mobile Application
- Desktop Application
- Backend Server
- Cloud Application


Typical Architecture:

User
  ↓
Website / Mobile App
  ↓
API
  ↓
Backend
  ↓
ML Model
  ↓
Prediction
  ↓
User


Example:

User enters:

Age = 45
Glucose = 160
BMI = 31
...

        ↓

       API

        ↓

   ML Model

        ↓

"Diabetic"


The trained model can be saved and loaded using tools such as:

- joblib
- pickle


--------------------------------------------------
13. TESTING
--------------------------------------------------

After deployment, the ML system must be tested.

Testing checks whether the complete system works correctly.

It can identify:

- Prediction errors
- Software bugs
- Data problems
- Performance issues
- User interface problems
- Model problems


Beta Testing:

The product is initially provided to a limited group of users.

Their feedback is collected to identify problems before
releasing the system to all users.


If problems are found, we may return to earlier stages.

Example:

Testing
   ↓
Problem Found
   ↓
Data Problem?
   ↓
Data Processing


or:

Testing
   ↓
Poor Model Performance
   ↓
Feature Engineering
   ↓
Model Training


Therefore, MLDLC is an iterative process.


--------------------------------------------------
14. MONITORING, OPTIMIZATION AND RETRAINING
--------------------------------------------------

Deployment is not the end of the Machine Learning Life Cycle.

The model must be continuously monitored after deployment.

Real-world data can change over time.

This can cause:

- Data Drift
- Concept Drift
- Model Degradation


Data Drift:

The distribution of input data changes over time.


Concept Drift:

The relationship between input and output changes over time.


Example:

A face-mask detection model may initially be trained on:

- Certain masks
- Certain lighting conditions
- Certain camera qualities

Later, users may provide:

- Different masks
- Different lighting
- Different cameras
- Different environments

The model's performance may decrease.


Solution:

1. Monitor model performance
2. Collect new data
3. Retrain the model
4. Test the new model
5. Deploy the improved model


--------------------------------------------------
IMPORTANT CONCEPT: MLDLC IS ITERATIVE
--------------------------------------------------

MLDLC is not a simple straight-line process.

For example:

Problem
   ↓
Data
   ↓
Preprocessing
   ↓
EDA
   ↓
Feature Engineering
   ↓
Training
   ↓
Evaluation
   ↓
Deployment
   ↓
Monitoring
   ↓
Performance decreases
   ↓
Collect new data
   ↓
Retrain
   ↓
Deploy again


--------------------------------------------------
COMPLETE MLDLC FLOW
--------------------------------------------------

Problem Framing
       ↓
Data Gathering
       ↓
Data Processing
       ↓
EDA
       ↓
Feature Engineering
       ↓
Feature Selection
       ↓
Model Training
       ↓
Model Evaluation
       ↓
Model Selection
       ↓
Hyperparameter Tuning
       ↓
Ensemble Learning (if required)
       ↓
Model Deployment
       ↓
Testing
       ↓
Monitoring
       ↓
Optimization
       ↓
Retraining
       ↓
Deployment





