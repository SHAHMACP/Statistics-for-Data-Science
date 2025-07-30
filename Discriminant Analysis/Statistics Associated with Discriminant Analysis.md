# Statistics Associated with Discriminant Analysis

Discriminant Analysis involves several key statistical measures and outputs that help evaluate the model's accuracy, interpretability, and performance.

## 1. Discriminant Scores
The score assigned to each observation, computed as:

$$
\text{Score} = (b_1 \cdot x_1 + b_2 \cdot x_2 + \dots + b_n \cdot x_n + \text{constant})
$$

Where:
- $b_i$: unstandardized coefficient
- $x_i$: value of the i-th variable

The scores are used to **assign the observation to the closest group centroid**.

## 2. Discriminant Function Coefficients
These are the **weights or multipliers** applied to each predictor variable in the discriminant function.

They are in the **original units** of measurement.

## 3. Standardized Discriminant Function Coefficients
These are the discriminant function coefficients calculated using **standardized variables** (mean = 0, std dev = 1).

They allow us to **compare the relative importance** of each variable in the model.

---

## 4. Canonical Correlation
Canonical correlation measures the **strength of association** between the discriminant scores and the groups.

It is essentially the **multiple correlation** between the set of predictor variables and the discriminant function.


## 5. Centroid
The centroid is the **mean value of the discriminant scores** for a particular group.

It shows where each group lies along the discriminant axis and helps in **group separation and classification**.
<img width="416" height="405" alt="image" src="https://github.com/user-attachments/assets/7bd3dbfe-5670-4e0c-9dcf-c20d9326a1cf" />



## 6. Classification Matrix (Confusion Matrix)
Also known as the **confusion matrix**, it shows the number of:

- **Correctly classified cases**
- **Misclassified cases**

It helps in evaluating the **accuracy of the discriminant function**.
<img width="250" height="241" alt="image" src="https://github.com/user-attachments/assets/e1ba364e-fcb0-48b2-b089-05dd8ca873d8" />


## 7. Eigenvalues  
For each discriminant function, the **eigenvalue** represents the **ratio of between-group to within-group variance**.

A higher eigenvalue means better discrimination between groups.
<img width="1200" height="630" alt="image" src="https://github.com/user-attachments/assets/a51e79e9-42d1-4562-ac61-45c452d57897" />


## 7. Pooled Within-Group Correlation Matrix
This matrix is obtained by **averaging the covariance matrices** of all groups.

It is used in computing the discriminant functions assuming **equal variance** among groups.



## 9. Structure Correlations (Pooled Within-Groups Correlation)

These represent the **simple correlations** between each predictor variable and the discriminant function.

They help interpret **which variables contribute most** to group separation.

---
