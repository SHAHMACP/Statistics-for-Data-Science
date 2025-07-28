# Statistics Associated with Discriminant Analysis

Discriminant Analysis involves several key statistical measures and outputs that help evaluate the model's accuracy, interpretability, and performance.

---

## 1. Canonical Correlation

**Definition**:  
Canonical correlation measures the **strength of association** between the discriminant scores and the groups.

It is essentially the **multiple correlation** between the set of predictor variables and the discriminant function.

---

## 2. Centroid

**Definition**:  
The centroid is the **mean value of the discriminant scores** for a particular group.

It shows where each group lies along the discriminant axis and helps in **group separation and classification**.

---

## 3. Classification Matrix (Confusion Matrix)

**Definition**:  
Also known as the **confusion matrix**, it shows the number of:

- **Correctly classified cases**
- **Misclassified cases**

It helps in evaluating the **accuracy of the discriminant function**.

---

## 4. Discriminant Function Coefficients

**Definition**:  
These are the **weights or multipliers** applied to each predictor variable in the discriminant function.

They are in the **original units** of measurement.

---

## 5. Discriminant Scores

**Definition**:  
The score assigned to each observation, computed as:

\[
\text{Score} = (b_1 \cdot x_1 + b_2 \cdot x_2 + \dots + b_n \cdot x_n + \text{constant})
\]

Where:
- \(b_i\): unstandardized coefficient
- \(x_i\): value of the i-th variable

The scores are used to **assign the observation to the closest group centroid**.

---

## 6. Eigenvalues

**Definition**:  
For each discriminant function, the **eigenvalue** represents the **ratio of between-group to within-group variance**.

A higher eigenvalue means better discrimination between groups.

---

## 7. Pooled Within-Group Correlation Matrix

**Definition**:  
This matrix is obtained by **averaging the covariance matrices** of all groups.

It is used in computing the discriminant functions assuming **equal variance** among groups.

---

## 8. Standardized Discriminant Function Coefficients

**Definition**:  
These are the discriminant function coefficients calculated using **standardized variables** (mean = 0, std dev = 1).

They allow us to **compare the relative importance** of each variable in the model.

---

## 9. Structure Correlations (Pooled Within-Groups Correlation)

**Definition**:  
These represent the **simple correlations** between each predictor variable and the discriminant function.

They help interpret **which variables contribute most** to group separation.

---

## ✅ Summary Table

| Statistic | Description |
|-----------|-------------|
| Canonical Correlation | Association between predictors and groups |
| Centroid | Mean discriminant score per group |
| Classification Matrix | Accuracy summary (correct vs misclassified) |
| Coefficients | Weights for predictors in the model |
| Scores | Output of the discriminant function |
| Eigenvalues | Measure of discriminatory power |
| Pooled Matrix | Combined group covariances |
| Standardized Coefficients | Comparisons across variables |
| Structure Correlations | Predictor-function correlations |

---
