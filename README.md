# Power System Load Category Prediction

## Goal

Build a multiclass model that predicts the `Load_Type` label (`Light_Load`, `Medium_Load`, `Maximum_Load`) using past power-system readings.

## Repository Layout

```
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
└── reports/
    └── results_summary.md
```

## How to Run

A virtual environment with Python 3.10 to 3.13 is suggested.

```powershell
python -m venv .venv
.venv\Scripts\activate            # Windows
# source .venv/bin/activate       # macOS / Linux
python -m pip install --upgrade pip
pip install -r requirements.txt
jupyter notebook notebooks/power_load_type_prediction.ipynb
```

Execute every cell in order from the first to the last. The notebook looks for the CSV file starting from the project root or from the notebook's own folder.

## Approach

1. Convert the original timestamp column to a datetime type and order the records by time.
2. Drop records whose timestamp cannot be parsed, and for repeated timestamps keep only the earliest row.
3. Leave missing feature values untouched until the modelling stage, where median imputation is learned from the training portion alone.
4. Create calendar features, with hour and month encoded as sine/cosine pairs to capture their cyclic nature.
5. Split by time: the last calendar month in the dataset is held out for testing, and every earlier month is used for training.
6. Train and compare two models: Logistic Regression and Random Forest.
7. Score the models using accuracy, macro-averaged precision, recall and F1, weighted F1, a per-class classification report and a confusion matrix.

## Notes

- The supplied CSV is treated as the ground truth, and the original file is stored without modification.
- The processed CSV differs from the raw one only in that timestamps are parsed and duplicate timestamps are removed. No values are imputed and no outliers are dropped.
- The held-out month is detected from the data itself instead of being fixed in the code.
- The figures in `reports/results_summary.md` describe what was observed on this dataset with this particular time-based split. They do not promise how the model will perform on new data in the future.