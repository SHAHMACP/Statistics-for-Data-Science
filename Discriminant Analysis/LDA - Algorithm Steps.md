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
# Linear Discriminant Analysis: Worked-Out Example

This demonstrates the complete LDA computation using matrix algebra, including:

- Mean vectors
- Within-class scatter matrix $S_W$
- Between-class scatter matrix $S_B$
- Solving the eigenvalue equation
- Computing eigenvectors
- Final projection vector

---
Given two classes:

**Class $C_1$:**

$$C_1 = \{(4,1), (2,4), (2,3), (3,6), (4,4)\} =  
\begin{bmatrix}
4&1\\
2& 4\\
2&3\\
3&6\\
4&4
\end{bmatrix}$$

**Class $C_2$:**

$$C_2 = \{(9,10), (6,8), (9,5), (8,7), (10,8)\}= \begin{bmatrix}
9&10\\
6& 8\\
9&5\\
8&7\\
10&8
\end{bmatrix}$$

<img width="400" height="300" alt="image" src="https://github.com/user-attachments/assets/3768d5bb-bb62-44c8-acad-3b288ae99d1d" />

---

## ✅ Step 1: Compute Class Means

Compute the mean for each class:

$\mu_1 = \left( \frac{4+2+2+3+4}{5}, \frac{1+4+3+6+4}{5} \right) = (3.0,\ 3.6)$

$\mu_2 = \left( \frac{9+6+9+8+10}{5}, \frac{10+8+5+7+8}{5} \right) = (8.4,\ 7.6)$

<img width="400" height="300" alt="image" src="https://github.com/user-attachments/assets/0e2e28ac-f405-45f8-98e1-b163f65b8e1b" />

---

## ✅ Step 2: Compute Within-Class Scatter Matrix $S_W$

Each term in:

$$
S_i = \sum_{x \in C_i} (x - \mu_i)(x - \mu_i)^T
$$

### For $C_1$:

Compute $(x - \mu_1)$ for each $x$ in $C_1$. 

- For $(4,1)$: $x_1 - \mu_1 =(4,1)-(3,3.6)= (1, -2.6)$
- For $(2,4)$: $x_2 - \mu_1 =(2,4)-(3,3.6)= (-1, 0.4)$
- For $(2,3)$: $x_3 - \mu_1 =(2,3)-(3,3.6)= (-1, -0.6)$
- For $(3,6)$: $x_4 - \mu_1 =(3,6)-(3,3.6)= (0, 2.4)$
- For $(4,4)$: $x_5 - \mu_1 =(4,4)-(3,3.6)= (1, 0.4)$

<img width="489" height="385" alt="image" src="https://github.com/user-attachments/assets/d3b628c0-3fed-4132-b21b-db9f87f582c1" />

Then:

$$\begin{align*}
S_1 
&=
\frac{1}{n} \sum_{x \in C_i} (x - \mu_i)(x - \mu_i)^T \\
&=
\frac{1}{5}( \begin{bmatrix}1 \\
-2.6 \end{bmatrix} 
 \begin{bmatrix}1 & -2.6 \end{bmatrix} + \begin{bmatrix}-1 \\
0.4 \end{bmatrix} 
 \begin{bmatrix}-1 & 0.4 \end{bmatrix} + \begin{bmatrix}-1 \\
-0.6 \end{bmatrix} 
 \begin{bmatrix}-1 & -0.6 \end{bmatrix}+ \begin{bmatrix} 0 \\
2.4 \end{bmatrix} 
 \begin{bmatrix}0 & 2.4 \end{bmatrix}+\begin{bmatrix}1 \\
0.4 \end{bmatrix} 
 \begin{bmatrix}1 & 0.4 \end{bmatrix}) \\
 &=
\frac{1}{5}( \begin{bmatrix}
1 & -2.6 \\
-2.6 & 6.76
\end{bmatrix} + \begin{bmatrix}
1 & -0.4 \\
-0.4 & 0.16
\end{bmatrix} + \begin{bmatrix}
1 & 0.6 \\
0.6 & 0.36
\end{bmatrix} + \begin{bmatrix}
0 & 0 \\
0 & 5.76
\end{bmatrix} + \begin{bmatrix}
1 & 0.4 \\
0.4 & 0.16
\end{bmatrix}) \\
&=
\frac{1}{5}(\begin{bmatrix}
4 & -2 \\
-2 & 13.2
\end{bmatrix}) \\
&=
\begin{bmatrix}
0.8 & -0.4 \\
-0.4 & 2.64
\end{bmatrix} \\
\end{align*}$$



### For $C_2$:

Compute $(x - \mu_2)$ for each $x$ in $C_2$. 

- For $(9,10)$: $x_1 - \mu_2 =(9,10)-(8.4,\ 7.6)= (0.6, 2.4)$
- For $(6,8)$: $x_2 - \mu_2 =(6,8)-(8.4,\ 7.6)= (-2.4, 0.4)$
- For $(9,5)$: $x_3 - \mu_2 =(9,5)-(8.4,\ 7.6)= (0.6, -2.6)$
- For $(8,7)$: $x_4 - \mu_2 =(8,7)-(8.4,\ 7.6)= (-0.4, -0.6)$
- For $(10,8)$: $x_5 - \mu_2 =(10,8)-(8.4,\ 7.6)= (1.6, 0.4)$
  
<img width="484" height="390" alt="image" src="https://github.com/user-attachments/assets/dbc8a616-96f1-4ea2-a548-d915cdc60015" />


Then:

$$\begin{align*}
S_1 
&=
\frac{1}{n} \sum_{x \in C_i} (x - \mu_i)(x - \mu_i)^T \\
&=
\frac{1}{5}( \begin{bmatrix}0.6 \\
2.4 \end{bmatrix} 
 \begin{bmatrix}0.6 & 2.4  \end{bmatrix} + \begin{bmatrix}-2.4 \\
0.4 \end{bmatrix} 
 \begin{bmatrix}-2.4 & 0.4 \end{bmatrix} + \begin{bmatrix}0.6 \\
-2.6 \end{bmatrix} 
 \begin{bmatrix}0.6 & -2.6 \end{bmatrix}+ \begin{bmatrix} -0.4 \\
 -0.6 \end{bmatrix} 
 \begin{bmatrix}-0.4 &  -0.6 \end{bmatrix}+\begin{bmatrix}1.6 \\
0.4 \end{bmatrix} 
 \begin{bmatrix}1.6 & 0.4 \end{bmatrix}) \\
 &=
\frac{1}{5}( \begin{bmatrix}
0.36 & 1.44 \\
1.44 & 5.76
\end{bmatrix} + \begin{bmatrix}
5.76 & -0.96 \\
-0.96 & 0.16
\end{bmatrix} + \begin{bmatrix}
0.36 & -1.56 \\
-1.56 & 6.76
\end{bmatrix} + \begin{bmatrix}
0.16 & 0.24 \\
0.24 & 0.36
\end{bmatrix} + \begin{bmatrix}
2.56 & 0.64 \\
0.64 & 0.16
\end{bmatrix}) \\
&=
\frac{1}{5}(\begin{bmatrix}
9.2 & -0.2 \\
-0.2 & 13.2
\end{bmatrix}) \\
&=
\begin{bmatrix}
1.84 & -0.04 \\
-0.04 & 2.64
\end{bmatrix} \\
\end{align*}$$


### Total Within-Class Scatter Matrix:

$$
S_W = S_1 + S_2 = \begin{bmatrix}
0.8 & -0.4 \\
-0.4 & 2.64
\end{bmatrix} + \begin{bmatrix}
1.84 & -0.04 \\
-0.04 & 2.64
\end{bmatrix} =
\begin{bmatrix}
2.64 & -0.44 \\
-0.44 & 5.28
\end{bmatrix}
$$

---

## ✅ Step 3: Compute Between-Class Scatter Matrix $S_B$

$$\mu_1 - \mu_2 = (3,3.6) - (8.4,\ 7.6)= (-5.4 ,-4.0)$$

<img width="461" height="392" alt="image" src="https://github.com/user-attachments/assets/77e60f3a-8667-4dd3-8885-83c9660bce61" />

Then:

$$
S_B = (\mu_1 - \mu_2)(\mu_1 - \mu_2)^T = \begin{bmatrix} -5.4 \\
-4 \end{bmatrix} 
 \begin{bmatrix} -5.4 & -4  \end{bmatrix} =
\begin{bmatrix}
29.16 & 21.6 \\
21.6 & 16
\end{bmatrix}
$$

---

## ✅ Step 4: Compute $S_W^{-1} S_B$

The goal is to maximize the ratio of the between-class scatter to the within-class scatter: So maximise $$J=\frac{S_B}{S_W} = S_W^{-1} S_B$$.

First, compute the inverse of $S_W$:

$$
S_W =
\begin{bmatrix}
2.64 & -0.44 \\
-0.44 & 5.28
\end{bmatrix}
$$

Let $S_W^{-1}$ be:

$$
S_W^{-1} = \frac{1}{\det(S_W)} \cdot adj(A) = 
\frac{1}{(2.64 \cdot 5.28) - (-0.44)^2} \cdot
\begin{bmatrix}
5.28 & 0.44 \\
0.44 & 2.64
\end{bmatrix} = \begin{bmatrix}
0.384 & 0.032 \\
0.032 & 0.192
\end{bmatrix}
$$

Then:

$$S_W^{-1} S_B =\begin{bmatrix}
0.384 & 0.032 \\
0.032 & 0.192
\end{bmatrix}
\cdot
\begin{bmatrix}
29.16 & 21.6 \\
21.6 & 16
\end{bmatrix}=
\begin{bmatrix}
11.89 & 8.81 \\
5.08 & 3.76
\end{bmatrix}
$$

---

## ✅ Step 5: Find Eigenvalues

Solve:

$$
\left| S_W^{-1}S_B - \lambda I \right| = 0
$$

$$
\left|
\begin{bmatrix}
11.89 & 8.81 \\
5.08 & 3.76
\end{bmatrix} -  \lambda  \cdot \begin{bmatrix}1 & 0 \\
0 & 1
\end{bmatrix}
\right| = 0
$$

$$
\left|
\begin{bmatrix}
11.89 - \lambda & 8.81 \\
5.08 & 3.76 - \lambda
\end{bmatrix}
\right| = 0
$$

Determinant:

$$
(11.89 - \lambda)(3.76 - \lambda) - (8.81)(5.08) = 0
$$

Solve:

$$ 44.7064 - 11.89\lambda- 3.76\lambda + \lambda^2 -44.7548 = 0$$

$$
\lambda^2 - 15.65\lambda + 0.0484 = 0
$$

$$
\Rightarrow \lambda = \frac{15.65 \pm \sqrt{(-15.65)^2 - 4 \cdot 1 \cdot  0.0484}}{2 \cdot 1} = 15.65, 0.0031
$$

---

## ✅ Step 6: Find Eigenvector $v$

For the best separation, we calculate the eigenvector corresponding to the highest eigenvalue of the scatter matrices.

So $\lambda =15.65$

Now Solve:

$$
(S_W^{-1} S_B - \lambda I)v = 0
$$

Substitute and solve:
$$
\begin{bmatrix}
11.89 - 15.65 & 8.81 \\
5.08 & 3.76 - 15.65
\end{bmatrix}
\cdot
\begin{bmatrix}
v_1 \\
v_2
\end{bmatrix}
= 0
$$

$$
\begin{bmatrix}
-3.76 & 8.81 \\
5.08 & -11.89
\end{bmatrix}
\cdot
\begin{bmatrix}
v_1 \\
v_2
\end{bmatrix}
= 0
$$

From row 1: $-3.76v_1 + 8.81v_2 = 0$

$$
\Rightarrow \frac{v_1}{v_2} = \frac{8.81}{3.76} = 2.34
$$

So:

$$
v =
\begin{bmatrix}
2.34 \\
1
\end{bmatrix}
$$

Normalize:

$$\|v\| = \sqrt{(2.34)^2 + 1^2} = 2.54
\Rightarrow v =
\begin{bmatrix}
\frac{2.34}{2.54} \\
\frac{1}{2.54}
\end{bmatrix}=
\begin{bmatrix}
0.92 \\
0.39
\end{bmatrix}
$$

---

## ✅ Step 7: Project Data

Each $x$ is projected onto new axis:

$$
y = v^T x = [0.92,\ 0.39] \cdot x
$$

---

## 📌 Summary of Results

| Step | Description |
|------|-------------|
| Step 1 | Class Means |
| Step 2 | Within-Class Scatter Matrix $S_W$ |
| Step 3 | Between-Class Scatter Matrix $S_B$ |
| Step 4 | Matrix Product $S_W^{-1} S_B$ |
| Step 5 | Find $\lambda$ |
| Step 6 | Solve Eigenvector $v$ |
| Step 7 | Project $x$ onto new axis using $y = v^T x$ |

---

## 📖 References

- LDA Theory: [Wikipedia](https://en.wikipedia.org/wiki/Linear_discriminant_analysis)
- Python Tutorial: [GeeksforGeeks LDA](https://www.geeksforgeeks.org/machine-learning/ml-linear-discriminant-analysis/)

