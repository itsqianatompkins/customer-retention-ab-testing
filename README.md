# customer-retention-ab-testing
End-to-end lifecycle marketing analytics framework for a D2C e-commerce platform. Features SQL cohort extraction, Python predictive modeling (Random Forest &amp; Neural Networks), A/B test lift architecture, and a Power BI retention dashboard to optimize margins and maximize win-back ROI.

##
<img width="870" height="643" alt="image" src="https://github.com/user-attachments/assets/27518066-1e1a-49a8-859b-da14a8f60b14" />



(This case study uses fictional company data with legitimate analytical methods and is intended solely to demonstrate professional skills and capabilities while pursuing career opportunities.)

## Background
Bookmark’d, a rapidly growing direct-to-consumer (D2C) online bookstore platform, faces a critical margin and customer retention challenge in a highly competitive digital marketplace. Historically, the brand managed customer lifecycle retention reactively, deploying blanket promotional discounts and win-back emails across its entire inactive database. While this broad approach secured short-term transaction spikes, it severely eroded net profit margins, accelerated advertising fatigue, and trained consumers to only purchase when offered steep discounts. To protect profitability and optimize marketing spend, Bookmark’d is transitioning to a proactive lifecycle optimization framework, leveraging predictive analytics to target customer accounts based on transactional behavior and explicit genre affinities before their churn risk peaks.

## Objective
The objective of this project is to analyze historical subscriber data and transaction patterns to build, fine-tune, and compare advanced predictive classification models (Logistic Regression, Multilayer Perceptron Neural Networks, and Random Forests) that isolate high-probability purchase signals. By evaluating model metrics such as Area Under the ROC Curve (AUC) and calculating decile-based cumulative gains and lift, this analysis establishes a statistically rigorous A/B testing framework. Ultimately, these models translate data-driven probabilities into prescriptive marketing strategies, ensuring that retention budgets are deployed exclusively to the highest-yield customer cohorts to maximize customer lifetime value (CLV) and win-back campaign ROI.

## Data Scope & Timeframe
* **Cohort Size:** 15,000 active user accounts evaluated for campaign readiness.
* **Granularity:** 10 sequential operational deciles (each representing 10% of the total cohort, or 1,500 accounts per tier).
* **Feature Dimensions Evaluated:** 
  * Static demographic profiles.
  * Deep genre affinity histories.
  * Standard Recency, Frequency, and Monetary Value (RFM) transaction metrics.
 
## Overview
This repository contains the end-to-end predictive modeling framework designed to optimize lifecycle marketing campaigns for **Bookmark'd**. When launching marketing initiatives to an active user base, generic "blast" campaigns introduce high overhead costs and customer fatigue. 

This project transitions marketing operations from broad targeting to high-efficiency, data-driven segments. By evaluating user histories through multiple behavioral paradigms, we isolate the highest-velocity buyers. The final optimization framework allows marketing teams to accurately select campaign cut-offs that maximize conversion rates while minimizing budget waste.

## Executive Summary
The primary goal was to determine the most cost-effective framework for predicting conversion behavior and to simulate the financial return of a targeted lifecycle campaign. 

* *Genre Affinity Paradigm:* Performed best among baseline frameworks (AUC: 0.752), indicating that specific content preferences are highly predictive of purchasing intent.
  
<img width="733" height="488" alt="Screenshot 2026-07-18 182727" src="https://github.com/user-attachments/assets/42faba75-54b1-468a-ac4e-d39643a3129a" />


### Core Methodology & Evolution
1. **Baseline Frameworks:** We initially built three distinct benchmark models using Logistic Regression to evaluate different feature sets:
   * *Demographic Paradigm:* Performed poorly (AUC: 0.573), proving that *who* a user is has very little predictive power regarding immediate purchasing decisions.
   * *RFM Metrics Paradigm:* Performed strongly (AUC: 0.738), showing that historical transaction patterns provide a solid behavioral anchor.
   * *Genre Affinity Paradigm:* Performed best among baseline frameworks (AUC: 0.752), indicating that specific content preferences are highly predictive of purchasing intent.
2. **Algorithmic Expansion:** To capture non-linear relationships, we tested an iterative Neural Network architecture. While a finely tuned 10-node layer matched our baseline performance (AUC: 0.751), increasing layer complexity to 30 and 50 nodes introduced immediate overfitting and noise vulnerabilities, dropping the test performance down to 0.749.

<img width="470" height="52" alt="Screenshot 2026-07-18 182739" src="https://github.com/user-attachments/assets/a8ba5025-0901-469a-a2b2-1f607e50dede" />

3. **The Winning Framework:** A hyperparameter-optimized **Random Forest Classifier** was deployed as the final production model. By utilizing a grid search to discover an optimal tree bootstrapping sample fraction of `0.75` (with 1,000 estimators and a constrained max depth of 10), the model achieved a peak test performance of **AUC: 0.796**, successfully neutralizing data noise and stabilization challenges.

<img width="639" height="486" alt="Screenshot 2026-07-18 182757" src="https://github.com/user-attachments/assets/d1917aa0-8d8b-4549-aab0-5605ae7bd30b" />

## Core Business Insights
The final model was deployed against a simulated lifecycle campaign targeting 15,000 accounts to map out real-world performance gains:

* **Front-Loaded Conversion Concentration:** The predictive framework successfully consolidated the vast majority of active buyers into the top tiers. Decile 1 alone captured **565 buyers** out of 1,500 accounts—yielding a **4.23x lift** over a random guessing baseline strategy.
* **The 30% Efficiency Boundary:** By the time the campaign reaches the end of Decile 3 (the top 30% of the audience), the model captures **71.65% of all total buyers** available in the entire 15,000-user ecosystem (958 cumulative buyers out of 1,335 total conversions). 
* **Diminishing Returns Beyond the Cut-off:** Targeting the remaining 70% of the user base (Deciles 4 through 10) requires 70% more budget but only yields a fractional 28.35% of remaining conversions. Deciles 9 and 10 combine for a mere 54 total conversions across 3,000 targeted accounts, proving that expanding the campaign past the threshold actively dilutes profitability.

---

## Financial Incrementality Simulation
Using an operational budget model of $0.50 marketing overhead cost per account and a gross value of $25.00 generated per successful conversion, a strict **Top 30% Target Optimization Boundary** yields the following financial performance:

| Metric | Performance Value |
| :--- | :--- |
| **Total Evaluated Volume** | 15,000 accounts |
| **Optimized Target Volume (Top 30%)** | 4,500 accounts targeted |
| **Total Campaign Budget Consumed** | $2,250.00 |
| **Gross Campaign Revenue Generated** | $23,950.00 |
| **Net Profit Realized** | **$21,700.00** |
| **Program Return on Investment (ROI)** | **964.44%** |

<img width="528" height="289" alt="Screenshot 2026-07-18 182817" src="https://github.com/user-attachments/assets/49c70187-c6a6-4944-8d84-708d3f1756dc" />

---

## Recommendations & Next Steps

1. **Enforce the 30% Operational Cut-off:** Hard-code the campaign dispatch pipelines to automatically truncate lifecycle marketing distributions at the 30th percentile boundary. This locks in 71.65% of potential revenue while permanently saving 70% ($5,250.00) of the overhead budget that would have been wasted on low-probability accounts.
2. **Prioritize Behavioral Intent Over Demographics:** Sunset any marketing acquisition or retention models relying strictly on static demographic profiles. Production scoring systems must prioritize deep **genre affinity metrics** combined with **RFM transaction intervals** to keep predictive outputs sharp.
3. **Automate the Random Forest Scoring Pipeline:** Deploy the optimized `RandomForestClassifier` configuration (`max_depth=10`, `max_samples=0.75`, `n_estimators=1000`) into a weekly batch-scoring cron job. This ensures that user account scores dynamically recalculate as engagement profiles change, keeping the top 3 deciles continuously refreshed.
