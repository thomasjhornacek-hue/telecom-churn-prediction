# Telecom Customer Churn Prediction

A PySpark machine learning pipeline that predicts telecom customer churn and compares three classifiers, then translates the strongest model into a retention strategy. Built as the applied project for the Johns Hopkins Big Data Analytics certificate.

## Overview

Customer churn is expensive in telecom, where retaining an existing subscriber costs far less than acquiring a new one. This project builds an end-to-end churn classification pipeline in PySpark, evaluates three models, and surfaces the behavioral signals that most predict churn so they can inform retention outreach.

## Data

The dataset is a standard telecom churn file (provided with the course) covering account length, usage minutes and charges across day, evening, night, and international windows, customer service call counts, plan flags, and a churn label. The target variable is `Churn`.

## Approach

1. Spark session setup and data loading
2. Exploratory analysis: distributions, count plots, and a correlation matrix
3. Feature assembly and stratified train/test split
4. Model training and evaluation across three classifiers
5. Model comparison and feature-importance analysis

## Models and Results

Three classifiers were trained and evaluated on a held-out test set:

| Model | Test Accuracy | Test Precision | Test Recall |
|---|---|---|---|
| Decision Tree | 0.9407 | 0.9388 | 0.9407 |
| Random Forest | 0.9376 | 0.9374 | 0.9376 |
| Gradient Boosted Trees | 0.9587 | 0.9577 | 0.9587 |

Gradient Boosted Trees performed best, reaching 95.87 percent test accuracy. The Decision Tree provided an interpretable baseline, Random Forest reduced overfitting through ensemble averaging, and GBT achieved the highest accuracy by iteratively correcting errors across boosting rounds.

## Key Churn Drivers

Feature importances identified the strongest predictors of churn:

1. Customer service calls (0.209)
2. Day minutes and day charge (0.205)
3. Evening minutes and evening charge (0.093)

The customer-service-call signal is the most actionable: a rising count of service calls is an early warning that a subscriber is at risk, which points to proactive retention outreach before churn occurs.

## Tools

PySpark, Spark MLlib (DecisionTreeClassifier, RandomForestClassifier, GBTClassifier), Spark DataFrames, Python, matplotlib, seaborn.

## Notes

Completed as part of the Johns Hopkins Big Data Analytics certificate. The dataset was provided with the course. The pipeline, model comparison, and retention framing are my own work.
