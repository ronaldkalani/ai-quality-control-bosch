# AI-Powered Quality Control System for Automotive Parts Manufacturing  

AI-Powered Quality Control System for Automotive Parts Manufacturing using Bosch Sensor Data. Includes XGBoost modeling, SPC, Root Cause Analysis, DOE, and FMEA simulation.

![Quality Engineering](https://img.shields.io/badge/domain-manufacturing-blue.svg) ![XGBoost](https://img.shields.io/badge/model-xgboost-green.svg) ![SPC](https://img.shields.io/badge/statistics-SPC-orange.svg)

## Project Overview

This project simulates a real-world AI-powered quality control pipeline tailored for the automotive parts manufacturing industry. It leverages Bosch's production sensor data to detect defective parts, trace root causes, simulate supplier variation, and analyze statistical process control (SPC) and FMEA (Failure Modes and Effects Analysis).

> Notebook: `Engineer_Quality.ipynb`

---

## Goal

To automate part defect detection using advanced ML modeling while supporting root cause analysis, real-time monitoring, and supplier quality comparisons through a simulated quality assurance environment.

---

## Intended Audience

- Quality Engineers  
- AI/ML Practitioners in Manufacturing  
- Six Sigma / SPC Professionals  
- Supplier Quality Analysts  
- Operations & Plant Managers  

---

## 🛠 Strategy & Pipeline Steps

### 1. Data Loading & Handling
- Load `train_numeric.csv`, `train_date.csv`, `train_categorical.csv`
- Subset for memory optimization
- Preprocessing missing values and dtype warnings

### 2. Quality Inspection Simulation (XGBoost Classifier)
- Train/Test split using `train_test_split` with stratification  
- Binary classification: Pass (0) vs Fail (1)  
- Evaluation: Precision, Recall, F1-score  

### 3. Feature Importance Visualization
- Extract and visualize top 10 sensor features  
- Identify critical stations and lines impacting product quality  

### 4. SPC Monitoring (X̄ Chart)
- Calculate process durations from timestamps  
- Detect process stability using control limits (+3σ)

### 5. Root Cause Analysis (Correlation Matrix)
- Identify top 10 sensor correlations with failures  
- Detect sensor redundancy and mirrored responses  

### 6. Quality Improvement
- Remove highly correlated/noisy features  
- Retrain model and compare improvement on defect recall  

### 7. Supplier Simulation
- Simulate 3 batches with induced quality drift  
- Compare defect rates among suppliers  

### 8. DOE Simulation
- Modify a sensor value to simulate process drift  
- Measure model robustness using classification report  

### 9. FMEA & Control Plan
- Simulate risk scores using Severity × Occurrence × Detection  
- Generate RPN values and rank sensor failure modes

---

##  Challenges Faced

-  **Severe class imbalance** (~0.5% defective parts)
- **Low recall** for defect detection
- **970+ features** creating interpretability complexity
- **High redundancy** in sensor signals across stations

---

## Problem Statement

The manual QC process fails to catch subtle sensor anomalies before failures occur. This project provides a predictive model to preemptively detect failures, enabling preventive maintenance and process improvements.

---

## Dataset

- **Source:** [Kaggle - Bosch Production Line Performance](https://www.kaggle.com/competitions/bosch-production-line-performance)  
- **Files Used:**  
  - `train_numeric.csv`  
  - `train_date.csv`  
  - `train_categorical.csv`  

---

## Machine Learning Prediction & Outcomes

### Initial XGBoost Results:
- Class 0 (Pass): Precision **0.99**, Recall **1.00**  
- Class 1 (Fail): Precision **0.23**, Recall **0.04**  
- Accuracy: **0.99** (misleading due to imbalance)

### After Noise Filtering:
- Class 1 recall improved **marginally** to 0.06

### DOE Simulation:
- Stability confirmed for passing parts  
- Variation sensitivity slightly improved for failures

---

##  Trailer Documentation

- ☁️ Colab-compatible notebook with modular code  
-  SMOTE, SHAP, and threshold tuning suggested for next version  
-  Clear output visualizations for charts, heatmaps, and feature ranks  

---

## Future Enhancements (AGI Alignment – Conceptual)

- Integrate real-time sensor streaming and self-learning pipelines  
- Enable automated retraining and alert systems for sensor anomalies  
- Explore SHAP explainability for in-depth sensor accountability  

---

## References

-  Bosch Dataset: [Kaggle](https://www.kaggle.com/competitions/bosch-production-line-performance)  
-  XGBoost: [https://xgboost.readthedocs.io](https://xgboost.readthedocs.io)  
-  SHAP: Lundberg & Lee (2017)  
-  FMEA: AIAG Automotive Guidelines  

---

## 🧾 License
This project is released under the [MIT License](https://opensource.org/licenses/MIT).

---

>  Developed by [Ronald Kalani](https://www.linkedin.com/in/ronaldkalani) | 📧 Contact: available on request
