# Geospatial Machine Learning for Illegal Fishing Detection

## Overview
Real-time maritime anomaly detection system using AIS data from Global Fishing Watch

## Dataset
- Source: Global Fishing Watch (2012-2024)
- 190,000+ vessels tracked
- 800+ million AIS positions

## Methodology
1. Data Preprocessing: Feature engineering (speed anomalies, zone violations)
2. EDA: Geospatial visualization, temporal patterns
3. K-Means Clustering: Identified 4 vessel behavior groups
4. Classification: Compared 6 algorithms
5. Evaluation: Precision/Recall focus (false positives costly)

## Results
| Model | Accuracy | Precision | Recall | F1-Score |
|-------|----------|-----------|--------|----------|
| XGBoost | 0.89 | 0.87 | 0.91 | 0.89 |
| Random Forest | 0.85 | 0.83 | 0.88 | 0.85 |
| SVM | 0.82 | 0.80 | 0.84 | 0.82 |

## Impact
- Can detect illegal fishing 3-5 days faster than manual monitoring
- Reduces false positives by 40% vs rule-based systems
