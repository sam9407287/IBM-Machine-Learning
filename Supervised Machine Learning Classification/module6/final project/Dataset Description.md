# Dataset Description

## Overview
The data has been split into two groups:

- **Training set (`train.csv`)**: Used to build your machine learning models. For the training set, we provide the outcome (also known as the "ground truth") for each passenger. Your model will be based on "features" like passengers' gender and class. You can also use feature engineering to create new features.

- **Test set (`test.csv`)**: Used to see how well your model performs on unseen data. For the test set, we do not provide the ground truth for each passenger. It is your job to predict these outcomes. For each passenger in the test set, use the model you trained to predict whether or not they survived the sinking of the Titanic.

We also include `gender_submission.csv`, a set of predictions that assume all and only female passengers survive, as an example of what a submission file should look like.

---

## Data Dictionary

| Variable   | Definition                          | Key/Notes                                                                 |
|------------|-------------------------------------|---------------------------------------------------------------------------|
| survival   | Survival                            | 0 = No, 1 = Yes                                                          |
| pclass     | Ticket class                        | 1 = 1st, 2 = 2nd, 3 = 3rd                                                |
| sex        | Sex                                 |                                                                           |
| age        | Age in years                        | Fractional if less than 1. If estimated, in the form of xx.5             |
| sibsp      | # of siblings / spouses aboard      |                                                                           |
| parch      | # of parents / children aboard      |                                                                           |
| ticket     | Ticket number                       |                                                                           |
| fare       | Passenger fare                      |                                                                           |
| cabin      | Cabin number                        |                                                                           |
| embarked   | Port of Embarkation                 | C = Cherbourg, Q = Queenstown, S = Southampton                            |

---

## Variable Notes

- **pclass**: A proxy for socio-economic status (SES)
  - 1st = Upper
  - 2nd = Middle
  - 3rd = Lower

- **age**: Age is fractional if less than 1. If the age is estimated, it is in the form of xx.5.

- **sibsp**: The dataset defines family relations in this way:
  - Sibling = brother, sister, stepbrother, stepsister
  - Spouse = husband, wife (mistresses and fiancés were ignored)

- **parch**: The dataset defines family relations in this way:
  - Parent = mother, father
  - Child = daughter, son, stepdaughter, stepson
  - Some children traveled only with a nanny, therefore `parch=0` for them.

---

## Files
- **Training set**: `train.csv`
- **Test set**: `test.csv`
- **Example submission**: `gender_submission.csv`

---

## Example Submission (`gender_submission.csv`)
This file contains an example of what a submission file should look like. The predictions assume that all and only female passengers survive.

