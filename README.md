<div align="center">
  
### UIDAI Hackathon 2026 Analytics

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-green?logo=pandas)
![Prophet](https://img.shields.io/badge/Prophet-Forecasting-orange)
![License](https://img.shields.io/badge/License-MIT-yellow)

<p align="center">
<em>Unlocking Societal Trends in Aadhaar Enrolment and Updates</em>
</p>

</div>

---

## 📜 Table of Contents

- [Overview](#-overview)
- [Problem Statement](#-problem-statement)
- [Key Features](#-key-features)
- [Tech Stack](#-tech-stack)
- [Dataset Details](#-dataset-details)
- [Methodology](#-methodology)
- [Key Findings & Results](#-key-findings--results)
- [Future Scope](#-future-scope)
- [Contributors](#-contributors)

---

## 🔍 Overview

**Aadhaar Drishti** is a predictive analytics solution developed for the **UIDAI Data Hackathon 2026**.

As Aadhaar saturation nears 100% among the adult population, the operational focus of UIDAI is shifting from **Acquisition** to **Lifecycle Management** (Biometric updates for children, demographic corrections, etc.). This project leverages advanced **Time-Series Forecasting** to predict regional demand shifts and identify operational anomalies.

📄 **[View Complete Analysis Report (PDF)](Aadhaar_Hackathon_Analysis.pdf)**

---

## 🎯 Problem Statement

The challenge addressed in this repository is: **"Unlocking Societal Trends in Aadhaar Enrolment and Updates."**

Specific objectives include:

- **Predictive Modelling**: Forecasting future demand for Enrolment vs. Biometric Updates.
- **Societal Indicators**: Using Age 0-5 enrolment data as a proxy for birth registration efficiency.
- **Anomaly Detection**: Identifying irregular spikes in demographic updates (potential fraud or data entry errors).

---

## ✨ Key Features

| Feature | Description |
|---------|-------------|
| 🤖 **Automated Data Pipeline** | A robust script that ingests nested ZIP files, standardizes column names, and cleanses data automatically. |
| 🔮 **Dual-Model Forecasting** | Implements Facebook Prophet (for seasonality) and Holt-Winters (for trend) to compare and select the best forecasting method. |
| 📅 **Granular Analysis** | Shifts from monthly to Weekly (W-SUN) aggregation to capture operational seasonality (e.g., the "Sunday Dip"). |
| 🧹 **Data Auditing** | Includes a strict deduplication logic that identified and removed 470k+ duplicate demographic records. |
| 🧩 **State Clustering** | Automatically classifies states into "Growth" (High Enrolment) vs. "Maintenance" (High Updates) clusters. |

---

## 🛠 Tech Stack

- **Language**: Python 3.x
- **Data Manipulation**: Pandas, NumPy
- **Visualization**: Matplotlib, Seaborn
- **Forecasting**: Prophet (Facebook), statsmodels (Holt-Winters)
- **Machine Learning Metrics**: Scikit-learn
- **Environment**: Jupyter Notebook / Google Colab

---

## 📊 Dataset Details

The analysis utilizes anonymized datasets provided by UIDAI (aggregated counts per region/date).

| Dataset | Records (Approx) | Description |
|---------|------------------|-------------|
| **Enrolment** | 983,000+ | New Aadhaar generations, segmented by Age (0-5, 5-18, 18+). |
| **Biometric** | 1,766,000+ | Mandatory updates (iris/fingerprint) for children turning 5 and 15. |
| **Demographic** | 1,598,000+ | Address, Name, and Mobile number updates. |

> ⚠️ **Note**: Raw data is not included in this repo due to size constraints.

---

## ⚙️ Methodology

### 1. Preprocessing & Cleaning
- **Path Extraction**: Auto-detection of enrol, bio, and demo folders inside ZIPs.
- **De-duplication**: Removed ~22% of the Demographic dataset (duplicates) to prevent inflated demand metrics.
- **Imputation**: Null values in numerical columns filled with 0 (implying no transaction).

### 2. Feature Engineering
- **Weekly Aggregation**: Converted noisy daily data into Weekly-Sunday frequency.
- **Metric Synthesis**: Created a Total_Activity metric for heatmap generation.

### 3. Forecasting Strategy
- **Prophet**: Configured with `yearly_seasonality=False` (due to <1 year data) and `weekly_seasonality=True`. Added Indian Country Holidays.
- **Validation**: Used Time-Series Cross-Validation (Rolling Origin) to calculate MAE/RMSE.

---

## 📉 Key Findings & Results

### 1. The "Biometric Surge"
While new enrolments are stabilizing (**Saturation Phase**), Biometric Updates are showing a linear growth trend (**Maintenance Phase**).

> 💡 **Insight**: Centers need to reallocate ~15% of resources from Enrolment counters to Biometric Update counters.

### 2. The 0-5 Age Proxy
Enrolment trends in the **0-5 Age Group** correlate strongly with hospital birth integration efficiency.

> 💡 **Insight**: "Bal Aadhaar" initiatives are succeeding significantly in UP and Bihar.

### 3. State Clustering
- **Cluster A (Growth)**: Bihar, UP (Focus: New Acquisitions)
- **Cluster B (Maintenance)**: Kerala, Maharashtra (Focus: Updates)

### 4. ABC Classification Framework

| Ordering | Recommendation | Description |
|----------|----------------|-------------|
| A>B>C | **Maintain (Ideal)** | Normal healthy pattern |
| B>A>C | **Investigate Usage Drop** | Biometric usage below expected |
| C>B>A | **Critical: Not Translating to Usage** | High enrolments but low usage |

### 5. Anomalous Districts
- **47 districts** identified with unusually high demographic update volumes (>130,000)

### Data Period
- **Historical Data**: March 2025 - December 2025
- **Forecast Period**: January 2026 - March 2026

---

## � Project Structure

```
├── Aadhar_Hackathon final.ipynb  # 🧠 Main Analysis Notebook
├── requirements.txt              # 📦 Python dependencies
├── README.md                     # 📖 Project Documentation
├── assets/                       # 📊 Generated Charts
│   ├── Enrolment_Forecast.png
│   ├── Biometric_Forecast.png
│   └── State_Heatmap.png
└── .gitignore                    # 🛡️ Ignored files (data/zips)
```

---

## �🚀 Future Scope

- **Hyper-Local Forecasting**: Drill down from State level to District/Tehsil level predictions.
- **Migration Tracking**: Correlate "Address Change" spikes with seasonal labor migration patterns.
- **Real-time Dashboard**: Integrate the Prophet model API directly into the live dashboard infrastructure.

---

## 👥 Contributors

- **Team ByteByUID** - UIDAI Hackathon 2026
-  [@atul-1603](https://github.com/atul-1603) 
- [@vedamehar](https://github.com/vedamehar) 
---

<div align="center">
<sub>Built with ❤️ for the UIDAI Hackathon 2026. Data used is anonymized and aggregated.</sub>
</div>
