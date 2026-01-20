# 🇮🇳 Aadhaar Drishti  
### UIDAI Hackathon 2026 — Analytics Track  
**Unlocking Societal Trends in Aadhaar Enrolment and Updates**

---

## 📌 Overview

**Aadhaar Drishti** is a predictive analytics solution developed for the **UIDAI Data Hackathon 2026**.

As Aadhaar saturation approaches **100% among the adult population**, UIDAI’s operational focus is shifting from **Acquisition** to **Lifecycle Management** (biometric updates, demographic corrections, child enrolments, etc.).

This project leverages **advanced time-series forecasting** to:

- Predict regional demand shifts  
- Detect operational anomalies  
- Support data-driven resource allocation  

---

## 🎯 Problem Statement

**“Unlocking Societal Trends in Aadhaar Enrolment and Updates.”**

### Objectives

- **Predictive Modelling**
  - Forecast future demand for enrolments vs. biometric updates

- **Societal Indicators**
  - Use **Age 0–5 enrolment trends** as a proxy for birth registration efficiency

- **Anomaly Detection**
  - Identify irregular spikes in demographic updates indicating potential fraud or errors

---

## ✨ Key Features

- **Automated Data Pipeline**
  - Ingests nested ZIP files
  - Auto-detects enrolment, biometric & demographic folders
  - Standardizes column names and cleans data

- **Dual-Model Forecasting**
  - Facebook Prophet (seasonality & holidays)
  - Holt-Winters (trend-focused)
  - Model selection via validation metrics

- **Granular Temporal Analysis**
  - Daily → Weekly (W-SUN) aggregation
  - Captures operational seasonality (e.g., *Sunday Dip*)

- **Strict Data Auditing**
  - Removed **470,000+ duplicate records**
  - Prevents inflated demand estimates

- **State-Level Clustering**
  - Growth States vs. Maintenance States classification

---

## 🛠 Tech Stack

### Programming & Analytics
- Python 3.x
- Pandas, NumPy

### Visualization
- Matplotlib
- Seaborn

### Forecasting
- Facebook Prophet
- Statsmodels (Holt-Winters)

### Evaluation
- Scikit-learn (MAE, RMSE)

### Environment
- Jupyter Notebook / Google Colab

---

## 📊 Dataset Details

| Dataset       | Records (Approx.) | Description |
|---------------|------------------|-------------|
| Enrolment     | 983,000+         | New Aadhaar enrolments by age (0–5, 5–18, 18+) |
| Biometric     | 1,766,000+       | Mandatory biometric updates |
| Demographic   | 1,598,000+       | Address, name, and mobile updates |

> ⚠️ **Note:**  
> Raw data is not included.  
> Place `Aadhar Dataset Hackathon.zip` in the project root.

---

## ⚙️ Methodology

### 1. Preprocessing & Cleaning
- Auto-detect dataset folders
- Removed ~22% duplicate demographic records
- Filled null numeric values with zero

### 2. Feature Engineering
- Weekly (Sunday-ending) aggregation
- Created `Total_Activity` metric

### 3. Forecasting Strategy
- Prophet with weekly seasonality
- Indian holidays added
- Rolling-origin cross-validation

---

## 💻 Installation & Usage

### Clone the Repository
```bash
git clone https://github.com/YourUsername/aadhaar-hackathon-analytics.git
cd aadhaar-hackathon-analytics
