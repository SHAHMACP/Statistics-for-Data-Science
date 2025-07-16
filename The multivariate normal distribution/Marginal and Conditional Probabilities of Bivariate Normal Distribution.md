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

The amount of rainfall recorded at a US weather station in January is modeled as a random variable $X$, and the amount in February is a random variable $Y$.  
Assume:  
 $$
(X, Y) \sim BVN(\mu_X = 6, \mu_Y = 4, \sigma_X = 1, \sigma_Y = 0.5, \rho = 0.1)
$$
  
Find:  
 1. \ P(X \leq 5) \)  
2. \( P(Y \leq 5 \mid X = 5) \)



### (i) Marginal Probability \( P(X \leq 5) \)

Since \( X \sim N(6, 1^2) \), standardize:

\[
Z = \frac{X - \mu_X}{\sigma_X} = \frac{5 - 6}{1} = -1
\]

From Z-table:

\[
P(X \leq 5) = P(Z \leq -1) = \boxed{0.1587}
\]

---

### (ii) Conditional Probability \( P(Y \leq 5 \mid X = 5) \)

We apply the formula for conditional normal distribution:

#### Step 1: Conditional Mean

\[
\mu_{Y|X} = \mu_Y + \rho \cdot \frac{\sigma_Y}{\sigma_X}(x - \mu_X)
= 4 + 0.1 \cdot \frac{0.5}{1}(5 - 6) = 4 - 0.05 = 3.95
\]

#### Step 2: Conditional Variance

\[
\sigma_{Y|X}^2 = \sigma_Y^2(1 - \rho^2) = 0.25 \cdot 0.99 = 0.2475
\]

#### Step 3: Standardize

\[
Z = \frac{5 - 3.95}{\sqrt{0.2475}} = \frac{1.05}{0.4975} \approx 2.11
\]

From Z-table:

\[
P(Y \leq 5 \mid X = 5) = P(Z \leq 2.11) = \boxed{0.9826}
\]

---

## ✅ Final Answers

- \( P(X \leq 5) = \boxed{0.1587} \)  
- \( P(Y \leq 5 \mid X = 5) = \boxed{0.9826} \)

---
