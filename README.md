# Adult Census Income — Binary Classification Project

Predicting whether an individual's annual income exceeds $50,000 using demographic, educational, and employment attributes from the Kaggle **Adult Census Income** dataset (32,561 records, 14 predictor variables, originally sourced from the 1994 U.S. Census).

## Problem Statement

Income is a central measure of economic well-being but is often unavailable or unreliably reported. This project builds and compares four classification models to estimate whether an individual earns more than $50,000/year from more observable demographic, educational, and employment attributes, and evaluates their practical business value, deployment strategy, and limitations.

## Repository Structure

```
adult-census-income-project/
├── README.md
├── .gitignore
├── notebooks/
│   └── Final_Project_Adult_Census_Income.ipynb   # full analysis: EDA, feature engineering, all 4 models
├── data/
│   └── raw/
│       └── train.csv                              # Kaggle Adult Census Income dataset
├── reports/
│   ├── Final_Report.docx
│   └── figures/                                    # exported confusion matrices, ROC curves, feature importance plots
└── slides/
    └── Final_Presentation.pptx
```

## Models & Work Split

| Model | Owner | Notebook Section |
|---|---|---|
| Logistic Regression | Elli Tai | Phase 2 |
| Decision Tree | Elli  | Phase 3 |
| Random Forest | Jessica | Phase 4 |
| Gradient Boosting | Ksatria | Phase 5 |

- **Elli** — built Logistic Regression and Decision Tree, established the shared cross-validation/evaluation framework (Phase 1) used by all four models, and identified/corrected data preparation issues from the midpoint analysis.
- **Jessica** — built Random Forest, set up and maintains this GitHub repository, and wrote the Business Impact, Practicality, and Extensions section.
- **Ksatria** — built Gradient Boosting, and wrote the Model Deployment/Automation Strategy and Lessons Learned & Recommendations sections.

All four models are trained and evaluated on the same 80/20 stratified train/test split (`random_state=42`), the same 5-fold `StratifiedKFold` cross-validation, and the same finalized 53-feature predictor set, ensuring results are directly comparable.

## Results Summary

| Model | CV F1 | CV ROC-AUC | Test F1 | Test ROC-AUC |
|---|---:|---:|---:|---:|
| Logistic Regression | 0.6563 | 0.9038 | 0.6637 | 0.8994 |
| Decision Tree | 0.6596 | 0.8804 | 0.6561 | 0.8672 |
| Random Forest | 0.6707 | 0.9126 | 0.6659 | 0.9082 |
| Gradient Boosting | 0.7061 | 0.9261 | 0.7008 | 0.9224 |

**Gradient Boosting performed best overall**, achieving the highest F1 score and ROC-AUC on both cross-validation and the holdout test set.

## How to Run

1. Clone the repo:
   ```bash
   git clone https://github.com/jmai3124/adult-census-income-project.git
   cd adult-census-income-project
   ```
2. Make sure `train.csv` is in `data/raw/` (or alongside the notebook — see the notebook's first cell for the exact path it expects).
3. Open `notebooks/Final_Project_Adult_Census_Income.ipynb` in Jupyter and run all cells top to bottom. The notebook is organized sequentially — later phases depend on variables created in earlier ones (e.g., `X_train`, `cv`, `evaluate_model_cv()`), so cells should not be run out of order.

**Requirements:** Python 3, `pandas`, `numpy`, `scikit-learn`, `matplotlib`, `seaborn`, `scipy`, `statsmodels`

## Dataset Source

[Kaggle — Adult Census Income](https://www.kaggle.com/datasets/uciml/adult-census-income) (originally from the UCI Machine Learning Repository, based on 1994 U.S. Census data).
