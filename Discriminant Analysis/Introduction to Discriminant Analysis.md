# Discriminant Analysis

## Definition
> Discriminant Analysis is a supervised, multivariate classification technique used to predict group membership based on observed features.

> Discriminant Analysis is used when:
- The **dependent variable** is **categorical** (i.e., it represents group labels or categories).
- The **independent variables** are **interval** or **ratio scale** (quantitative variables).
> It is a technique to discriminate between two or more mutually exclusive and exhaustive groups on the basis of some explanatory variables.

> It finds a linear combination of predictor variables (like age, income, test scores) that best separates observations into predefined classes (like pass/fail, spam/not spam, diseased/healthy).
---

## **Multiple Discriminant Analysis (MDA)**

- Used when there are **more than two groups** (e.g., three or more categories in the dependent variable).
- LDA with **multiple discriminant functions**, one fewer than the number of groups.
- Helps in visualizing the **group separation** in higher-dimensional space.

**Example**:  
Classifying a product preference into **three brands** based on price sensitivity, quality perception, and advertisement response.

---
## Comparison: Discriminant Analysis vs ANOVA vs Regression


### Similarities

| Aspect | Discriminant Analysis (DA) | ANOVA | Regression |
|--------|-----------------------------|-------|------------|
| **Number of Dependent Variables** | One |One |One |
| **Number of Independent Variables** | Multiple |Multiple |Multiple |


### Differences

| Feature | Discriminant Analysis | ANOVA | Regression |
|--------|------------------------|-------|------------|
| **Dependent Variable Type** | **Categorical** (e.g., Pass/Fail, Class A/B/C) | **Continuous**, but grouped into **categories** | **Continuous** (e.g., height, sales) |
| **Independent Variables** | **Continuous** (interval/ratio scale) | **Categorical** (usually grouping variable) | **Continuous or categorical** |
| **Goal** | **Classify** cases into known groups | **Test** if group means differ | **Predict** the value of a response variable |
| **Output** | **Classification rule**, group membership | **F-ratio**, significance of mean differences | **Regression equation**, predicted value |
| **Number of Groups** | 2 or more categories in dependent variable | 2 or more groups in factor | Usually one dependent variable |


---
## Assumptions of Discriminant Analysis

To use Discriminant Analysis effectively and interpret results correctly, certain statistical assumptions must be satisfied.

| Assumption | Description | Why? |
|------------|-------------|-------------|
| 1. Sample Size | Sample size should be **at least 5 times** the number of independent variables **per group** | A small sample size can make covariance estimates unstable and result in poor classification performance|
| 2. Normality | Each of the **independent variables should be normally distributed** within each group of the dependent variable | DA uses probability density functions that assume normality to compute classification functions accurately |
| 3. Equal Variances | Variance-covariance matrices are the same for all groups | This assumption ensures **linear** separation between groups. If violated, **Quadratic Discriminant Analysis (QDA)** should be used |
| 4. No Outliers | Data should not contain extreme values |DA is **highly sensitive to outliers**, which can distort group means, covariances, and classification accuracy |
| 5. No Multicollinearity among the independent variables | Predictors should not be highly correlated | Highly correlated predictors can make the discriminant function unstable and hard to interpret. |
| 6. Mutually Exclusive Groups | The groups (categories of the dependent variable) must be **mutually exclusive** | Each subject or case must belong to **only one group**, not multiple. |
| 7. Correct Classification | Each case in the training data must be **correctly classified** into the known group. Training labels must be accurate |The DA model learns from the group labels provided; incorrect labeling misguides the function.  |



> Violating these assumptions can lead to poor model accuracy, invalid statistical tests, and incorrect interpretations.

---

## Hypothesis in Discriminant Analysis (DA)

### **Null Hypothesis (H₀)**:
> The group means of a set of independent variables for two or more groups are **equal**.  
(There is **no significant difference** between the groups based on the independent variables.)

Mathematically:

$$H_0: \mu_1 = \mu_2 = \dots = \mu_k$$

Where $\mu_k $ is the mean vector of the independent variables for group $k$.

---

### **Alternative Hypothesis (H₁)**:
> The group means are **not equal**.  
At least one group is significantly different from the others in terms of the independent variables.

\[
H_1: \mu_i \ne \mu_j \quad \text{for some } i \ne j
\]

---

## 🧠 What It Means

- If we **fail to reject H₀**, it means the independent variables **do not significantly distinguish** between the groups.
- If we **reject H₀**, it means the model can be used to **classify observations** into groups better than chance.

---

---

### Evaluating a Discriminant Analysis

Discriminant Analysis not only builds classification rules, but also:

- Tests for **significant differences** among groups.
- Measures **classification accuracy** (how well the model classifies cases into correct groups).
- Tells us **how many categories** the dependent variable contains and how well they are separated.

---
