# Module 12 Report

## Overview of the Analysis

In this section, describe the analysis you completed for the machine learning models used in this Challenge. This might include:

* Explain the purpose of the analysis.
* Explain what financial information the data was on, and what you needed to predict.
* Provide basic information about the variables you were trying to predict (e.g., `value_counts`).
* Describe the stages of the machine learning process you went through as part of this analysis.
* Briefly touch on any methods you used (e.g., `LogisticRegression`, or any resampling method).

The code analyzes the risk of default for loan data. The characteristics/features included loan size, interest rate, borrower income, debt-to-income ratio, number of accounts, negative marks, and total debt. These were split into a training and testing data set and then the training split was used to fit an sklearn LogisticRegression model. Then, when testing this model with the test split data, this model returned a balanced accuracy score of 0.952, and the weighted averages for precision, recall, and f1-score were all 0.99, indicating that our model was significantly accurate on this original training split.
We then oversampled the training split (due to a imbalance in categories - an approximately 30:1 split) using imblearn's RandomOverSampler, which evened the samples per category. Then we trained the sklearn LogisticRegression model on this new oversampled training data, and predicted the loan status once again. With this new resampled data, the model was even more accurate (0.994 balanced accuracy, >0.99 weighted avg precision/recall/f1-score).

## Results

Using bulleted lists, describe the balanced accuracy scores and the precision and recall scores of all machine learning models.

* Base sklearn LogisticRegression:
  * Balanced Accuracy: 0.952
  * Precision: 0.99
  * Recall: 0.99


* RandomOverSampler plus LogisticRegression:
  * Balanced Accuracy: 0.994
  * Precision: 0.99
  * Recall: 0.99

## Summary

Both models performed exceedingly well (>0.95 on all scores). The second model performed better in most respects (all except high-risk precision); however, in a case where we want to minimize risk (defaulting a loan), higher precision would be preferable, which the first model showed for positives (1's). This would lead a highly risk-averse bank to use the first model, while a more stable bank may opt for the balanced accuracy provided by the second model.
