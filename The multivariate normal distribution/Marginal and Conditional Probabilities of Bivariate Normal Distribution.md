# Bivariate Normal Distribution — Marginal and Conditional Probabilities

A **Bivariate Normal Distribution** models two continuous random variables, say  $X$ and $Y$, that are **jointly normally distributed**. It is defined by:

- Means: $\mu_X, \mu_Y$
- Standard deviations: $\sigma_X, \sigma_Y$
- Correlation coefficient: $\rho$

### Notation

$$
(X, Y) \sim BVN(\mu_X, \mu_Y, \sigma_X^2, \sigma_Y^2, \rho)
$$

The **joint probability density function (PDF)** is:

$$
f(x, y) = \frac{1}{2\pi \sigma_X \sigma_Y \sqrt{1 - \rho^2}} \exp \left( -\frac{1}{2(1 - \rho^2)} \left[
\left( \frac{x - \mu_X}{\sigma_X} \right)^2 - 2\rho \left( \frac{x - \mu_X}{\sigma_X} \right) \left( \frac{y - \mu_Y}{\sigma_Y} \right) + \left( \frac{y - \mu_Y}{\sigma_Y} \right)^2
\right] \right)
$$

---

## Marginal Distribution

The **marginal distribution** of one variable (say,  $X$ ) is simply its individual distribution ignoring the other. In a bivariate normal, the marginals are also normal:

That is if $(X, Y) \sim BVN(\mu_X, \mu_Y, \sigma_X^2, \sigma_Y^2, \rho)$ then

$$
X \sim \mathcal{N}(\mu_X, \sigma_X^2), \quad Y \sim \mathcal{N}(\mu_Y, \sigma_Y^2)
$$

The probability density function (PDF) of a marginal normal distribution with mean $\mu$ and variance $\sigma^2$ is:

\$$
f(x) = \frac{1}{\sqrt{2\pi \sigma^2}} \cdot \exp\left( -\frac{1}{2} \cdot \frac{(x - \mu)^2}{\sigma^2} \right)
\$$

---

## Conditional Distribution

The **conditional distribution** of $Y$ given  $X = x$ is also normal:

$$
Y \mid X = x \sim \mathcal{N}(\mu_{Y|X}, \sigma_{Y|X}^2)
$$

Where:

 $$ \mu_{Y|X} = \mu_Y + \rho \cdot \frac{\sigma_Y}{\sigma_X}(x - \mu_X) $$
 $$ \sigma_{Y|X}^2 = \sigma_Y^2(1 - \rho^2) $$

This shows that knowing one variable changes our prediction and uncertainty about the other.

---

## ✅ Example 
*  Imagine we’re studying the height (in cm) and weight (in kg) of students in a college. We assume that these two variables are jointly normally distributed, i.e., they follow a bivariate normal distribution.
* If you look at just one variable (say, height), ignoring the other (weight), that’s a marginal distribution.
* Now imagine you know a student’s weight is 72 kg, and you ask:
“What is the probability distribution of their height, given they weigh 72 kg?”. That’s a conditional distribution. Because height and weight are correlated, knowing one gives extra information about the other.

---

## Problems

## Question 1: 

Let $X$ and $Y$ be jointly normal random variables such that:

- $X \sim N(1, 1)$
- $Y \sim N(0, 4)$
- Correlation $\rho = \frac{1}{2}$

Find:

$$
P(Y > 1 \mid X = 2)
$$


###  Solution

We use the formula for conditional distribution:

$$
Y \mid X = x \sim \mathcal{N} \left( \mu_Y + \rho \cdot \frac{\sigma_Y}{\sigma_X}(x - \mu_X),\ \sigma_Y^2 (1 - \rho^2) \right)
$$

#### Step 1: Plug in known values

- $\mu_X = 1, \sigma_X^2 = 1 \Rightarrow \sigma_X = 1$
- $\mu_Y = 0, \sigma_Y^2 = 4 \Rightarrow \sigma_Y = 2$
- $\(\rho = \frac{1}{2} \), \( x = 2)$

#### Step 2: Conditional Mean

$$
\mu_{Y|X=2} = 0 + \frac{1}{2} \cdot \frac{2}{1} \cdot (2 - 1) = 1
$$

#### Step 3: Conditional Variance

$$
\sigma_{Y|X}^2 = 4 (1 - \rho^2) = 4 \left(1 - \frac{1}{4} \right) = 4 \cdot \frac{3}{4} = 3
$$

So:

$$
Y \mid X = 2 \sim \mathcal{N}(1, 3)
$$


#### Step 4: Compute the probability

We want:

$$
P(Y > 1 \mid X = 2)
$$

Standardize:

$$
Z = \frac{1 - 1}{\sqrt{3}} = 0
$$

So:

$$
P(Y > 1 \mid X = 2) = P(Z > 0) = \boxed{0.5}
$$

---



## Question 2:
The amount of rainfall recorded at a US weather station in January is modeled as a random variable $X$, and the amount in February is a random variable $Y$.  
Assume:  
$\(X, Y) \sim BVN(\mu_X = 6, \mu_Y = 4, \sigma_X = 1, \sigma_Y = 0.5, \rho = 0.1)\$
  
Find:  
 1. $P(X \leq 5)$  
2. $P(Y \leq 5 \mid X = 5)$

### Solution

#### (i) Marginal Probability $P(X \leq 5)$

Since $X \sim N(6, 1^2)$, standardize:

$$
Z = \frac{X - \mu_X}{\sigma_X} = \frac{5 - 6}{1} = -1
$$

From Z-table:

$$
P(X \leq 5) = P(Z \leq -1) = \boxed{0.1587}
$$



#### (ii) Conditional Probability $P(Y \leq 5 \mid X = 5)$

We apply the formula for conditional normal distribution:

##### Step 1: Conditional Mean

$$
\mu_{Y|X} = \mu_Y + \rho \cdot \frac{\sigma_Y}{\sigma_X}(x - \mu_X)
= 4 + 0.1 \cdot \frac{0.5}{1}(5 - 6) = 4 - 0.05 = 3.95\
$$

##### Step 2: Conditional Variance

$$
\sigma_{Y|X}^2 = \sigma_Y^2(1 - \rho^2) = 0.25 \cdot 0.99 = 0.2475
$$

##### Step 3: Standardize

$$
Z = \frac{5 - 3.95}{\sqrt{0.2475}} = \frac{1.05}{0.4975} \approx 2.11
$$

From Z-table:

$$
P(Y \leq 5 \mid X = 5) = P(Z \leq 2.11) = \boxed{0.9826}
$$

---
## Question 3:

The life of a tube ($X_1$) and the filament diameter ($X_2$) are distributed as a **Bivariate Normal Distribution**:

$$
(X_1, X_2) \sim BVN\(2000, 0.1, 2500 , 0.01, 0.87)
$$

If the filament diameter is $0.098$, what is the probability that the tube will last more than 1950 hours?


### Solution

Given that 

$$
(X_1, X_2) \sim BVN\left(
\begin{bmatrix}
2000 \\
0.1
\end{bmatrix},
\begin{bmatrix}
2500 & 0.87 \\
0.87 & 0.01
\end{bmatrix}
\right)
$$

We need to compute:

$$
P(X_1 > 1950 \mid X_2 = 0.098)
$$

This follows the conditional normal distribution:

$$
X_1 \mid X_2 = x_2 \sim \mathcal{N}(\mu_{1|2}, \sigma_{1|2}^2)
$$

Where:

- Conditional mean:  
  $\mu_{1|2} = \mu_1 + \rho \cdot \frac{\sigma_1}{\sigma_2} (x_2 - \mu_2)$
  
  $= 2000 + 0.87 \cdot \frac{50}{0.1}(0.098 - 0.1)
  = 1999.13$

- Conditional variance:  
  $\sigma_{1|2}^2 = \sigma_1^2 (1 - \rho^2) = 2500 (1 - 0.7569) = 2500 \cdot 0.2431 = 607.75$

So:

$$
X_1 \mid X_2 = 0.098 \sim \mathcal{N}(1999.13,\ 607.75)
$$


#### Step: Standardize the probability

$$
P(X_1 > 1950 \mid X_2 = 0.098) = P\left(Z > \frac{1950 - 1999.13}{\sqrt{607.75}} \right)
= P(Z > -1.99)
$$

From the standard normal table:

$$
P(Z > -1.99) = \boxed{0.9767}
$$

---
