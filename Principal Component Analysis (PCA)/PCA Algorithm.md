# The PCA algorithm



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


## Mathematical Foundation

Given a dataset with `n` samples and `d` features:

1. **Standardize the data**  
   Ensure each feature has mean = 0 and variance = 1.

2. **Compute the Covariance Matrix**  
   \[
   \text{Cov}(X) = \frac{1}{n-1} X^\top X
   \]

3. **Compute Eigenvalues and Eigenvectors** of the covariance matrix  
   - Eigenvectors → directions of maximum variance (principal components)  
   - Eigenvalues → magnitude of variance in each direction

4. **Sort eigenvectors** by descending eigenvalues

5. **Select top `k` components** (based on cumulative explained variance)

6. **Project data** onto the new `k`-dimensional subspace

---

## 🔢 PCA Algorithm (Step-by-Step)

```text
1. Normalize the dataset (zero mean, unit variance)
2. Calculate the covariance matrix
3. Calculate the eigenvalues and eigenvectors
4. Choose top k eigenvectors based on eigenvalues
5. Form a projection matrix W
6. Project the original dataset: X_reduced = X × W


* **PCA is sensitive to scale**, so always **standardize** your data before applying PCA.
* **PCA is a linear technique**, so it works best when relationships between features are linear.
