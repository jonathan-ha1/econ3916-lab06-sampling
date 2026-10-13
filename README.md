# Sampling for Machine Learning — Train-Test Splits

## Objective
This lab tests how the way data is split affects whether a model's evaluation can be trusted.

## Methodology
- Explored the Titanic dataset of 891 passengers, using survival as the target variable.
- Compared a naive train-test split with a stratified split and checked that stratifying kept the survival rate the same in both the training and test sets.
- Found data leakage in a StandardScaler step and a SimpleImputer step, where both were fit on all the data before splitting. Fixed them by splitting first, fitting on the training rows only, and then only transforming the test rows.
- Wrote a function, `split_by_share()`, that splits a table using a test share and a seed, and checked that it matched the lab's own split.

## Key Findings
- Stratifying the split kept the survival rate the same in both halves, which a naive split does not guarantee.
- Fitting a scaler or imputer before splitting lets information from the test set leak into training, which makes the model's test results look better than they really are.
- A split is only a fair test of a model if the test rows are kept completely separate from everything the model learns during training.
