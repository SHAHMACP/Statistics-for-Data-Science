## 📘 Problems Based on Multivariate Normal Distribution

---

### 🔹 Q1

Let $X \sim \mathcal{N}_3(\mu, \Sigma)$ where:

$$
\mu = \begin{bmatrix} 5 \\ 3 \\ 7 \end{bmatrix}, \quad
\Sigma = \begin{bmatrix}
4 & -1 & 0 \\
-1 & 2 & 2 \\
0 & 2 & 9
\end{bmatrix}
$$

#### a) Find $P(X_1 > 6)$

Since $X \sim \mathcal{N}_3(\mu, \Sigma)$ then using the property (If the whole vector $X$ is multivariate normal, then each component $X_j$ is also normally distributed): 
$X_1 \sim \mathcal{N}(\mu=5, \sigma=4)$

So,

$$
\begin{aligned}
P(X_1 > 6) &= P(\frac{X_1 - \mu}{\sigma} > \frac{6 - 5}{2})\\
&= P(Z > 0.5) \\
&= 1- P(Z<=0.5) \\
&= 1 - 0.6915 \\
&= \boxed{0.3085} \\
\end{aligned}
$$

---

#### b) Find $P(5X_2 + 4X_3 > 70)$

Let $Y = 5X_2 + 4X_3$

If you make a linear combination like $Y = a_1X_1 + a_2X_2 + \dots + a_nX_n$, then $Y$ will follow a normal distribution.
Then $Y \sim \mathcal{N}(\mu', \sigma')$.

First, compute the expected value:

$$
\begin{aligned}
\mathbb{E}(Y) &= \mathbb{E}(5X_2 + 4X_3) \\
&= 5 \mathbb{E}(X_2) + 4 \mathbb{E}(X_3)\\
&=  5 \cdot 3 + 4 \cdot 7 \\
&= 15 + 28 \\
&= 43
\end{aligned}
$$

Now compute variance:
From $\Sigma$: $\text{Var}(X_2) = 4$, $\text{Var}(X_3) = 9$, $\text{Cov}(X_2, X_3) = 2$

$$
\begin{aligned}
\text{Var}(Y) &= \text{Var}(5X_2 + 4X_3) \\
&= 5^2 \cdot \text{Var}(X_2) + 4^2 \cdot \text{Var}(X_3) + 2 \cdot 5 \cdot 4 \cdot \text{Cov}(X_2, X_3) \\
&= 25 \cdot 4 + 16 \cdot 9 + 40 \cdot 2 \\
&= 100 + 144 + 80 \\
&= 324
\end{aligned}
$$

Then $Y \sim \mathcal{N}(\mu'=43, \sigma'=324)$.

Now standardize:

$$
\begin{aligned}
P(Y> 70)&=P(\frac{Y - 43}{\sqrt{324}} > \frac{70 - 43}{\sqrt{324}}) \\
&= P(Z > 1.5) \\
&= 1-P(Z<=1.5) \\
&= 1-0.9332\\
&=  \boxed{0.0668}
\end{aligned}
$$

---

#### c) Find $P(4X_1-3X_2 + 5X_3 < 80)$
Let $Y = 4X_1-3X_2 + 5X_3$

If you make a linear combination like $Y = a_1X_1 + a_2X_2 + \dots + a_nX_n$, then $Y$ will follow a normal distribution.
Then $Y \sim \mathcal{N}(\mu', \sigma')$.

First, compute the expected value:

$$
\begin{aligned}
\mathbb{E}(Y) &= \mathbb{E}(4X_1-3X_2 + 5X_3) \\
&= 4 \mathbb{E}(X_1)- 3 \mathbb{E}(X_2) + 5 \mathbb{E}(X_3)\\
&= 4 \cdot 5- 3 \cdot 3 + 5 \cdot 7 \\
&= 20-9 + 35 \\
&= 46
\end{aligned}
$$

Now compute variance:
From $\Sigma$: $\text{Var}(X_1) = 4$, $\text{Var}(X_2) = 4$, $\text{Var}(X_3) = 9$, $\text{Cov}(X_1, X_2) = -1$, $\text{Cov}(X_2, X_3) = 2$, $\text{Cov}(X_1, X_3) = 0$

$$
\begin{aligned}
\text{Var}(Y) &= \text{Var}(4X_1-3X_2 + 5X_3) \\
&= 4^2 \cdot \text{Var}(X_1) +3^2 \cdot \text{Var}(X_2) + 5^2 \cdot \text{Var}(X_3) + 2 \cdot 4 \cdot (-3) \cdot \text{Cov}(X_1, X_2)+ 2 \cdot (-3) \cdot 5 \cdot \text{Cov}(X_2, X_3)+ 2 \cdot 4 \cdot 5 \cdot \text{Cov}(X_1, X_3) \\
&= 16 \cdot 4 + 9 \cdot 4 + 25 \cdot 9 - 24 \cdot (-1)- 30 \cdot 2 + 40 \cdot 0  \\
&= 64 + 36+225+24-60 + 0 \\
&= 289
\end{aligned}
$$

Then $Y \sim \mathcal{N}(\mu'=46, \sigma'=289)$.

Now standardize:

$$
\begin{aligned}
P(Y< 80)&=P(\frac{Y - 46}{\sqrt{289}} < \frac{80 - 46}{\sqrt{289}}) \\
&= P(Z < 2) \\
&=  \boxed{0.9773}
\end{aligned}
$$

---

### 🔹 Q2

Let $X$ and $Y$ be jointly normal with:

- $\mu_X = 1$, $\sigma_X^2 = 1$
- $\mu_Y = 0$, $\sigma_Y^2 = 1$
- $\rho = \frac{1}{2}$

Find $P(2X + Y < 3)$

Let $V = 2X + Y$. Then:

$$
\mathbb{E}(V) = 2 \cdot \mathbb{E}(X) + \mathbb{E}(Y) = 2 \cdot 1 + 0 = 2
$$

Since $\text{Cov}(X,Y) = \rho \cdot \sigma_X \cdot \sigma_Y = \frac{1}{2} \cdot 1 \cdot 2 = 1$

$$
\text{Var}(V) = 2^2 \cdot \text{Var}(X) + \text{Var}(Y) + 2 \ cdot 2 \cdot 1 \cdot \text{Cov}(X, Y)
= 4 + 4 + 4 \cdot 1 = 4 + 4 + 4 = 12
$$

Then,

$$
V \sim \mathcal{N}(2, 12)
$$

Now standardize:

$$
\begin{aligned}
P(V< 3)&=P(\frac{V - 2}{\sqrt{12}} < \frac{3 - 2}{\sqrt{12}}) \\
&= P(Z < \frac{1}{\sqrt{12}}) \\
&= P(Z < 0.2886) \\
&=  \boxed{0.6103}
\end{aligned}
$$

---
