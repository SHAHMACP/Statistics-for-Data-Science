# The PCA algorithm
Principal Component Analysis (PCA) is an **unsupervised linear transformation technique** used for **dimensionality reduction**.  
It finds new directions (**principal components**) that capture the **maximum variance** in the data.


## Common Terms in PCA Algorithm

| Term                                          | Meaning                                                                                               |
| --------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| **Feature / Variable**                        | An individual measurable property (e.g., height, weight, sweetness)                                   |
| **Dimension**                                 | The number of features/ variables/ columns in a dataset (e.g., 2D = 2 features)                                           |
| **Standardization / Normalization**           | Rescaling data so that each feature has mean = 0 and standard deviation = 1                           |
| **Covariance**                                | A measure of how two variables change together (positive = increase together, negative = opposite)    |
| **Correlation**                         | It signifies the strength and direction of the relationship between two variables.                                      |
| **Covariance Matrix**                         | A square matrix showing covariance between each pair of features                                      |
| **Eigenvalue**                                | Represents the amount of variance carried in the direction of a corresponding eigenvector             |
| **Eigenvector**                               | A vector that defines the direction of a principal component                                          |
| **Projection**                                | Mapping the original data onto the new principal component axes                                       |
| **Orthogonal Vectors**                        | Vectors that are at 90° to each other; uncorrelated(Correlation=0)                                                   |

---
## PCA Algorithm – Step-by-Step


### **Step 1 – Prepare the Dataset**

Let the dataset have:

* $n$ = number of features (variables)
* $N$ = number of samples (observations)

| Feature | Sample 1 | Sample 2 | ... | Sample N |
| ------- | -------- | -------- | --- | -------- |
| $X_1$   | $X_{11}$ | $X_{12}$ | ... | $X_{1N}$ |
| $X_2$   | $X_{21}$ | $X_{22}$ | ... | $X_{2N}$ |
| ...     | ...      | ...      | ... | ...      |
| $X_n$   | $X_{n1}$ | $X_{n2}$ | ... | $X_{nN}$ |


### **Step 2 – Compute the Mean of Each Feature**

The mean of the $i$-th variable is:

$$
\bar{X_i} = \frac{1}{N} \sum_{j=1}^{N} X_{ij}
$$

This mean will be used for centering the data.


### **Step 3 – Compute the Covariance Matrix**

The covariance between features $X_i$ and $X_j$ is:

$$
\text{Cov}(X_i, X_j) = \frac{1}{N-1} \sum_{k=1}^N (X_{ik} - \bar{X_i}) (X_{jk} - \bar{X_j})
$$

The **covariance matrix $S$** is an $n \times n$ matrix:

$$
S = 
\begin{bmatrix}
\text{Cov}(X_1, X_1) & \text{Cov}(X_1, X_2) & \dots & \text{Cov}(X_1, X_n) \\
\text{Cov}(X_2, X_1) & \text{Cov}(X_2, X_2) & \dots & \text{Cov}(X_2, X_n) \\
\vdots & \vdots & \ddots & \vdots \\
\text{Cov}(X_n, X_1) & \text{Cov}(X_n, X_2) & \dots & \text{Cov}(X_n, X_n)
\end{bmatrix}
$$


### **Step 4 – Find Eigenvalues and Eigenvectors of the Covariance Matrix**

To find **eigenvalues ($\lambda$)**:

$$
|S - \lambda I| = 0
$$

This gives $n$ roots:

$$
\lambda_1, \lambda_2, ..., \lambda_n
$$

where:

$$
\lambda_1 > \lambda_2 > ... > \lambda_n
$$

For each eigenvalue $\lambda$, solve:

$$
(S - \lambda I) U = 0
$$

where $U$ is the eigenvector corresponding to $\lambda$


### **Step 5 – Normalize Eigenvectors**

Each eigenvector is normalized to have unit length:

$$
e_i = \frac{u_i}{\|u_i\|}, \quad \|u_i\| = \sqrt{u_{i1}^2 + u_{i2}^2 + \dots + u_{in}^2}
$$


### **Step 6 – Select Principal Components**

* The **first principal component** corresponds to the eigenvector with the **largest eigenvalue**.
* The **second principal component** corresponds to the eigenvector with the second largest eigenvalue, and so on.


### **Step 7 – Derive the New Dataset**

Form a projection matrix from the top $k$ eigenvectors:

$$
W = [e_1, e_2, ..., e_k]
$$

Project the original centered dataset $X$ into the new reduced space:

$$
P_{ij} = e_i^T 
\begin{bmatrix}
X_{1j} - \bar{X_1} \\
X_{2j} - \bar{X_2} \\
\vdots \\
X_{nj} - \bar{X_n}
\end{bmatrix}
$$

The result is the **transformed dataset** with $k$ principal components.

---

## 📊 PCA Algorithm Summary Table

| Step | Action                          | Output                               |
| ---- | ------------------------------- | ------------------------------------ |
| 1    | Prepare dataset                 | Matrix $X$                           |
| 2    | Compute mean of features        | Mean vector                          |
| 3    | Compute covariance matrix       | Matrix $S$                           |
| 4    | Find eigenvalues & eigenvectors | $\lambda_i$, $e_i$                   |
| 5    | Normalize eigenvectors          | Unit vectors                         |
| 6    | Select top $k$ PCs              | Projection matrix $W$                |
| 7    | Project data                    | Reduced dataset $X_{\text{reduced}}$ |

---

