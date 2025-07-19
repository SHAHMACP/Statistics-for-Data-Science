# ANOVA, ANCOVA, MANOVA, and MANCOVA – Definitions and Examples

This repository explains four related statistical methods using a clear structure:  
**Method → Simple Definition → Real-World Example**

---

## 🔹 1. ANOVA – *Analysis of Variance*

Compares the **means of one dependent variable** across **two or more independent groups**.

**Example:**  
A school tests whether three different teaching methods (A, B, C) lead to different **math test scores** among students.

> - IV: Teaching Method  
> - DV: Math Test Score  
> - ➤ Use ANOVA to check if the average scores differ between groups.

---

## 🔹 2. ANCOVA – *Analysis of Covariance*

Compares **group means** of one outcome **while adjusting for another variable (covariate)** that also influences the outcome.

**Example:**  
You want to compare the **math test scores** of students taught using methods A, B, and C — but students started with different **previous GPA** levels.

> - IV: Teaching Method  
> - DV: Math Test Score  
> - Covariate: Previous GPA  
> - ➤ Use ANCOVA to control for GPA before comparing test scores.

---

## 🔹 3. MANOVA – *Multivariate Analysis of Variance*

Tests group differences for **two or more dependent variables** at the same time, **considering their relationships**.

**Example:**  
You compare teaching methods A, B, and C to see their effect on both **math test scores** and **class attendance rates**.

> - IV: Teaching Method  
> - DVs: Math Score, Attendance %  
> - ➤ Use MANOVA to analyze combined outcomes together.

---

## 🔹 4. MANCOVA – *Multivariate Analysis of Covariance*

Extends MANOVA by **including covariates** — tests group differences across multiple dependent variables while **controlling for other variables**.

**Example:**  
You evaluate how teaching methods A, B, and C affect both **math scores** and **attendance**, while controlling for **previous GPA**.

> - IV: Teaching Method  
> - DVs: Math Score, Attendance %  
> - Covariate: Previous GPA  
> - ➤ Use MANCOVA to see real group differences after adjusting for GPA.

---

## Summary Table

| Method    | # DVs | Covariate | Purpose                                                                 |
|-----------|-------|-----------|-------------------------------------------------------------------------|
| ANOVA     | 1     | ❌ No      | Compare one outcome across groups                                      |
| ANCOVA    | 1     | ✅ Yes     | Compare one outcome across groups, adjusting for a covariate           |
| MANOVA    | 2+    | ❌ No      | Compare multiple related outcomes across groups                        |
| MANCOVA   | 2+    | ✅ Yes     | Compare multiple outcomes across groups, adjusting for covariates      |

---

## What is a Covariate?

> A **covariate** is a continuous variable that **influences the outcome** but is **not part of the group comparison**.  
> Example: A student's **previous GPA** can affect test scores but isn’t related to the teaching method itself.

---

## Real-World Use Cases

| Field        | Use Case Example                                                                 |
|--------------|----------------------------------------------------------------------------------|
| Education    | Teaching method effects on test score + participation (adjusting for prior GPA) |
| Healthcare   | Treatment effects on blood pressure + weight (adjusting for age)                |
| Marketing    | Ad campaign effects on brand recall + purchase (adjusting for income)           |
| Psychology   | Therapy effects on stress + mood (controlling for baseline anxiety score)       |

---
