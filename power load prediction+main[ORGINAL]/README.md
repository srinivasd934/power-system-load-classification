# Electrical Grid Load Regime Classification

## Project Overview
Develop a multiclass machine learning pipeline to classify power consumption into distinct operational tiers: `Light_Load`, `Medium_Load`, and `Maximum_Load`, utilizing historical sensory and telemetry data from power distribution systems.

## Project Layout
```text
power_load_prediction/
├── README.md
├── requirements.txt
├── data/
│   ├── raw/
│   │   ├── load_data.csv
│   │   └── Problem statement.docx
│   └── processed/
│       └── load_data_timestamp_cleaned.csv
├── notebooks/
│   └── power_load_type_prediction.ipynb
├── reports/
    └── results_summary.md