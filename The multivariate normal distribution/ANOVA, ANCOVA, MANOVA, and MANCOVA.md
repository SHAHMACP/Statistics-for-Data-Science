# ANOVA, ANCOVA, MANOVA, and MANCOVA

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

<img width="1893" height="903" alt="image" src="https://github.com/user-attachments/assets/28ae2675-4770-4e44-8848-4867b409621a" />

<img width="1874" height="1089" alt="image" src="https://github.com/user-attachments/assets/7501d29d-e8ba-4c68-b993-a2085f164e0f" />

---

## 🔹 2. ANCOVA – *Analysis of Covariance*

Compares **group means** of one outcome **while adjusting for another variable (covariate)** that also influences the outcome.

**Example:**  
You want to compare the **math test scores** of students taught using methods A, B, and C — but students started with different **previous GPA** levels.

> - IV: Teaching Method  
> - DV: Math Test Score  
> - Covariate: Previous GPA  
> - ➤ Use ANCOVA to control for GPA before comparing test scores.

<img width="1861" height="1117" alt="image" src="https://github.com/user-attachments/assets/e68b16fe-8c24-4c41-b37e-bfa44d85312a" />

<img width="1818" height="1117" alt="image" src="https://github.com/user-attachments/assets/57edb38b-1f96-404d-901d-f0ad17036be2" />

---

## 🔹 3. MANOVA – *Multivariate Analysis of Variance*

Tests group differences for **two or more dependent variables** at the same time, **considering their relationships**.

**Example:**  
You compare teaching methods A, B, and C to see their effect on both **math test scores** and **class attendance rates**.

> - IV: Teaching Method  
> - DVs: Math Score, Attendance %  
> - ➤ Use MANOVA to analyze combined outcomes together.

<img width="1800" height="867" alt="image" src="https://github.com/user-attachments/assets/4bdb8425-cd31-49be-8f35-5303fd088298" />


<img width="1912" height="1117" alt="image" src="https://github.com/user-attachments/assets/421841e5-263c-45bf-a966-96fc381a1231" />

---

## 🔹 4. MANCOVA – *Multivariate Analysis of Covariance*

Extends MANOVA by **including covariates** — tests group differences across multiple dependent variables while **controlling for other variables**.

**Example:**  
You evaluate how teaching methods A, B, and C affect both **math scores** and **attendance**, while controlling for **previous GPA**.

> - IV: Teaching Method  
> - DVs: Math Score, Attendance %  
> - Covariate: Previous GPA  
> - ➤ Use MANCOVA to see real group differences after adjusting for GPA.

<img width="1863" height="1117" alt="image" src="https://github.com/user-attachments/assets/6c775242-ac58-4c07-bc52-8ed51aed4541" />

<img width="1912" height="1117" alt="image" src="https://github.com/user-attachments/assets/6a1cbf11-7b92-4f29-bb44-000549b9affc" />


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
