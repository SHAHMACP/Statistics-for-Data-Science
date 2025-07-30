# Linear Discriminant Analysis (LDA)

**Linear Discriminant Analysis (LDA)** is a dimensionality reduction technique used as a **preprocessing step** in **pattern classification** and **machine learning applications**. 
It finds the **linear combination of features** that best separates two or more classes.

---

## Main Idea

- To **find projection to a line** such that samples from different classes are **well separated linearly**.
- Or to **project high-dimensional data** (N-dimensional) onto a **lower-dimensional space** (K = n−1) while retaining the **maximum class discriminatory information**.

---

## Why is LDA Important?

1. It is **multi-faceted** and can handle multiple and different scenarios.
2. It can be used as a **multi-class linear classifier**, unlike logistic regression.
3. Useful for **dimensionality reduction**.
4. Helps in **extracting features** in face detection and image classification models.

---

## How Does LDA Work?

The goal of an LDA algorithm is to find the **best linear combination** that gives the **maximum separation between the number of groups**.
 LDA maximizes the ratio of between-class scatter to within-class scatter.

- It calculates **discriminant scores** using a **linear combination** of weights and centered data points.
- These weights are **extracted from eigenvectors**.

---

## What are the Limitations of LDA?

- It assumes **linear boundaries** and does **not work well for non-linear problems**.
- Assumes **normal distribution** of features.
- Performs poorly with **imbalanced data**.

---

## How to Prepare Data for LDA?

1. **Classification Problem**: LDA is applied when the **target variable is categorical** (binary or multi-class).
2. **Gaussian Distribution**: The standardized input variables should follow a **Gaussian distribution**.
3. **Remove Outliers**: LDA is **sensitive to outliers**. They should be removed to avoid distorting class means and variances.
4. **Same Variance**: LDA assumes **equal variance** across groups.
5. **Standardization**: It is better to **standardize the data** before applying LDA.

---

## Extensions to LDA

1. **Quadratic Discriminant Analysis (QDA)**:  
   Allows each class to have its own estimate of variance.
    <img width="266" height="178" alt="image" src="https://github.com/user-attachments/assets/2db3d69d-5586-48c5-9c40-622d2d4fbf20" />

2. **Regularized Discriminant Analysis (RDA)**:  
   Adds regularization to manage small sample sizes and high-dimensional data.

3. **Flexible Discriminant Analysis (FDA)**:  
   Allows for **non-linear combinations** of input variables using splines or kernel functions.

---

## Real-World Applications of LDA

1. **Face Recognition**:  
   Face recognition systems represent each face as a set of features and use LDA to classify individuals.

2. **Medical Diagnosis**:  
   Used to classify patients based on symptoms into disease categories.

3. **Customer Identification**:  
   LDA helps in segmenting customers likely to buy a product in a shopping mall.

4. **Speech Recognition**:  
   Helps classify spoken phrases based on sound patterns.

5. **Robotics & AI**:  
   Used in training robots for object recognition, interaction, and movement planning.

---

