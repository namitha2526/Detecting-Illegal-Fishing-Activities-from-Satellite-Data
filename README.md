# Detecting Illegal Fishing Activities Using Satellite AIS Data

## Overview
Illegal, Unreported, and Unregulated (IUU) fishing is a major threat to marine ecosystems and global economic stability. Many fishing vessels intentionally disable tracking systems or operate outside permitted regions to avoid detection.  

This project leverages **Satellite AIS (Automatic Identification System) data** and **Machine Learning** to identify suspicious fishing behavior based on vessel activity patterns.

---

## Objectives
- Detect vessels exhibiting **suspicious fishing behavior**
- Classify vessel activity as **Normal** or **Potentially Illegal**
- Support maritime monitoring, enforcement authorities, and sustainability research

---

## Dataset Description
The dataset is derived from **Global Fishing Watch** monthly vessel activity summaries.

Each row represents the activity of a vessel in a specific ocean grid cell on a given date.

| Column | Description |
|--------|-------------|
| `date` | Activity date |
| `year`, `month` | Time-based grouping fields |
| `cell_ll_lat`, `cell_ll_lon` | Geographic position (latitude & longitude) |
| `flag` | Vessel nationality (ISO country code) |
| `geartype` | Type of fishing gear used (e.g., trawler, longline, purse seine) |
| `hours` | Total hours vessel stayed in the area |
| `fishing_hours` | Estimated hours spent actively fishing |
| `mmsi_present` | 1 = AIS identity broadcasted, 0 = AIS off (identity hidden) |

### Key Risk Indicators
- **AIS turned off (`mmsi_present = 0`)** → High suspicion
- **Fishing in regions outside country’s permitted waters**
- **High fishing intensity in deep ocean zones**
- **High-risk gear types associated with commercial illegal fishing**

---

## Data Preprocessing & Feature Engineering
- Converted `date` to appropriate datetime format
- Created time-based features:
  - `day_of_week`
  - `is_weekend`
  - `day_of_month`
- Derived spatial features:
  - `distance_from_equator = abs(latitude)`
  - `hemisphere = north / south`
- Calculated behavioral features:
  - `fishing_efficiency = fishing_hours / hours`
  
## Handling Class Imbalance
Illegal fishing cases are relatively fewer than normal fishing events.  
To avoid biased learning, we applied:
SMOTE (Synthetic Minority Oversampling Technique)
This balances both classes before model training.

---

## Models Used
Multiple machine learning models were trained and compared:

| Model | Purpose |
|-------|---------|
| Logistic Regression | Baseline, interpretable model |
| Decision Tree | Captures nonlinear patterns |
| Random Forest | Robust ensemble classification |
| XGBoost | High-performance boosted trees |
| SVM | Margin-based classification |
| KNN | Behavior similarity-based classification |
| Gaussian Naive Bayes | Probabilistic baseline |

Performance was evaluated using:
- Accuracy
- Precision
- Recall
- F1-Score
- ROC-AUC

> **Recall was prioritized** to avoid missing illegal activity cases.

---

## System Workflow
Satellite AIS Data → Preprocessing → Feature Engineering
→ Class Balancing (SMOTE) → Multi-Model Training
→ Suspicious Vessel Classification → Output / Alerts
---


---

## Real-World Applications
- Coast Guard surveillance & patrol optimization
- Fisheries management and maritime law enforcement
- Ocean sustainability and ecological protection
- NGO & government monitoring (e.g., Global Fishing Watch)

---

## Future Improvements
- Integrate Exclusive Economic Zone (EEZ) boundary data
- Apply LSTM/GRU sequence models for movement trajectory analysis
- Add Synthetic Aperture Radar (SAR) satellite verification
- Build real-time anomaly detection dashboard

---

## Repository Structure
├── data/ # AIS processed dataset
├── notebooks/ # Model development and EDA notebooks
├── models/ # Exported or saved ML models
├── visualizations/ # Plots and analytics outputs
├── README.md # Project documentation (this file)
└── requirements.txt # Dependencies

---

## Dependencies
pandas
numpy
matplotlib
seaborn
scikit-learn
xgboost
imblearn

---

## Author
**Namitha R**  
Computer Science & Engineering  

LinkedIn: https://www.linkedin.com/in/namitha-r-b52799310/  
GitHub: https://github.com/namitha2526  

---

## License
This project is released under the **MIT License**.


