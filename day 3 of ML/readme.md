# Types of Machine Learning

This README provides concise, exam-oriented notes based on the provided lecture transcript.

## Machine Learning

Machine Learning can broadly be divided into four categories:

1. Supervised Learning
2. Unsupervised Learning
3. Semi-Supervised Learning
4. Reinforcement Learning

---

## 1. Supervised Learning

In **Supervised Learning**, the dataset contains both:

- **Input features (X)**
- **Output/Target/Label (Y)**

The model learns the relationship between input and output and uses it to predict the output for new inputs.

### Example

| IQ | CGPA | Placement |
|---:|---:|---|
| 100 | 7.1 | Yes |
| 111 | 8.9 | Yes |
| 72 | 6.3 | No |

Here:

- IQ and CGPA → Inputs
- Placement → Output/Target

### Types of Supervised Learning

#### A. Regression

If the target/output is a **numerical or continuous value**, the problem is called Regression.

Examples:

- House price prediction
- Salary prediction
- Temperature prediction
- Student package prediction

**Rule:**

> Numerical output → Regression

#### B. Classification

If the target/output represents a **class or category**, the problem is called Classification.

Examples:

- Placement → Yes/No
- Email → Spam/Not Spam
- Loan → Approved/Rejected
- Image → Dog/Cat
- Rain → Yes/No

**Rule:**

> Categorical output → Classification

---

## 2. Unsupervised Learning

In **Unsupervised Learning**, the dataset contains input data but does not have predefined output labels.

The goal is to discover hidden patterns, groups, relationships, or unusual observations in the data.

### Major Applications

### A. Clustering

Clustering divides data points into groups based on similarity.

Example:

Students can be grouped according to their IQ and CGPA:

- High IQ + High CGPA
- High IQ + Low CGPA
- Low IQ + Low CGPA

Applications:

- Customer segmentation
- Student grouping
- Market segmentation
- Product grouping

### B. Dimensionality Reduction

A dataset may contain a very large number of features. Dimensionality reduction reduces the number of dimensions while trying to preserve important information.

Benefits:

- Reduces computational complexity
- Makes data easier to visualize
- Can remove redundant information
- Helps deal with high-dimensional datasets

A commonly used technique is:

- **PCA — Principal Component Analysis**

For example, data with hundreds or thousands of dimensions can sometimes be represented in 2D or 3D for visualization.

### C. Anomaly Detection

An anomaly is a data point that is significantly different from normal observations.

Examples:

- Credit-card fraud
- Unusual financial transactions
- Manufacturing defects
- Network/security anomalies

### D. Association Rule Learning

Association Rule Learning finds relationships between items or events in a dataset.

A common application is **Market Basket Analysis**.

Example:

If customers frequently buy Product A and Product B together, a business can use this relationship for:

- Product placement
- Recommendations
- Promotions
- Cross-selling

A famous example is the observed association between **baby diapers and beer** in retail transaction data.

---

## 3. Semi-Supervised Learning

**Semi-Supervised Learning** combines ideas from supervised and unsupervised learning.

The dataset contains:

- A small amount of **labelled data**
- A large amount of **unlabelled data**

### Why use it?

Creating labels can be expensive and time-consuming because humans may need to manually inspect and label data.

For example:

- Collecting thousands of images may be easy.
- Manually identifying and labelling every image can be difficult and expensive.

Semi-supervised methods attempt to use the small labelled portion together with the large unlabelled portion.

### Example

In image/face recognition systems, a small number of examples may be identified or labelled, while the system uses patterns in the remaining data to help organize or identify similar examples.

---

## 4. Reinforcement Learning

**Reinforcement Learning (RL)** is based on learning through interaction with an environment.

Instead of being given a fixed set of correct answers, an **agent** takes actions and receives feedback in the form of rewards or penalties.

### Basic Process

```text
Agent
  ↓
Observes Environment
  ↓
Takes Action
  ↓
Receives Reward / Penalty
  ↓
Updates Policy
  ↓
Takes Better Action
```

### Important Terms

#### Agent
The entity that makes decisions.

#### Environment
The world/system in which the agent operates.

#### Action
A decision made by the agent.

#### Reward
Positive feedback received for a desirable action.

#### Penalty
Negative feedback received for an undesirable action.

#### Policy
The strategy used by the agent to decide which action to take in a particular situation.

### Example

Suppose an agent is playing a game.

- Good action → Reward
- Bad action → Penalty

After repeated interaction, the agent learns which actions are more likely to produce good results.

Reinforcement Learning has been used in areas such as game playing and other sequential decision-making problems.

---

# Complete Machine Learning Classification

```text
Machine Learning
│
├── Supervised Learning
│   ├── Regression
│   └── Classification
│
├── Unsupervised Learning
│   ├── Clustering
│   ├── Dimensionality Reduction
│   ├── Anomaly Detection
│   └── Association Rule Learning
│
├── Semi-Supervised Learning
│
└── Reinforcement Learning
```

---

# Quick Comparison

| Type | Data Available | Main Goal | Example |
|---|---|---|---|
| **Supervised** | Input + Output | Predict output | House price |
| **Unsupervised** | Input only | Find patterns/groups | Customer clustering |
| **Semi-Supervised** | Some labelled + lots of unlabelled data | Learn with limited labels | Image recognition |
| **Reinforcement** | Interaction + rewards/penalties | Learn good decisions | Game playing |

---

# Important Exam Shortcuts

### Supervised Learning

> Input + Output → Learn relationship → Predict

### Regression vs Classification

> Numerical output → **Regression**

> Categorical output → **Classification**

### Unsupervised Learning

> Input only → Find hidden patterns

### Semi-Supervised Learning

> Small labelled dataset + Large unlabelled dataset

### Reinforcement Learning

> Agent + Environment + Action + Reward/Penalty

---

