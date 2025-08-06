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
