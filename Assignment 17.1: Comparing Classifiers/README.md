# Assignment 17.1: Comparing Classifiers

## Project Files

- [Jupyter Notebook](prompt_III.ipynb)
- [Dataset](data/bank-additional-full.csv)
- [Source Paper](CRISP-DM-BANK.pdf)

## Overview

The goal of this project is to predict whether a customer will subscribe to a term deposit and compare Logistic Regression, KNN, Decision Tree, and SVM classifiers.

## Procedure

1. Clean and explore the data
2. Prepare the bank-client features
3. Compare the four classifiers
4. Tune and evaluate a decision tree

## Results

Accuracy was misleading because only 11.27% of customers subscribed. The tuned decision tree improved balanced accuracy from 52.52% to 59.92% and recall from 8.84% to 48.92%, but it also produced more false positives.

The tuned model is useful when finding more potential subscribers is the priority. A stricter decision threshold should be considered when reducing unnecessary calls is more important.
