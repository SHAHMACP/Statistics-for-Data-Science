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

Given a dataset with `n` samples and `d` features:

### **Step 1: Standardize the Data**
- PCA is sensitive to feature scaling
- Ensure each feature has mean 0 and variance 1.
- Standardization formula: $z = \frac{x - \mu}{\sigma}$ where $\mu$ is the mean of the feature and $\sigma$ is standard deviation of the feature


### **Step 2: Compute the Covariance Matrix**
- The covariance matrix shows relationships between variables
- Formula: $\text{Cov}(X) = \frac{1}{n-1} X^\top X$ where $X$ is the standardized data matrix



### **Step 3: Calculate Eigenvalues and Eigenvectors**
- **Eigenvectors** → Directions of maximum variance (principal components)
- **Eigenvalues** → Amount of variance captured in each direction


### **Step 4: Sort Eigenvalues and Select Top k**
- Arrange eigenvalues in **descending order**
- Keep the top `k` eigenvectors (based on explained variance)


### **Step 5: Form the Projection Matrix**
- Projection matrix $W$ is formed from selected eigenvectors: $W = [e_1, e_2, ..., e_k]$

### **Step 6: Transform the Data**
- Project original data into new feature space: $X_{\text{reduced}} = X \times W$

---
