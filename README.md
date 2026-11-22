 **Student Registration Number:** 2021/ICT/87

 Project 43 – AI Risk Review

1. Case Study

A hypothetical organization uses an AI-based income-prediction system to support financial decisions. The system predicts an individual's income category using the UCI Adult Census Income dataset.

The financial-decision scenario is hypothetical. The original dataset is not a loan, credit-risk, or hiring dataset. This project examines the potential risks of using AI predictions in sensitive decision-making environments.

2. Research Question

How can an AI-based income prediction system create privacy, bias and misuse risks, and how can these risks be identified, evaluated and mitigated?

3. Project Objectives

Develop a machine learning model to predict income categories.

Establish a baseline model and compare it with an improved model.

Evaluate model performance using appropriate classification metrics.

Identify incorrect predictions through error analysis.

Examine potential fairness issues across sex and race groups.

Assess privacy, bias and misuse risks.

Recommend appropriate risk mitigation measures.

4. Dataset

Dataset: UCI Adult Census Income Dataset

Source: https://archive.ics.uci.edu/dataset/2/adult

The dataset is based on an extraction from the 1994 US Census database.

The original archive includes:

adult.data – Training records.

adult.test – Held-out test records.

adult.names – Dataset documentation.

Download the dataset from the UCI repository and place adult.data and adult.test inside the data/raw/ directory. Do not rename these files.

The target variable is income, classified into two categories:

<=50K

>50K

Dataset size

Dataset

Records

Training data

32,561

Test data

16,281

The dataset contains demographic, educational and employment-related attributes.

5. Technologies Used

Python

Jupyter Notebook

Pandas

NumPy

Scikit-learn

Matplotlib

Seaborn

Joblib

6. Machine Learning Methodology

Data Preprocessing

Loaded the training and test datasets.

Handled missing values using imputation.

Applied numerical scaling.

Applied one-hot encoding to categorical features.

Removed the fnlwgt feature from the model inputs.

Used Scikit-learn pipelines to combine preprocessing and model training.

Baseline Model

A DummyClassifier using the most frequent strategy was implemented as the baseline model.

Main Model

Logistic Regression was selected as the main classification algorithm.

The model predicts whether an individual's income category is >50K or <=50K.

Model Evaluation

The following evaluation methods were used:

Accuracy

Precision

Recall

F1-score

Classification report

Five-fold stratified cross-validation

Held-out test evaluation using adult.test

The test dataset was reserved for final evaluation.

7. Model Results

The following results were obtained from the project notebook.

Model Performance Comparison

Metric

Dummy Baseline

Logistic Regression

Accuracy

0.764

0.851

Precision

0.000

0.730

Recall

0.000

0.587

F1-score

0.000

0.651

The Logistic Regression model performed better than the DummyClassifier baseline across the reported evaluation metrics.

Five-Fold Cross-Validation

The Logistic Regression model was evaluated using five-fold stratified cross-validation on the training dataset.

Metric

Mean CV Score

Accuracy

0.851

Precision

0.734

Recall

0.598

F1-score

0.659

The results indicate reasonably consistent performance across the five validation folds.

8. Error Analysis

Error analysis was conducted to understand incorrect model predictions.

At least 10 incorrect predictions were examined.

Two types of classification errors were identified:

False Negative: An individual whose actual income category is >50K is predicted as <=50K.

False Positive: An individual whose actual income category is <=50K is predicted as >50K.

The selected examples included both false negatives and false positives.

The analysis demonstrates that the model can make incorrect predictions even when its overall accuracy is relatively high.

9. Fairness Analysis

A group fairness audit was conducted using sex and race attributes.

The following measures were examined:

Number of individuals in each group.

Predicted positive rate.

True positive rate.

Differences in prediction rates and true positive rates were observed across demographic groups.

These differences indicate potential fairness concerns that require further investigation. However, group disparities alone do not prove discrimination.

Smaller demographic groups may also have less reliable estimates due to limited sample sizes.

Reduced Model Comparison

A second Logistic Regression model was evaluated after excluding sex and race from the model features.

Model

Accuracy

Precision

Recall

F1-score

Full model

0.851

0.730

0.587

0.651

Reduced model

0.851

0.732

0.585

0.650

Removing sex and race did not materially change the model's performance.

However, removing protected attributes does not guarantee fairness because other variables may act as proxies for protected characteristics.

10. AI Risk Assessment

The project examines three main categories of AI risk.

Privacy Risks

Personal and demographic information may be exposed, collected or used beyond its original purpose.

Mitigation:

Apply data minimization.

Restrict access to sensitive information.

Use secure data storage.

Avoid unnecessary collection of personal data.

Bias and Fairness Risks

The model may produce different outcomes across demographic groups due to patterns in historical data.

Mitigation:

Conduct regular fairness audits.

Monitor group-level performance.

Investigate differences in prediction outcomes.

Avoid relying only on overall accuracy.

Misuse Risks

Predictions may be incorrectly treated as facts and used to make important decisions about individuals.

Mitigation:

Clearly communicate model limitations.

Require human review for important decisions.

Avoid fully automated high-impact decisions.

Restrict the model to its intended educational purpose.

Risk levels were assessed using qualitative likelihood and impact scores.

11. Model Saving and Prediction

The trained Logistic Regression model was saved using Joblib.

The saved model was loaded successfully and tested with new sample input data.

A prediction function was also implemented to accept individual feature values and return an income-category prediction.

Example output:

Prediction from saved model: >50K

This confirms that the saved model can be loaded and used to generate predictions.

The prediction is an estimate and should not be treated as a guaranteed fact.

12. Reproducibility

A fixed random seed of 42 was used to support reproducibility.

Preprocessing operations were included inside Scikit-learn pipelines to reduce the risk of data leakage.

Cross-validation was performed using only the training dataset. The official test dataset was reserved for final evaluation.

The notebook was tested after restarting the Jupyter kernel and running all cells from top to bottom.

13. Project Structure

Project43_UCI_Adult_Starter/
│
├── data/
│   └── raw/
│       ├── adult.data
│       └── adult.test
│
├── notebooks/
│   └── AI_Risk_Review_Project43.ipynb
│
├── results/
│   └── income_prediction_model.pkl
│
├── requirements.txt
│
└── README.md

14. How to Run the Project

Step 1: Install Python

Install Python and ensure it is available from your terminal.

Step 2: Open the Project Folder

Open a terminal in the project directory.

Step 3: Create a Virtual Environment (Optional)

python -m venv venv

Activate it on Windows:

venv\Scripts\activate

Step 4: Install Dependencies

python -m pip install -r requirements.txt

Step 5: Start Jupyter Notebook

jupyter notebook

Step 6: Open the Notebook

Open:

notebooks/AI_Risk_Review_Project43.ipynb

Step 7: Run the Notebook

Run all notebook cells from top to bottom.

Ensure that the two dataset files are available inside data/raw/ before running the notebook.

15. Limitations

The dataset is based on the 1994 US Census and does not represent current Sri Lankan population or income patterns.

The dataset is not specifically designed for loan approval, credit scoring or hiring decisions.

The model predicts income categories only.

Predictions may be incorrect and should not be treated as guaranteed facts.

Group disparities do not independently establish discrimination.

Removing protected attributes does not eliminate all potential sources of bias.

Risk ratings are qualitative assessments.

The model requires further evaluation before any real-world application.

16. Data Handling and Ethical Considerations

The dataset is publicly available, but responsible data handling is still important.

Do not attempt to identify or re-identify individuals.

Do not upload private personal records to external AI services.

Use data only for the intended educational and research purposes.

Check the dataset citation and terms before redistributing the original data.

Do not use this model to make real financial, employment or other high-impact decisions about individuals.

## Dataset Attribution

Becker, B. & Kohavi, R. (1996).
Adult [Dataset]. UCI Machine Learning Repository.
https://doi.org/10.24432/C5XW20

License: Creative Commons Attribution 4.0 International (CC BY 4.0).

17. Conclusion

This project demonstrates how a machine learning model can be developed and evaluated while also examining the risks associated with AI-based prediction systems.

Although Logistic Regression achieved better performance than the baseline model, the evaluation identified incorrect predictions and potential differences across demographic groups.

The project highlights the importance of privacy protection, fairness evaluation, transparency, responsible use and human oversight when developing AI systems.

Project 43 – AI Risk Review
Educational case study using the UCI Adult Census Income Dataset.