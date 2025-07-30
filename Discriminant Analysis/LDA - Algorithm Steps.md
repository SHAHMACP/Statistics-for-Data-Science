# Linear Discriminant Analysis (LDA) -  Main Objective
- LDA works by finding directions in the feature space that best separate the classes. 
- Maximize between-class variance while minimizing within-class variance.

---

## Algorithm Steps

Assume we have two classes with d-dimensional samples such as $x_1,x_2,x_3,...,x_n$ where $x_i$ represents a data point.
Suppose $n_1$ samples belong to class $c_1$ and $n_2$ samples belong to class $c_2$. 
Let the means of class $c_1$ and class $c_2$ is $\mu_1$ and $\mu_2$ respectively. 
​
 
#### 1. Compute Within-Class Scatter Matrix ($S_w$)

- For each class $C_i$ with mean $\mu_i$:
  $$S_i = \sum_{x \in C_i}(x - \mu_i)(x - \mu_i)^T$$
- Combine to get:
  $$S_W = \sum_i S_i= \sum S_1+ \sum S_2+...$$
  

#### 2. Compute Between-Class Scatter Matrix ($S_B$)

- For two classes:
  $$S_B = (\mu_1 - \mu_2)(\mu_1 - \mu_2)^T$$
- For multiple classes, generalize using weighted class means.

### 3. Solve the Eigenproblem
The goal is to maximize the ratio of the between-class scatter to the within-class scatter, which leads us to the following criteria:
$$J=\frac{S_B}{S_W}$$.
For the best separation, we calculate the eigenvector corresponding to the highest eigenvalue of the scatter matrices
- Solve:
  $$S_W^{-1} S_B V = \lambda V$$
- Principal eigenvector (largest $\lambda\$) gives the **optimal projection direction**.

### 4. Project and Classify

- New observation $x$ is projected as:
  $$y = V^T x$$
- Assign class based on **closest centroid** or highest discriminant score.

---
