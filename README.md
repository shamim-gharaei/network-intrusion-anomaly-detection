# Network Intrusion Anomaly Detection

A machine learning project for detecting PortScan attacks in network traffic using the CICIDS2017 dataset.

## Project Overview

This project focuses on distinguishing benign network traffic from PortScan activity using supervised machine learning.

The workflow includes:

- Data cleaning and preprocessing
- Exploratory data analysis
- Baseline model training
- Comparison of multiple classifiers
- Final Random Forest evaluation
- Feature importance analysis
- Saving the trained model and evaluation results

## Dataset

The project uses the PortScan subset of the CICIDS2017 dataset.

After preprocessing, the cleaned dataset contained:

- 213,777 network flows
- 78 predictive features
- 123,083 BENIGN samples
- 90,694 PortScan samples

## Models Evaluated

Three classification models were evaluated:

1. Logistic Regression
2. Decision Tree
3. Random Forest

Random Forest achieved the strongest overall performance and was selected as the final model.

## Final Model Performance

| Metric | Score |
|---|---:|
| Accuracy | 0.999906 |
| Precision | 1.000000 |
| Recall | 0.999779 |
| F1-score | 0.999890 |

The final confusion matrix was:

    [[24617     0]
     [    4 18135]]

Only four PortScan samples were incorrectly classified as BENIGN in the held-out test set.

## Important Features

The most influential features included:

1. Flow IAT Max
2. Subflow Fwd Bytes
3. Fwd Packet Length Mean
4. Bwd Packets/s
5. Average Packet Size
6. Total Length of Fwd Packets
7. Fwd Packet Length Max
8. PSH Flag Count
9. Packet Length Mean
10. Packet Length Std

## Project Structure

    network-intrusion-anomaly-detection/
    ├── data/
    ├── models/
    │   └── random_forest_portscan.joblib
    ├── notebooks/
    │   ├── 01_data_exploration.ipynb
    │   ├── 02_baseline_model.ipynb
    │   ├── 03_model_comparison.ipynb
    │   └── 04_final_model_analysis.ipynb
    ├── results/
    │   ├── figures/
    │   │   ├── confusion_matrix.png
    │   │   └── feature_importance.png
    │   ├── classification_report.txt
    │   ├── feature_importance.csv
    │   └── metrics.csv
    ├── .gitignore
    ├── requirements.txt
    └── README.md

## Technologies

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Jupyter Notebook
- Joblib

## Reproducibility

Install the required packages using:

    pip install -r requirements.txt

The raw CICIDS2017 dataset is not included in the repository because of its size.

## Notes

The reported results apply to the evaluated PortScan subset and the specified train-test split. Performance on unseen network environments or other attack categories may differ.