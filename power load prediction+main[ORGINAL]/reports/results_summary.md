# Results Summary

## Evaluation setup
- **Target:** `Load_Type`
- **Test strategy:** hold out the final calendar month
- **Held-out month:** December 2018
- **Test rows after removing duplicate timestamps:** 2,976
- **Models compared:** Logistic Regression and Random Forest
- **Selection criterion:** highest macro F1-score

## Best observed model: Random Forest

| Metric | Score |
|---|---:|
| Accuracy | 0.9519 |
| Macro precision | 0.9368 |
| Macro recall | 0.9578 |
| Macro F1-score | 0.9467 |
| Weighted F1-score | 0.9521 |

## Per-class test results

| Class | Precision | Recall | F1-score | Support |
|---|---:|---:|---:|---:|
| Light_Load | 0.98 | 0.94 | 0.96 | 1,744 |
| Medium_Load | 0.92 | 0.98 | 0.95 | 704 |
| Maximum_Load | 0.91 | 0.95 | 0.93 | 528 |

## Interpretation
The Random Forest model achieved approximately **95.2% test accuracy** on the held-out December observations. Macro F1 of approximately 0.947 indicates strong performance averaged equally across the three classes. The confusion matrix and exploratory plots are available in the executed notebook.

## Limitations
- This is a single-month chronological holdout; performance may vary in another month or year.
- The notebook does not perform hyperparameter tuning on the test set.
- Feature importance is not evidence of causation.
- The original dataset's label-generation logic is not documented in the provided problem statement. Validate how load categories were assigned before relying on the model in a live power system.
