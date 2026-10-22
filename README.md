# 📊 Using R to Disprove Layoff Bias & Decode Compensation Dynamics (IBM HR Analytics)

> **An advanced people analytics project utilizing rigorous statistical hypothesis testing and linear regression modeling in R to audit workforce restructuring claims, evaluate compliance risk, and decode compensation drivers.**

---

## 📌 Executive Summary

People analytics operates at the intersection of business strategy, human capital management, and legal compliance. When organizational restructurings trigger workforce reductions, relying on intuition or surface-level dashboards is insufficient for defending company practices against formal grievances.

This project—accompanying the case study by Nate Mulatu—uses the **IBM HR Analytics Attrition Dataset** to address two critical business objectives:

1. **Risk & Compliance Management:** Evaluating formal employee grievances alleging systemic age and tenure bias during layoffs using rigorous two-sample hypothesis testing.


2. **Compensation Equity:** Uncovering the primary drivers of `MonthlyIncome` across the organization using simple and multiple linear regression models, separating correlation from operational causality.



---

## 🛠️ Tech Stack & Libraries

* **Language:** R (R Markdown / Notebook)
* **Core Base Packages:** `stats` (`t.test`, `lm`, `cor`), `graphics` (`boxplot`, `pairs`)


* **Data Manipulation:** Base R indexing, factor creation with ordered education levels



---

## 🔍 Act I: Risk, Compliance & Hypothesis Testing (Auditing Layoff Bias)

Following an organizational restructuring, former employees filed formal grievances alleging discriminatory targeting of older and more senior staff. To test these claims objectively, we implemented statistical audits in R.

### 1. Baseline Correlation & Data Exploration

* Extracted numeric subsets (`Age`, `TotalWorkingYears`) to evaluate collinearity and baseline workforce experience.


* Computed correlation matrices confirming intuitive career progression dynamics.


* Generated scatterplot matrices (`pairs`) mapping the joint distributions of `MonthlyIncome`, `Age`, and `TotalWorkingYears`.



### 2. Testing Claim 1: Layoff Bias & Age Distribution

* **Methodology:** Isolated age vectors for departed employees (`Attrition == "Yes"`) versus retained staff (`Attrition != "Yes"`) and executed a two-sample $t$-test (`t.test(yes_age, no_age)`).


* **Statistical Finding:** The analysis yielded a highly significant $p$-value ($1.38 \times 10^{-8}$), but **refuted** the employee's claim. The mean age of departing staff was significantly *younger* than the retained group, proving the restructuring did not systematically target older workers.



### 3. Testing Claim 2: Tenure & Employee Number Bias

* **Methodology:** Evaluated `EmployeeNumber` (as a proxy for hire order/tenure) using a two-sample $t$-test (`t.test(yes_empno, no_empno)`) to audit whether longer-tenured employees were disproportionately impacted.



---

## 💰 Act II: Decoding Compensation Dynamics (Linear Regression)

To understand salary structures and ensure internal pay equity, we transitioned from classification/attrition analysis to parametric regression modeling.

* **Model 1 (Simple Linear Regression):** Evaluated `MonthlyIncome ~ Age` to establish the baseline linear growth rate of compensation relative to chronological age.


* **Model 2 (Multiple Linear Regression):** Extended the analysis to `MonthlyIncome ~ Age + TotalWorkingYears` to control for cumulative experience and isolate the true drivers of compensation scaling.



---

## 📊 Exploratory Data Analysis & Feature Engineering

The workflow includes robust feature engineering and structured visualization scripts:

* **Education Factor Mapping:** Converted numeric education codes (1 to 5) into an ordered factor (`EducationLabel`) with explicit levels: *Below College*, *College*, *Bachelor*, *Master*, and *Doctor*.


* **Comparative Boxplots:** Analyzed distributions of `Age`, `TotalWorkingYears`, and `MonthlyIncome` across education tiers and attrition statuses to inspect organizational tiering and variance.


## 📂 Repository Structure

```text
📦 IBM_HR_analytics_project_using_R
 ┣ 📜 HR-Employee-Attrition.csv       # Main dataset containing employee records and metrics
 ┣ 📜 HR_Data_Dictionary.pdf          # Documentation explaining the employee attrition dataset columns
 ┣ 📜 IBM_Analysis.Rmd                # R Markdown notebook containing code, analysis, and narrative
 ┗ 📜 README.md                       # Project overview and documentation
