# UPI Transaction Forecasting & Capacity Planning

## 📊 Project Overview

This project analyses **monthly UPI transaction volume and transaction value** to forecast future transaction activity and support a business decision around **payment-processing infrastructure capacity**.

The analysis uses **8 years of monthly data (2018–2025)** and approaches the problem from a Business Analytics perspective:

> **When should additional UPI processing capacity be added to avoid future capacity constraints?**

The project combines exploratory time-series analysis, growth analysis, forecasting, out-of-sample model validation, and capacity planning.

---

## 🎯 Business Objective

The analysis addresses six key questions:

* How are UPI transaction volume and value growing?
* Is the growth pattern linear, exponential/multiplicative, or changing over time?
* Are there any major disruptions or structural changes?
* Do transaction volume and transaction value follow similar patterns?
* How is average transaction size changing?
* Which forecasting approach provides the most reliable predictions?

The final objective is to determine **when transaction volume is likely to approach or exceed the company's current processing capacity of 35 billion transactions per month**.

---

## 📁 Dataset

The dataset contains monthly observations with the following variables:

| Variable                         | Description                                 |
| -------------------------------- | ------------------------------------------- |
| `Date`                           | Month of observation                        |
| `Transaction_Volume_Billion`     | Monthly UPI transaction volume in billions  |
| `Transaction_Value_INR_Trillion` | Monthly UPI transaction value in ₹ trillion |

### Dataset Period

**January 2018 – December 2025**

**Frequency:** Monthly
**Observations:** 96

---

## 🔍 Analytical Approach

### 1. Exploratory Time-Series Analysis

* Data quality and missing-value checks
* Time-series visualization
* Monthly and year-on-year growth analysis
* Trend identification
* Seasonality assessment
* Structural disruption analysis

### 2. Growth Analysis

Linear and logarithmic trend specifications were compared to determine whether UPI activity follows a simple linear trajectory or a multiplicative growth pattern.

The analysis indicates that the series exhibits a **strong multiplicative growth pattern**, making simple linear forecasting less appropriate for long-term prediction.

### 3. Transaction Volume vs Transaction Value

The relationship between transaction volume and transaction value was examined using:

* Level correlation
* Growth-rate correlation
* Comparative time-series analysis

### 4. Average Transaction Size

Average transaction size was calculated as:

**Average Transaction Size = Transaction Value / Transaction Volume × 1000**

This provides an estimate of the average INR value processed per transaction.

### 5. Structural Change Analysis

The historical series was examined for unusual movements and potential structural changes.

A notable disruption was observed around **2020**, followed by a return towards the longer-term growth trajectory.

### 6. Out-of-Sample Forecasting

The final **12 months of historical data were treated as unseen test data**.

The forecasting workflow therefore followed:

**Training Data → Forecast → Compare with Actual Test Data → Evaluate Accuracy → Select Model**

This prevents model selection based solely on historical fit.

---

## 📈 Forecasting Models

Multiple forecasting approaches were evaluated, including:

* Naïve benchmark
* Drift
* Seasonal naïve
* Linear trend
* Log-linear trend
* Exponential Smoothing / ETS models

### Selected Model

**ETS(M,M,M) — Exponential Smoothing**

The ETS model was selected based on its **out-of-sample forecasting performance**.

ARIMA was not used as the primary model because the data's multiplicative growth structure was better captured by the selected ETS specification.

---

## 📊 Key Findings

### Transaction Growth

Transaction volume increased from approximately:

**0.53 billion → 26.43 billion transactions per month**

between 2018 and 2025.

Transaction value increased from approximately:

**₹0.68 trillion → ₹44.29 trillion per month**

over the same period.

### Volume and Value

Transaction volume and transaction value show a very strong positive relationship, while differences in their growth rates reflect changes in average transaction size.

### Average Transaction Size

Average transaction size increased over the long-term period, although recent movements indicate that transaction volume growth has become increasingly important to overall UPI activity.

### Forecasting Performance

The selected ETS model demonstrated strong out-of-sample forecasting performance, with substantially lower forecast errors than simple benchmark approaches.

---

## 🚦 Capacity Planning

The company's assumed current processing capacity is:

### **35 billion transactions per month**

The selected forecasting model indicates that transaction volume is expected to approach this threshold during **2026** and cross the threshold around **June 2026**.

### Management Recommendation

Capacity expansion should **not wait until the infrastructure reaches its absolute limit**.

The recommended approach is to begin expansion planning before the forecast reaches the 35-billion threshold, allowing sufficient time for implementation and reducing operational capacity risk.

Prediction intervals are also considered to account for uncertainty around the point forecasts.

---

## 🛠️ Tools & Technologies

* **R**
* Time Series Analysis
* Exponential Smoothing / ETS
* Statistical Analysis
* Forecast Accuracy Evaluation
* Data Visualization
* Capacity Planning
* Quarto

### R Packages

Key packages used include:

```r
tidyverse
forecast
tseries
lubridate
scales
strucchange
```

---

## 📂 Repository Structure

```text
UPI_Transaction_Forecasting/
│
├── UPI_CASE_STUDY.html
├── UPI_CASE_STUDY_files/
├── UPI_CASE_STUDY.qmd
├── UPI_Transactions_Case_study.csv
└── README.md
```

### File Description

| File                              | Purpose                                      |
| --------------------------------- | -------------------------------------------- |
| `UPI_CASE_STUDY.html`             | Complete rendered analytical report          |
| `UPI_CASE_STUDY_files/`           | Supporting files required by the HTML report |
| `UPI_CASE_STUDY.qmd`              | Reproducible Quarto source file              |
| `UPI_Transactions_Case_study.csv` | Dataset used for analysis                    |
| `README.md`                       | Project documentation                        |

---

## 📑 Project Deliverables

The analysis provides:

1. Statistical and time-series analysis
2. Reproducible R code
3. Forecasting model comparison
4. Forecast accuracy evaluation
5. Actual vs forecast visualizations
6. 12-month transaction and capacity forecasts
7. Capacity-risk assessment
8. Final management recommendation

---

## 🌐 Interactive Analysis

**View the complete rendered analysis:**

`UPI_CASE_STUDY.html`

---

## 💡 Business Analytics Takeaway

The key lesson from this project is:

> **Forecasting is not the final objective. The value of analytics comes from translating forecasts into actionable business decisions.**

In this case, the forecast provides management with an evidence-based basis for deciding **when additional UPI processing infrastructure should be planned and deployed**.

---

## 👤 Author

**Sachin Laksh**

MSc Business Analytics | Aspiring Business Analyst

**Areas of Interest:**
Business Analytics • Supply Chain Analytics • Time Series Forecasting • Data-Driven Decision Making

---

## 📌 Disclaimer

This project is an analytical case study based on the provided dataset and is intended for educational and portfolio purposes. Forecasts and capacity recommendations are dependent on the assumptions and historical patterns present in the dataset.
