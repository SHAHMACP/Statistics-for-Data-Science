# Multivariate Analysis of Variance (MANOVA)

**MANOVA (Multivariate Analysis of Variance)** compares the means of **multiple dependent variables** across groups defined by one or more **independent variables**.

Unlike ANOVA (which tests group differences for a single dependent variable), **MANOVA** accounts for **correlations between multiple dependent variables**, offering a more **comprehensive understanding** of group differences.

---

## Key Assumptions of MANOVA

- **Multivariate Normality**:  
  All dependent variables should be normally distributed **within each group**.

- **Homogeneity of Covariance Matrices**:  
  The variance-covariance matrices of the dependent variables should be **equal across groups**.

- **Independence of Observations**:  
  Observations should be independent — one participant's data must not influence another's.

- **Linearity**:  
  The relationships between each pair of dependent variables should be **linear within each group**.

---

## Why Assumption Checking Matters

| Reason                  | Explanation                                                                 |
|-------------------------|-----------------------------------------------------------------------------|
| Validity of Results   | Violating assumptions can lead to **misleading or invalid** conclusions.    |
| Interpretation        | Proper interpretation relies on assumption validity. If assumptions fail, consider alternative methods. |
| Statistical Power     | Satisfying assumptions improves the ability to detect **true** group differences. |

---

## Types of MANOVA

| Type          | Description                                                  |
|---------------|--------------------------------------------------------------|
| **One-way MANOVA** | Tests differences in multiple DVs based on a **single** IV.   |
| **Two-way MANOVA** | Examines the combined effects of **two** IVs on multiple DVs. |

---

## Example: Testing Diet Plans

### Objective:
Determine if different diet plans lead to differences in **health outcomes** like weight, blood pressure, and cholesterol.

### Hypotheses:
- **Null Hypothesis**: No significant difference in the combined health outcomes across diet plans.
- **Alternative Hypothesis**: At least one diet leads to a different combination of outcomes.

### Steps:
1. Check MANOVA assumptions.
2. Conduct MANOVA test.
3. If significant, run **post-hoc tests** to identify where differences lie.

---

## Benefits of Using MANOVA

- **Comprehensive Analysis**:  
  Understand group differences across multiple outcomes simultaneously.

- **Reduced Type I Error**:  
  Considers correlations between DVs, avoiding inflated error from running separate ANOVAs.

- **Increased Statistical Power**:  
  Higher likelihood of detecting actual group effects when DVs are correlated.

- **Informative Visualizations**:  
  Group differences and relationships can be visualized using scatter plots, profile plots, and canonical discriminant analysis.

---

## Practical Applications of MANOVA

| Domain                 | Use Case Example                                                                 |
|------------------------|----------------------------------------------------------------------------------|
| **Education**        | Compare teaching methods on **grades**, **participation**, and **motivation**.   |
| **Healthcare**       | Evaluate treatment effects on **weight**, **BP**, and **glucose**.               |
| **Marketing**        | Compare ad campaigns based on **recall**, **engagement**, and **conversion**.    |
| **Psychology**       | Assess therapy outcomes on **anxiety**, **mood**, and **stress**.                |

---
