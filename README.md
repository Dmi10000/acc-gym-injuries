ACC: Predicting Gym Injuries
This repository contains a Python implementation for predicting the likelihood of future gym injuries among ACC clients. The primary goal is to identify individuals at higher risk of re-injury so that targeted interventions (e.g., free PT sessions) can be offered.

Overview
Data Ingestion and Cleaning

Reads the CSV file (DataForExercise.csv) into a pandas DataFrame.
Handles missing data by filling numeric NaN values with zero and categorical NaN values with "Unknown".
Removes or flags duplicate records.
Exploratory Data Analysis (EDA)

Visualizes the distribution of key variables (e.g., age, correlation among numeric columns).
Helps understand data shape, outliers, and potential relationships.
Feature Engineering

Filters out out-of-range ages (under 16), since gym usage in NZ typically starts at 16.
Creates dummy variables for categorical fields (ethnicity, location, work type).
Encodes claim year as a numerical proxy for “recency.”
Summarizes total past injuries into one feature (total_past_injuries).
Converts the response variable from “Y/N” to a binary indicator (1/0).
Model Building (Logistic Regression)

Splits the dataset into training and test sets (70% / 30%).
Trains a logistic regression model to predict whether an individual will have a future gym injury (response_binary).
Model Evaluation

Evaluates the model via classification report, AUC (Area Under the Curve), and confusion matrix.
Inspects precision, recall, F1-score to understand how effectively high-risk individuals are identified.
Ranking Individuals by Predicted Risk

Computes predicted probabilities for each person.
Sorts the DataFrame by risk (descending).
Selects the top 500 individuals most likely to be re-injured (for targeted interventions).
Visualizing Insights

Displays histograms/bar charts for demographics (age, ethnicity, location, work type) among the top 500.