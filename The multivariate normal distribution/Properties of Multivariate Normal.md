# Properties of Multivariate Normal Distribution

Let $X_{n \times 1} \sim \mathcal{N}_n(\mu, \Sigma)$, i.e., a multivariate normal random vector with mean vector $\mu$ and covariance matrix $\Sigma$. Then the following properties hold:

---

## 1. Each Variable is Univariate Normal
If the whole vector $X$ is multivariate normal, then each component $X_j$ is also normally distributed.

If $X \sim \mathcal{N}_n(\mu, \Sigma)$, then for all $j = 1, 2, \dots, n$:   $X_j \sim \mathcal{N}(\mu_j, \sigma_j^2)$

**Example**:  
If  

$$
X = \begin{bmatrix} 
X_1 \\ 
X_2 
\end{bmatrix} 
\sim \mathcal{N}_2\left( 
\begin{bmatrix} 
5 \\ 
3 
\end{bmatrix},\ 
\begin{bmatrix} 
4 & 1 \\ 
1 & 2 \end{bmatrix} 
\right)
$$


Then:  
- $X_1 \sim \mathcal{N}(5, 4)$  
- $X_2 \sim \mathcal{N}(3, 2)$  

---

## 2. Any Subset is Multivariate Normal

If you select a few components from the vector $X$, the resulting subset is also multivariate normal.
  
If $X_{n \times 1} \sim \mathcal{N}_n(\mu, \Sigma)$, then for any subset $X_q$:  $X_q \sim \mathcal{N}_q(\mu_q, \Sigma_q)$

**Example**:  
From a 5-variable MVN vector, selecting $X_1$, $X_3$, and $X_5$ results in:

$$
X_q = \begin{bmatrix} X_1 \\ X_3 \\ X_5 \end{bmatrix} \sim \mathcal{N}_3(\mu_q, \Sigma_q)
$$

---

## 3. Any Linear Combination is Univariate Normal

If you make a linear combination like $Y = a_1X_1 + a_2X_2 + \dots + a_nX_n$, then $Y$ will follow a normal distribution.
  
If $X \sim \mathcal{N}_n(\mu, \Sigma)$ and $a \in \mathbb{R}^n$, then:

$$
Y = a^T X \sim \mathcal{N}(a^T \mu, a^T \Sigma a)
$$

**Example**:  
Using the same $X$ as above:

$$Y = 2X_1 - 3X_2 \sim \mathcal{N}(2 \cdot 5 - 3 \cdot 3, \, 2^2 \cdot 4 + (-3)^2 \cdot 2 + 2 \cdot 2 \cdot (-3) \cdot 1)$$  
So,  
$Y \sim \mathcal{N}(1, 16 + 18 - 12 = 22)$

---

## 4. Linear Transformation is Multivariate Normal

If we apply a matrix $A$ to $X$, the result is still a multivariate normal distribution.

If $X \sim \mathcal{N}_n(\mu, \Sigma)$ and $A$ is a $q \times n$ matrix, then:

$$
Y = AX \sim \mathcal{N}_q(A\mu, A\Sigma A^T)
$$

**Example**:  
If $X$ is a 3D MVN vector and you define two new variables $Y_1, Y_2$ using a matrix $A$, then:

$$
Y = \begin{bmatrix} Y_1 \\ Y_2 \end{bmatrix} = A X \sim \mathcal{N}_2(A \mu, A \Sigma A^T)
$$

---



