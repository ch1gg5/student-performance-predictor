# Student Performance Predictor

This project aims to predict student exam scores based on various academic, social, and demographic factors. Through extensive data exploration and model evaluation, a Linear Regression model was identified as the most effective approach for this dataset.

## Dataset Overview

The dataset (`data/student_data.csv`) includes information on students' study habits, attendance, parental involvement, and more. Key features include:

- **Academic Factors:** Hours Studied, Attendance, Previous Scores, Tutoring Sessions.
- **Social/Demographic Factors:** Parental Involvement, Access to Resources, Motivation Level, Teacher Quality, Peer Influence, etc.
- **Target Variable:** `Exam_Score` (Range: 55-100).

## Key Findings from Exploratory Data Analysis (EDA)

- **Correlations:** `Attendance` and `Previous_Scores` showed a visible relationship with the final `Exam_Score`.
- **Data Quality:** The dataset is generally clean, though some potential outliers (e.g., scores > 100) were identified and handled during exploration.
- **Group Means:** Factors like `Parental Involvement`, `Motivation Level`, and `Access to Resources` show variations in average exam scores, indicating their relevance.

## Model Evaluation and Metrics

Several models were tested and compared using Mean Absolute Error (MAE), Root Mean Squared Error (RMSE), and R-squared ($R^2$).

### 1. Linear Regression (Selected Model)
- **Performance:**
    - **MAE:** ~0.415
    - **RMSE:** ~1.521
    - **$R^2$:** ~0.825
- **Observations:** The baseline Linear Regression model performed exceptionally well. It maintained strong correlation ($r \approx 0.909$) between actual and predicted scores. 
- **Limitations:** The model slightly compresses predictions towards the mean (predicted range ~55.5-78.2 vs. actual ~55-98) and struggles with unusually high-scoring students.

### 2. Decision Tree Regressor
- **Performance (Optimal Depth 5):**
    - **MAE:** ~1.576
    - **RMSE:** ~2.391
    - **$R^2$:** ~0.568
- **Observations:** Unrestricted trees severely overfitted. Even with depth tuning, the performance remained significantly lower than Linear Regression.

### 3. Ensemble Methods (Random Forest & Gradient Boosting)
- **Random Forest:** Performance varied with depth but did not surpass Linear Regression.
- **Gradient Boosting:** Even after tuning learning rates and number of estimators, it failed to improve upon the generalization achieved by the simple Linear Regression model.

## Conclusion

**Linear Regression is the preferred model for this dataset.** It consistently achieved the strongest predictive performance and maintained its advantage through cross-validation. The analysis suggest that the remaining errors are likely due to inherent variance in the data not captured by the available features, rather than a lack of model complexity.

---
*Note: Findings based on analysis in `notebooks/exploration.ipynb`.*
