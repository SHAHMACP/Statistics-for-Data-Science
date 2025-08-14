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


### **Step 3 – Center the data (subtract the mean from each column)**

Centered rows (sample − mean):
 | Sample 1 | Sample 2 | ... | Sample N |
 | ------- | -------- | -------- | --- |
 | $X_{11}-\bar{X_1}$ | $X_{12}-\bar{X_1}$ | ... | $X_{1N}-\bar{X_1}$ |
 | $X_{21}-\bar{X_2}$ | $X_{22}-\bar{X_2}$ | ... | $X_{2N}-\bar{X_2}$ |
 | ...      | ...      | ... | ...      |
 | $X_{n1}-\bar{X_n}$ | $X_{n2}-\bar{X_n}$ | ... | $X_{nN}-\bar{X_n}$ |

### **Step 4 - Compute the Covariance Matrix**

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


### **Step 5 – Find Eigenvalues and Eigenvectors of the Covariance Matrix**

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


### **Step 6 – Normalize Eigenvectors**

Each eigenvector is normalized to have unit length:

$$
e_i = \frac{u_i}{\|u_i\|}, \quad \|u_i\| = \sqrt{u_{i1}^2 + u_{i2}^2 + \dots + u_{in}^2}
$$


### **Step 7 – Select Principal Components**

* The **first principal component** corresponds to the eigenvector with the **largest eigenvalue**.
* The **second principal component** corresponds to the eigenvector with the second largest eigenvalue, and so on.


### **Step 8 – Derive the New Dataset**

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

## PCA Algorithm Summary Table

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
# PCA worked example

* $x = [4,\ 8,\ 13,\ 7]$
* $y = [11,4,5,14]$

We reduce from **2 features** into  **1 principal component**.

#### Step 1 — Data matrix

Write the data as rows = samples, columns = features:

$$
X =
\begin{bmatrix}
4 & 11\\
8 & 4\\
13 & 5\\
7 & 14
\end{bmatrix}
\quad(\text{4 samples, 2 features x and y})
$$



#### Step 2 — Compute the mean of each feature (column means)

$$
\bar{x} = \frac{4 + 8 + 13 + 7}{4} = \frac{32}{4} = 8.0
$$

$$
\bar{y} = \frac{11 + 4 + 5 + 14}{4} = \frac{34}{4} = 8.5
$$

So mean vector: $\bar{\mathbf{m}} = [8.0,\; 8.5]$.



#### Step 3 — Center the data (subtract the mean from each column)

Centered rows (sample − mean):

$$
X_{\text{centered}} =\begin{bmatrix}
4-8 & 11-8.5\\
8-8 & 4-8.5\\
13-8 & 5-8.5\\
7-8 & 14-8.5
\end{bmatrix}=
\begin{bmatrix}
-4 & 2.5\\
0 & -4.5\\
5 & -3.5\\
-1 & 5.5
\end{bmatrix}
$$

(We will use these centered values for covariance and projection.)


## Step 4 — Covariance matrix (sample covariance, divide by $N-1$)

Covariance formula for two features $X$ and $Y$:

$$
Cov(X,X)=\frac{1}{N-1}\sum_{k=1}^N (x_k-\bar{x})^2
$$

$$
Cov(X,Y)=\frac{1}{N-1}\sum_{k=1}^N (x_k-\bar{x})(y_k-\bar{y})
$$

and symmetric for $Cov(Y,X)$, etc.

Compute entries:

1. $Cov(x,x) =
\frac{1}{4-1}\big((-4)^2 + 0^2 + 5^2 + (-1)^2\big)
= \frac{1}{3}\big(16 + 0 + 25 + 1\big) = \frac{42}{3} = 14
$

2. $Cov(y,y)=
\frac{1}{3}\big((2.5)^2 + (-4.5)^2 + (-3.5)^2 + (5.5)^2\big)
= \frac{1}{3}\big(6.25 + 20.25 + 12.25 + 30.25\big)
= \frac{69}{3} = 23
$

3. $Cov(x,y)=
\frac{1}{3}\big((-4)(2.5) + 0(-4.5) + 5(-3.5) + (-1)(5.5)\big)
= \frac{1}{3}\big(-10 + 0 -17.5 -5.5\big)
= \frac{-33}{3} = -11
$

3. $Cov(y,x)=
Cov(x,y) = -11
$

So the covariance matrix $S$ is:

$$
S =
\begin{bmatrix}
Cov(x,x) & Cov(x,y) \\
Cov(y,x) & Cov(y,y)
\end{bmatrix}=
\begin{bmatrix}
14 & -11 \\
-11 & 23
\end{bmatrix}
$$

(Confirm: symmetric and positive semidefinite.)

---

## Step 4 — Solve eigenproblem for $S$

We need eigenvalues $\lambda$ and eigenvectors $u$ solving:

$$
|S - \lambda I| = 0
\quad\Rightarrow\quad
\det\begin{bmatrix}14-\lambda & -11\\ -11 & 23-\lambda\end{bmatrix}=0
$$

Compute determinant:

$$
(14-\lambda)(23-\lambda) - (-11)^2 = 0
$$

$$
(14-\lambda)(23-\lambda) - 121 = 0
$$

$$
\lambda^2 - 37\lambda + 201 = 0
$$

Solve quadratic:

$$
\lambda = \frac{37 \pm \sqrt{37^2 - 4\cdot201}}{2}
= \frac{37 \pm \sqrt{1369 - 804}}{2}
= \frac{37 \pm \sqrt{565}}{2}
$$

Numerically:

$$
\sqrt{565} \approx 23.76972865
$$

$$
\lambda_1 \approx \frac{37 + 23.76972865}{2} \approx 30.38486432
$$

$$
\lambda_2 \approx \frac{37 - 23.76972865}{2} \approx 6.61513568
$$

So eigenvalues (sorted descending): $\lambda_1 \approx 30.3849$, $\lambda_2 \approx 6.6151$.



## Step 5 — Eigenvectors (directions of principal components)

Solve $(S - \lambda I)u=0$.

For $\lambda_1 \approx 30.38486432$:

$$
(14-\lambda_1) u_1 - 11 u_2 = 0
\quad\Rightarrow\quad
(14-30.3849) u_1 - 11 u_2 = 0
$$

$$
(-16.38486432) u_1 - 11 u_2 = 0
\quad\Rightarrow\quad
u_1 = \frac{-11}{-16.38486432} u_2 = \frac{11}{16.38486432}\,u_2
$$

Choose $u_2 = 1$ to get unnormalized eigenvector:

$$
u^{(1)} \propto \begin{bmatrix} 11/16.38486432 \\ 1 \end{bmatrix}
\approx \begin{bmatrix} 0.6718 \\ 1 \end{bmatrix}
$$

Normalize to unit length to obtain the principal component direction (unit eigenvector). Numerically (using standard eigen decomposition) the normalized eigenvector corresponding to the largest eigenvalue is:

$$
\mathbf{e}_1 =
\begin{bmatrix}
0.55738997\\
-0.83025082
\end{bmatrix}
$$

> Note: eigenvectors can be multiplied by −1 and still be valid — direction is what matters. The sign convention depends on how you solve; here PC1 is chosen so it points roughly in the positive size, negative sweetness direction.

For $\lambda_2$ the eigenvector (orthogonal to $\mathbf{e}_1$) is:

$$
\mathbf{e}_2 \approx \begin{bmatrix}-0.83025082\\ -0.55738997\end{bmatrix}
$$

(verify orthogonality: $\mathbf{e}_1^\top \mathbf{e}_2 \approx 0$.)

---

## Step 6 — Explained variance

Total variance = $\lambda_1 + \lambda_2 = 30.38486432 + 6.61513568 = 37$.

Explained variance ratio:

$$
\text{PC1 explained} = \frac{\lambda_1}{\lambda_1+\lambda_2} \approx \frac{30.38486432}{37} \approx 0.8212 \; (82.12\%)
$$

$$
\text{PC2 explained} \approx 17.88\%
$$

So PC1 already explains \~82% of the total variance — a good reason to reduce to 1 component.

---

## Step 7 — Project the centered data onto PC1 (compute scores)

Projection (score) for sample $j$:

$$
\text{score}_j = \mathbf{e}_1^\top \; (\mathbf{x}_j - \bar{\mathbf{m}})
$$

Using the centered rows computed earlier and $\mathbf{e}_1 = [0.55738997,\; -0.83025082]^\top$, compute scores:

Centered data rows:

1. $[-4,\; 2.5]$
2. $[0,\; -4.5]$
3. $[5,\; -3.5]$
4. $[-1,\; 5.5]$

Dot with $\mathbf{e}_1$:

1. $(-4)(0.55739) + (2.5)(-0.83025) \approx -4.30518692$
2. $(0)(0.55739) + (-4.5)(-0.83025) \approx 3.73612869$
3. $(5)(0.55739) + (-3.5)(-0.83025) \approx 5.69282771$
4. $(-1)(0.55739) + (5.5)(-0.83025) \approx -5.12376947$

So the 1‑D projected dataset (scores on PC1) is approximately:

$$
\text{PC1 scores} = [-4.3052,\; 3.7361,\; 5.6928,\; -5.1238]
$$

(These are the coordinates of each sample along the first principal component.)

---

## Optional: reconstruct approximate original values from PC1 (1‑D approximation)

If desired, one can reconstruct approximate original centered data by:

$$
\hat{X}_{\text{centered}} = (\text{scores}) \cdot \mathbf{e}_1^\top
$$

Then add back the mean $\bar{\mathbf{m}}$ to get approximate original coordinates. This shows information lost by keeping only PC1.

---



