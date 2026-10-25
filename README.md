# Ad Click Prediction

A logistic regression model that predicts whether a user will click an online ad, built to help a digital advertising company (ConnectSphere Digital, a case study) stop showing ads to people unlikely to click.

**Result: 96.7% accuracy on a held-out test set (300 users).**

## Problem

Many ads are shown to users who never click them, which wastes marketing budget. This project builds a model that predicts click or no click from basic user information, so ads can be shown to the right audience.

## Dataset

About 1,000 users, one row per user.

| Feature | Description |
|---|---|
| Daily Time Spent on Site | Average minutes spent on the website |
| Age | Age of the user |
| Area Income | Average income of the user's area |
| Daily Internet Usage | Average time spent online per day |
| Gender | Gender of the user |
| Timestamp | Date and time the ad was shown |
| Clicked on Ad | Target: 1 = clicked, 0 = did not click |

Data file: `advertising.csv` in this repo.

## Approach

1. **Cleaning:** removed duplicate records and converted Timestamp to date-time format.
2. **Feature work:** extracted Hour and Day of Week from Timestamp, and encoded Gender as a numeric column.
3. **Exploration:** box plots, age distribution and a correlation heatmap.
4. **Model:** logistic regression (scikit-learn), trained on 70% of the data and tested on the remaining 30%.
5. **Evaluation:** accuracy, confusion matrix and classification report.

## Results

| Metric | Value |
|---|---|
| Accuracy | 96.7% |
| Precision (clicked) | 0.97 |
| Recall (clicked) | 0.96 |
| F1-score | 0.97 |

Confusion matrix on the 300 test users: 142 true negatives, 148 true positives, 4 false positives, 6 false negatives.

**What stood out in the data:** Daily Internet Usage and Daily Time Spent on Site had the strongest relationship with clicking (both negative), followed by Age (positive) and Area Income (negative). In this dataset, heavier site and internet users were less likely to click.

## Tech stack

Python, pandas, NumPy, scikit-learn, Matplotlib, Seaborn, Google Colab

## How to run

1. Open the notebook in Google Colab, or download it and open it in Jupyter.
2. Make sure the data file is in the same folder, or let the notebook read it from this repo.
3. Run all cells.

## Limitations and next steps

- Small dataset (about 1,000 rows) and a single train/test split, so the score may change on new data.
- Next steps: cross-validation, comparing with other models (decision tree, random forest), and testing on larger, real campaign data.
