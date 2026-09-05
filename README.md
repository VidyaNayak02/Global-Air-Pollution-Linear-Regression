# Machine Learning Foundations: Regression, Feature Selection & Outlier Treatment

## 📌 Overview

This project explores fundamental concepts in data analysis and machine learning through practical experiments on real-world data.

The main focus is understanding how **variable selection, univariate linear regression, feature scaling, and outlier treatment** affect data analysis and model performance.

Different preprocessing techniques were tested and compared rather than applying a single method blindly.

---
### Dataset
https://www.kaggle.com/datasets/sazidthe1/global-air-pollution-data

---
## 🎯 Concepts Covered

- Variable Selection using Data Visualization
- Univariate Linear Regression
- Feature Scaling
- Outlier Detection and Treatment
- IQR Method
- Winsorization
- 3-Sigma Method
- Model Performance Comparison

---

## 1️⃣ Variable Selection

Variable selection was performed to identify features that were useful for predicting the target variable.

**Data visualization played a key role in this process.** Correlation analysis and visual comparisons were used to understand relationships between variables and the target before selecting features for modelling.

This helped make feature selection more data-driven rather than selecting variables only based on their availability.

### Key Learning

> Data visualization can play an important role in understanding relationships and selecting meaningful variables before modelling.

---

## 2️⃣ Univariate Linear Regression

Univariate Linear Regression was implemented using a **single independent variable** to predict a continuous target.

### Workflow

```text
Dataset
   ↓
Select one predictor
   ↓
Train-Test Split
   ↓
Linear Regression
   ↓
Prediction
   ↓
Model Evaluation
```

The model was evaluated using:

- MAE — Mean Absolute Error
- MSE — Mean Squared Error
- RMSE — Root Mean Squared Error
- R² Score

### Key Learning

Univariate Linear Regression provides a simple baseline for understanding the relationship between one predictor and a continuous target.

---

## 3️⃣ Feature Scaling

Feature scaling transforms numerical features to a comparable scale.

Two common techniques were studied:

### Standardization — Z-score



Standardization transforms the data using its mean and standard deviation.



### Important Observation

Feature scaling did not produce a meaningful improvement in the performance of ordinary Univariate Linear Regression in the experiment.

This demonstrates that feature scaling is **algorithm-dependent**.

It is generally more important for algorithms that depend on **distance or feature magnitude**, such as:

- K-Nearest Neighbors (KNN)
- K-Means Clustering
- Support Vector Machines (SVM)

### Key Learning

> Feature scaling may have little effect on ordinary Univariate Linear Regression but can be much more important for distance-dependent and scale-sensitive algorithms.

---

# 4️⃣ Outlier Detection and Treatment

Three different approaches were explored for identifying and treating outliers:

1. **IQR Method**
2. **Winsorization**
3. **3-Sigma Method**

The purpose was to understand how different outlier-treatment techniques affect the dataset and subsequent model performance.

---

## 4.1 IQR Method

The Interquartile Range (IQR) method identifies potential outliers using the first quartile (Q1) and third quartile (Q3).

\[
IQR = Q3-Q1
\]

The usual boundaries are:

\[
Lower\ Bound = Q1-1.5(IQR)
\]

\[
Upper\ Bound = Q3+1.5(IQR)
\]

Observations outside these limits were treated as potential outliers.

### Key Learning

The IQR method is useful because it is based on quartiles and does not require the data to follow a normal distribution.

---

## 4.2 Winsorization

Winsorization was used to reduce the influence of extreme values without completely deleting the observations.

Instead of removing extreme observations, values beyond selected limits are replaced by the corresponding boundary values.

### Key Learning

> Winsorization retains the observations while reducing the effect of extreme values on the analysis.

---

## 4.3 3-Sigma Method

The 3-Sigma method identifies observations that lie more than three standard deviations away from the mean.

\[
\mu-3\sigma \leq X \leq \mu+3\sigma
\]

Values outside this range were considered potential outliers.

### Result in This Analysis

The 3-Sigma method identified **288 potential outliers** during the analysis.

Among the three approaches tested, **3-Sigma produced the most useful results for the particular dataset and analysis performed in this project**.

The treated data was then compared with the original data to observe the effect on model performance.

### Key Learning

> The effectiveness of an outlier-treatment technique depends on the characteristics of the dataset. In this particular analysis, the 3-Sigma approach gave the most favourable results among the three methods tested.

---

## 🔍 Outlier Treatment Comparison

| Method | Main Idea | Observation |
|---|---|---|
| **IQR** | Uses quartiles and IQR boundaries | Useful for detecting extreme values without assuming normality |
| **Winsorization** | Caps extreme observations | Retains observations while reducing their influence |
| **3-Sigma** | Uses mean ± 3 standard deviations | Performed best for this particular dataset in the experiment |

### Important Note

The conclusion that 3-Sigma performed best is **specific to this dataset and experimental setup**. It should not be interpreted as meaning that 3-Sigma is always better than IQR or Winsorization.

---

# 🔄 Overall Workflow

```text
Dataset
   ↓
Data Inspection
   ↓
Variable Selection
   ↓
Data Visualization
   ↓
Univariate Linear Regression
   ↓
Model Evaluation
   ↓
Feature Scaling
   ↓
Outlier Detection
   ├── IQR
   ├── Winsorization
   └── 3-Sigma
   ↓
Outlier Treatment
   ↓
Model Evaluation & Comparison
```

---

## 🛠️ Tools & Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

---

## 📚 Key Learnings

### Variable Selection
Data visualization played a key role in understanding relationships between variables and selecting useful predictors.

### Linear Regression
Univariate Linear Regression provides a simple baseline for understanding how one feature can be used to predict a continuous target.

### Feature Scaling
Feature scaling is algorithm-dependent. It may have little effect on ordinary Univariate Linear Regression but can be important for distance-dependent algorithms.

### Outlier Treatment
Different methods can produce different results. Outliers should be investigated rather than automatically removed.

### IQR
IQR provides a robust method for identifying potential outliers using quartiles.

### Winsorization
Winsorization reduces the influence of extreme values while retaining the observations.

### 3-Sigma
The 3-Sigma method provided the most favourable results among the tested outlier-treatment methods for this particular dataset.

---

# ✅ Conclusion

This project demonstrated that effective machine learning requires more than simply selecting a model. **Understanding the data, selecting relevant variables, choosing appropriate preprocessing techniques, and comparing their effects are all important steps.**

Variable selection was supported by data visualization, which helped identify meaningful relationships before modelling. Univariate Linear Regression was then used as a baseline to study the relationship between a predictor and the target.

Three outlier-treatment techniques—**IQR, Winsorization, and 3-Sigma**—were explored. Each method treats extreme observations differently, and the results showed that there is no single outlier-treatment technique that is automatically best for every dataset. In this particular analysis, **the 3-Sigma method produced the most favourable results among the three approaches tested**.

The analysis also highlighted an important principle: **outliers are not necessarily errors**. They can represent genuine extreme observations or contain useful information. Therefore, they should be investigated and treated carefully rather than removed blindly.

Feature scaling was also examined, and the experiment showed that its effect depends on the machine-learning algorithm. While it did not meaningfully improve ordinary Linear Regression, feature scaling can be much more important for **distance-dependent algorithms such as KNN and K-Means**, where differences in feature magnitude directly affect distance calculations.

> **Overall Takeaway:** Good machine learning starts with understanding the data. Visualization, thoughtful variable selection, appropriate outlier treatment, and algorithm-specific preprocessing choices are essential for building meaningful and reliable models.
### Author
Vidya Nayak
