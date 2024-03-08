# [Energy Consumption Peak Demand Forecasting Dashboard](https://lookerstudio.google.com/reporting/1b7e2094-e024-42db-8b20-bcd6cd3dd199)


## Table of Contents
1. [Introduction](#1-introduction)
2. [Business Proposal | The Problem](#2-business-proposal--the-problem)
    - [Customer Classification](#21-customer-classification)
    - [Customer Bill Calculation Example](#22-customer-bill-calculation-example)
    - [More about the Problem](#23-more-about-the-problem)
3. [Proposed Solution](#3-proposed-solution)
4. [Dashboard Service Technicals](#4-dashboard-service-technicals)
5. [Flow Diagram](#5-flow-diagram)
6. [Full Data and Machine Learning Pipeline](#6-full-data-and-machine-learning-pipeline)
7. [Features to Add in the Future](#7-features-to-add-in-the-future)
8. [Reproducibility](#8-reproducibility)
9. [Business Viability Conclusion](#9-business-viability-conclusion)
10. [Acknowledgments](#10-acknowledgments)

---
## 1. Introduction 
<div align="justify">
In the energy sector, demand forecasting presents a persistent and evolving challenge. With the increasing integration of renewable energy sources to achieve net-zero goals by 2030 to 2050, the issue has become even more pressing. The adoption of renewables such as wind, solar, and nuclear introduces greater variability into the supply side of the grid, contributing to its complexity. While advancements in battery technology are expected to mitigate this volatility in the future, it remains a current reality.Accurate and tailored demand forecasting is crucial in mitigating disruptions to the grid, reducing energy consumption, and minimizing carbon footprint. It not only enhances grid efficiency and cost savings but also facilitates renewable energy integration and enables informed decision-making and resource allocation. Most importantly, it improves real-time demand balancing to prevent blackouts. The benefits of accurate demand forecasting are numerous and far-reaching.From a business perspective, this project aims to evaluate the viability of a peak demand prediction service for heavy power users in Ontario and provide a simple proof of concept. From a technical standpoint, it seeks to develop a robust data engineering pipeline incorporating best practices, along with an end-to-end MLOps framework for model monitoring and tracking.



---

## 2. Business Proposal|The problem
### 2.1 Customer Classification 
If you are a large electricity user, large is defined as a user using average monthly maximum hourly demand of 1MW and above and are considered Class A customers. They are able to curtail electricity. For those large users, 50-60% of their electricity bill cost is determined by their consumption during those 5 peak hours. That is called Global Adjustment. GA is used to cover the cost of building new electricity infrastructure in the province, regulated rates paid to electricity suppliers under contract, and the costs of delivering the province’s energy efficiency and conservation programs. Global Adjusted (GA) is calculated using the Class A users energy consumption on those peak 5 days which is known as a peak demand factor (PDF). Here is how the calculation works:

### 2.2 Customer Bill Calculation Example
There is a system-wide GA cost for a given month, for example, let's say for the month of May it's **999.6M**.

The class A large electricity client has a **Peak Demand Factor** of **0.00017749**.

His GA monthly charge is 999.6M * 0.00017749 = $ 177,419 monthly, around $2.1M.

The Peak Demand Factor is calculated as follows:

The Class A **clients consumption** during the top 5 demand peak hours (MWh) divided by the sum of the **top 5 system-wide Consumption Peaks (MWh)**.

### 2.3 More about the problem 
If you are interested in how GA works, more information can be found [here](https://www.ieso.ca/en/Sector-Participants/Settlements/Global-Adjustment-and-Peak-Demand-Factor)

---

## 3. Proposed Solution

The project aims to reduce the PDF value by accurately predicting the top 5 peak demand hours allowing users to decrease their consumption on those predicted days to reduce their GA contribution. The user will see the 5-day prediction uploaded automatically to the **Energy_Consumption_Forecasting_Dashboard** between late May and early October. The Dashboard services will also come with real-time forecasting for the next day's demand and 7 days ahead.

1. **Time Series Forecasting Service:(Business)**
   - Predicts day-ahead and 7-day-ahead energy consumption.
   - Targeted towards heavy electrical power users based in Ontario. (This is similar to IESO [peak tracker](https://ieso.ca/Sector-Participants/Settlements/Peak-Tracker) which forecasts, 1 day and 6 days ahead. Then lists the top 10 peak demand hours to help large utilities calculate their PDF and GA)

2. **Peak Demand Forecasting service:(Business)**
   - Predicts energy consumption for the 5 peak days during the summer to help businesses mitigate the Global Adjustment (GA) part of the bill.
   - Targeted towards Ontario-based users with a daily electrical an hourly monthly average demand of 1MW or more. (Class A) 

3. **Full Automated Dashboard. (Time series forecasting, Peak demand forecasting):**
   - Develop an end-to-end data pipeline and machine learning model pipeline for energy consumption forecasting.
   - The final product is a dashboard accessible via Google Looker Studio, tailored for internal teams of large electricity users.

This project is meant to be a proof of concept to assess if this service is viable both from a technical standpoint and business. For that to be achieved:

1. The model has to be good enough to make the business model viable
    - Very High accuracy predictions for peak demand days (otherwise, reimbursements from Large electricity user for wrong prediction out of/5 will eat at cashflow and revenue). Make consistent predictions to mitigate financial risk 
    - It has to perform better than base model predictions (Highest temperature/ Highest humidity are used)

2. Adhere to Data engineering, Machine learning, Mlops fundamentals and best practices to build robust pipelines and final product.

---

## 4. Dashboard Service Technicals
### Technologies Used:

- **Cloud**: AWS, GCP, Azure, or others
- **Experiment tracking tools**: MLFlow, Weights & Biases, and more.
- **Workflow orchestration**: Prefect, Airflow, Flyte, Kubeflow, Argo, and more.
- **Monitoring**: Evidently, WhyLabs/whylogs, and more.
- **CI/CD**: GitHub Actions, Gitlab CI/CD, and more.
- **Infrastructure as Code (IaC)**: Terraform, Pulumi, Cloud Formation, and more.

#### Data 

Ontario Demand data: 
Ontario Price data: 
Population 
gdp
holidays
weather 

---

## 5. Flow Diagram
...

---

## 6. Full Data and Machine Learning Pipeline
...

---

## 7. Features to add in the future
...

---

## 8. Reproducibility
...

---

## 9. Business Viability Conclusion
...

---

## 10. Acknowledgments
...

This project is done after going through the course material from [mlops-zoomcamp](https://github.com/MarwanH7/mlops-zoomcamp)

