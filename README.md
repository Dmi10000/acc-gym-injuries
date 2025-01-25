**ACC: Predicting Gym Injuries**

This repository contains a Python implementation for predicting the likelihood of future gym injuries among ACC clients. The primary goal is to identify individuals at higher risk of re-injury so that targeted interventions (e.g., free PT sessions) can be offered.

**Overview**
1. Data Ingestion and Cleaning

  Reads the CSV file (DataForExercise.csv) into a pandas DataFrame.
  Handles missing data by filling numeric NaN values with zero and categorical NaN values with "Unknown".
  Removes or flags duplicate records.
  
2. Exploratory Data Analysis (EDA)
  Visualizes the distribution of key variables (e.g., age, correlation among numeric columns).
  Helps understand data shape, outliers, and potential relationships.

3. Feature Engineering
  Filters out out-of-range ages (under 16), since gym usage in NZ typically starts at 16.
  Creates dummy variables for categorical fields (ethnicity, location, work type).
  Encodes claim year as a numerical proxy for “recency.”
  Summarizes total past injuries into one feature (total_past_injuries).
  Converts the response variable from “Y/N” to a binary indicator (1/0).

4. Model Building (Logistic Regression)
Splits the dataset into training and test sets (70% / 30%).
Trains a logistic regression model to predict whether an individual will have a future gym injury (response_binary).

5. Model Evaluation
Evaluates the model via classification report, AUC (Area Under the Curve), and confusion matrix.
Inspects precision, recall, F1-score to understand how effectively high-risk individuals are identified.

6. Ranking Individuals by Predicted Risk
  Computes predicted probabilities for each person.
  Sorts the DataFrame by risk (descending).
  Selects the top 500 individuals most likely to be re-injured (for targeted interventions).

7. Visualizing Insights
  Displays histograms/bar charts for demographics (age, ethnicity, location, work type) among the top 500.


**Prerequisites**

Python 3.7+

pandas, numpy, matplotlib, seaborn, scikit-learn




**Project Structure**

.
├── DataForExercise.csv           # Sample dataset

├── README.md                     # This file

└── acc_gym_injury_prediction.ipynb (or .py)  # Main Python script



**Key Points**

Age Filtering: We drop records where age_at_extraction_date < 16, aligning with NZ gym policy.

Missing Data: Handled by simple fill strategies (zeros for numeric, “Unknown” for categorical). Adjust as needed.

Feature Engineering:
  Recency: Encoded by year (higher = more recent claim).
	
  Past Injuries: Summed into total_past_injuries for a global injury score.
	
Model Selection: Logistic Regression provides interpretability; you can swap in other classifiers for experimentation.

Targeted Intervention: After scoring, the top 500 high-risk individuals are flagged for a possible PT session intervention.
