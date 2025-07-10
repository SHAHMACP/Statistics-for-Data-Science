# Assumptions of Multivariate Regression – Explained Simply**

---

###  1. **Linearity**

**What it means**:
There should be a straight-line relationship between the inputs (independent variables) and the result (dependent variable).

**What if it’s not true?**
The model will give wrong results because it's trying to fit a straight line to a curved pattern.

**How to check**:

* **Residuals vs Fitted Plot**: If there's a curve, it's not linear.
* **Partial Residual Plot**: Helps show how each variable affects the result.

**Example**:
Predicting salary using years of experience is linear. But predicting salary using age (very young and very old may earn less) may not be linear.

---

### 2. **Independence of Observations**

 **What it means**:
Each observation should be unrelated to the others.

 **What if it’s not true?**
Standard errors become too small, making unimportant predictors look important.

 **How to check**:

* **Durbin-Watson Test**: Detects patterns in data over time.
* **Residual Plot**: Patterns mean values are connected.

 **Example**:
In sales data collected every day, today’s sales may depend on yesterday’s (violates independence).

---

### 3. **Homoscedasticity (Equal Spread of Errors)**

 **What it means**:
Errors (residuals) should have the same spread no matter the value of the inputs.

 **What if it’s not true?**
The model might give more weight to certain data points, leading to incorrect conclusions.

 **How to check**:

* **Residual vs Fitted Plot**: Should be a random cloud. A cone or fan shape indicates a problem.
* **Scale-Location Plot**: Checks if the spread is constant.

 **Example**:
Predicting house prices—if errors are large only for expensive houses, it's a violation.

---

### 4. **Normality of Errors**

 **What it means**:
The errors (residuals) should follow a normal (bell-curve) distribution.

 **What if it’s not true?**
The confidence intervals and p-values might be wrong.

 **How to check**:

* **Q-Q Plot**: Dots should lie on a straight line.
* **Histogram of Residuals**: Should look like a bell curve.

 **Example**:
If your errors are skewed, like only large positive errors, it's not normal.

---

### 5. **No Multicollinearity**

 **What it means**:
The input variables (predictors) shouldn’t be highly related to each other.

 **What if it’s not true?**
It’s hard to know which variable is actually influencing the output, and the model becomes unstable.

 **How to check**:

* **VIF (Variance Inflation Factor)**: Value > 10 is a red flag.
* **Correlation Matrix**: Look for high correlations between inputs.

 **Example**:
Including both height in inches and height in centimeters will cause multicollinearity.

---

### 6. **No Autocorrelation in Residuals**

 **What it means**:
The errors should not follow a pattern over time (or space).

 **What if it’s not true?**
Future predictions, especially in time-series data, will be unreliable.

 **How to check**:

* **Durbin-Watson Test**
* **Residuals Over Time Plot**

 **Example**:
In stock market data, prices today are linked to yesterday’s prices – autocorrelation is common.

---

### 7. **Sufficient Sample Size**

 **What it means**:
You need enough data to build a reliable model.

 **What if it’s not true?**
The model might learn noise (random things) instead of the real pattern—called overfitting.

 **How to check**:

* **Power Analysis**: To estimate needed sample size.

 **Example**:
Trying to predict house prices using only 10 houses is too little—model won’t generalize well.

---

###  8. **Mean of Residuals Should Be Zero**

 **What it means**:
On average, the prediction errors (residuals) should cancel out to zero.

 **What if it’s not true?**
The line may not be the best fit—it's either always over or under-predicting.

 **How to check**:

* Look at the **mean of residuals** after fitting the model.

 **Example**:
If you predict that all students will get 5 marks more than they actually do, the residuals are not centered around 0.

---

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


