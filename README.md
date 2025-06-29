# AI-Powered Quality Control System for Automotive Parts Manufacturing  

AI-Powered Quality Control System for Automotive Parts Manufacturing using Bosch Sensor Data. Includes XGBoost modeling, SPC, Root Cause Analysis, DOE, FMEA simulation, Supplier Quality Variance, Pareto Charts, and Process Mapping.

![Quality Engineering](https://img.shields.io/badge/domain-manufacturing-blue.svg) ![XGBoost](https://img.shields.io/badge/model-xgboost-green.svg) ![SPC](https://img.shields.io/badge/statistics-SPC-orange.svg)

## Project Overview

This project simulates a complete AI-based quality engineering pipeline for the automotive manufacturing sector. It leverages Bosch's real-world production sensor data to build defect classification models, perform root cause analysis, simulate supplier drift, apply SPC techniques, and generate a simplified FMEA with visual tools such as Pareto charts and process flow mapping.

> Notebook: `Engineer_Quality.ipynb`

---

## Goal

To automate defect detection, root cause diagnosis, and quality variance analysis using machine learning and quality engineering tools. The goal is to provide a simulated environment that replicates day-to-day responsibilities of a Quality Engineer in an automotive parts facility.

---

## Intended Audience

- Quality Engineers  
- AI/ML Professionals in Manufacturing  
- Plant Operations Managers  
- Six Sigma / SPC Analysts  
- Supplier Development Engineers  

---

## 🛠 Strategy & Pipeline Steps

### 1. Data Loading & Preprocessing
- Mounted Google Drive to access Bosch data: `train_numeric.csv`, `train_date.csv`, `train_categorical.csv`  
- Loaded a subset (100,000 rows) due to memory limits  
- Missing values handled with `.fillna(-1)`  

### 2. Inline Defect Detection (XGBoost)
- Classification model to predict part failure using `Response` as target  
- Train/test split with `stratify=y` to preserve class imbalance  
- Model trained using `XGBClassifier` with logloss eval metric  
- Classification report highlights class 1 (fail) performance  

### 3. Feature Importance Analysis
- Extracted top 10 features based on model weights  
- Horizontal bar chart plotted to reveal most critical sensor stations impacting outcomes  

### 4. Statistical Process Control (SPC)
- Process durations calculated from `train_date.csv` timestamp range  
- X̄ chart plotted using mean and ±3σ to show process variation and anomalies  
- Helps identify stations going out of control  

### 5. Root Cause Analysis (Correlation Matrix)
- Correlation between features and the failure label  
- Top 10 sensor correlations with defects extracted  
- Visualized using seaborn heatmap to identify redundant and key contributors  

### 6. Quality Improvement Initiative
- Removed noisy/highly correlated features  
- Retrained the model and compared recall scores to demonstrate impact of corrective actions  

### 7. Supplier Quality Simulation
- Simulated 3 batches (suppliers A, B, and C) with induced signal drift  
- Evaluated defect rates across simulated suppliers to reflect incoming material quality variation  

### 8. DOE (Design of Experiments)
- Sensor variable artificially modified to simulate process change  
- Classifier retrained and evaluated to observe model robustness  
- Demonstrated impact of pressure/timing shifts in a test scenario  

### 9. FMEA & Control Plan
- Manually constructed simplified FMEA matrix for critical sensors  
- RPN (Risk Priority Number) calculated as Severity × Occurrence × Detection  
- Ranked sensor risks and proposed mitigation in markdown table format  

### 10. Pareto Chart for Defect Types
- Simulated defect causes (e.g., sensor drift, calibration error)  
- Plotted bar chart + cumulative line for classic 80/20 defect distribution analysis  

### 11. Process Flow Mapping
- ASCII-style process flow visual outlining production line checkpoints  
- Mimics standard automotive process flow (Material Input → Sensor → QC → Assembly/Rework)

---

##  Key Challenges

- Severe class imbalance (failures < 1%)  
- Over 970 features – difficult to interpret  
- High multicollinearity across stations  
- Low precision/recall for class 1 despite 99% overall accuracy  

---

## Problem Statement

Manual inspections are ineffective at identifying subtle quality deviations in sensor data. This project introduces a predictive analytics approach to reduce defects and improve response time to quality issues through automated diagnostics and preventive alerts.

---

## Dataset

- **Source:** [Kaggle - Bosch Production Line Performance](https://www.kaggle.com/competitions/bosch-production-line-performance)  
- **Files Used:**  
  - `train_numeric.csv`  
  - `train_date.csv`  
  - `train_categorical.csv`  

---

## Model Results

**Initial XGBoost:**
- Class 0: Precision 0.99, Recall 1.00  
- Class 1: Precision 0.23, Recall 0.04  
- Overall Accuracy: 0.99  

**After Feature Filtering:**
- Class 1 Recall improved to **0.06**  
- Showed marginal defect catch improvement after removing noise  

**DOE Simulation:**
- Validated sensor variation impact on model stability  

---

##  Visual Simulations Included

- XGBoost Feature Importance Chart  
- Cycle Time SPC (X-bar) Chart  
- Heatmap of Top Correlated Sensors  
- Pareto Chart for Defect Root Causes  
- ASCII Process Flow Mapping  
- FMEA Matrix with RPN Ranking  

---

## Trailer Documentation

-  Google Colab-compatible, modular notebook  
-  Suggestions for next version: SHAP, SMOTE, Real-time alerts  
-  Charts, reports, and risk matrices rendered with Matplotlib/Seaborn  

---

## Future Enhancements

- SHAP for sensor accountability and visual explanations  
- SMOTE for better class 1 training balance  
- Real-time streaming model with alert thresholds  
- Integration with supplier dashboards for quality scorecarding  
- Dynamic retraining pipeline with CI/CD in manufacturing cloud stack  

---

## References

- Bosch Dataset: [Kaggle Competition](https://www.kaggle.com/competitions/bosch-production-line-performance)  
- XGBoost Documentation: [xgboost.readthedocs.io](https://xgboost.readthedocs.io)  
- FMEA: Automotive Industry Action Group (AIAG) Manual  
- SHAP: Lundberg & Lee, NIPS 2017  

---

## 🧾 License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT)

---

> Developed by [Ronald Kalani](https://www.linkedin.com/in/ronaldkalani)  
> 📧 Contact: available on request  

