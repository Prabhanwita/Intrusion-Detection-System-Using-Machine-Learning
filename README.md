# Intrusion Detection System Using Machine Learning

## Project overview
This project evaluates machine-learning models for detecting malicious network traffic using the **UNSW-NB15** dataset. The report describes data preprocessing, feature selection, encoding, scaling, handling class imbalance with SMOTE, and comparison of multiple classifiers and ensemble methods.

This README also explains how an **Agile development approach** can be applied to develop the IDS project incrementally. The Agile plan below is a proposed workflow based on the project report, not a claim that formal Agile ceremonies were already performed.

## Objectives
- Prepare the UNSW-NB15 dataset for modelling.
- Evaluate binary classification of network traffic as attack or normal.
- Compare models including Logistic Regression, Random Forest, Naive Bayes variants, Decision Tree, Bagging, XGBoost, Stacking, and Voting.
- Evaluate accuracy, precision, recall, and F1-score.
- Improve minority attack detection while managing false alarms.

## Dataset and preprocessing
The report describes UNSW-NB15 as containing 2,540,044 records and 49 features, with training and testing files. Preprocessing steps include duplicate/redundant record checks, handling missing values, one-hot encoding of categorical fields, numeric conversion, feature selection, scaling, and SMOTE for class imbalance.

## Agile approach
Agile breaks work into short iterations (sprints), delivers usable increments, and uses feedback and test results to reprioritize work.

### Suggested sprint plan
1. **Sprint 1 — Requirements and data audit:** define attack/normal labels, target users, acceptance metrics, data access rules, and inspect the train/test files.
2. **Sprint 2 — Data preparation:** implement repeatable cleaning, categorical encoding, feature selection, scaling, and validation checks.
3. **Sprint 3 — Baseline models:** train Decision Tree and Logistic Regression baselines; establish accuracy, precision, recall, F1, and confusion matrices.
4. **Sprint 4 — Ensemble models:** evaluate Random Forest, Bagging, XGBoost, Stacking, and Voting with consistent splits and metrics.
5. **Sprint 5 — Imbalance handling:** test SMOTE within the training pipeline only, then compare minority-class recall, precision, and F1.
6. **Sprint 6 — Evaluation and handover:** validate on held-out data, summarize model trade-offs, document limitations, and prepare a reproducible notebook and report.

## Definition of done
- Data preprocessing can be rerun consistently.
- Train/test separation is preserved; resampling is applied only to training data.
- Results include precision, recall, F1-score, and confusion matrix, not accuracy alone.
- Model comparisons use consistent evaluation data and settings.
- Notebook, dataset requirements, and instructions are documented.
- Limitations and next steps are clearly stated.

## Testing and quality checks
- Verify input columns, data types, missing values, and labels.
- Check that encoders and scalers are fitted only on training data.
- Avoid leakage by applying SMOTE only after splitting and only to training data.
- Evaluate per-class performance, especially rare attacks such as Worms and Shellcode.
- Repeat experiments with recorded random seeds and parameter settings.
- Check model performance on the untouched test set before final reporting.

## Results described in the project report
The report states that tree-based and ensemble methods generally performed strongly. It reports Random Forest accuracy of 0.9168 and F1-score of 0.9273 in its performance comparison, and describes Decision Tree, XGBoost, Stacking, Voting, and Bagging as strong approaches. These values are reproduced from the report and have not been independently rerun here.

## Suggested team roles
- **Data analyst:** audit and document the dataset.
- **Machine-learning developer:** build preprocessing and model pipelines.
- **Evaluation lead:** define metrics, validate comparisons, and check leakage.
- **Security/domain reviewer:** assess operational usefulness and false-alert consequences.
- **Project coordinator/product owner:** prioritize sprint goals and accept increments.

## Limitations and future work
Performance on a benchmark dataset does not guarantee performance on live network traffic. Before operational use, test on representative current traffic, evaluate rare attack classes, monitor drift, review privacy/security constraints, and plan ongoing model updates. Confirm that the final reported scores can be reproduced from the code and data.

## How to use the project
1. Open the project's Jupyter Notebook or source code.
2. Obtain the UNSW-NB15 training and testing files referenced by the implementation.
3. Install the Python libraries used by the notebook, including pandas, NumPy, scikit-learn, and any model-specific libraries such as XGBoost or imbalanced-learn if used.
4. Run preprocessing and model-training cells in order.
5. Review the model comparison and class-level metrics.
6. Record any changes and results for each Agile sprint.
