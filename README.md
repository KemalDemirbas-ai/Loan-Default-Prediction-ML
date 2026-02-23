🚀 Loan Default Prediction and Risk Analysis
📌 Project Overview
The main objective of this project is to develop a robust machine learning model for a financial institution to predict in advance whether loan applicants will be able to repay their loans (the risk of defaulting).

We didn't just build a predictive model; we conducted comprehensive Exploratory Data Analysis (EDA), meticulous data cleaning, and custom Feature Engineering. By strictly adhering to Data Leakage prevention rules, we generated actionable Business Insights to minimize financial risks.

🎯 The Business Problem
For banks, a customer defaulting on a loan is far more costly than rejecting a good customer. In this dataset, which suffers from Class Imbalance, the model's goal is not to artificially inflate overall Accuracy. Instead, the objective is to maximize the Recall for the "Charged Off" (Defaulters) class, which is what actually causes massive financial harm to the bank.

🛠️ Methodology and Pipeline
1. Data Cleaning and Preprocessing
Messiness in real-world data was handled:

Columns with no predictive power, such as Customer IDs, were dropped from the model.

Financial values entered in string format (e.g., $584.03, 10+ years) were cleaned using RegEx and converted to numerical (float) formats.

Missing Values were imputed using Median values to prevent statistical bias.

2. Feature Engineering
Going beyond standard columns in credit risk analysis, one of the banking sector's most crucial metrics, the Credit Utilization ratio, was engineered from scratch:

Credit Utilization = Current Credit Balance / Maximum Open Credit
(Note: This new feature emerged as the 3rd most influential factor in the model's decision-making process.)

3. Preventing Data Leakage and Scaling
The common industry mistake of "applying scaling and data oversampling to the entire dataset" was avoided. To prevent the model from "cheating" (Data Leakage), the data was first split into Train and Test sets. StandardScaler and SMOTE (Synthetic Minority Over-sampling Technique) were applied only to the training data.

📊 Model Evaluation: The "Accuracy Paradox"
Two different Random Forest models were trained in the project, and the "Accuracy vs. Recall" trade-off was analyzed:

Model 1 (Baseline - Imbalanced Data): Although it yielded a high overall Accuracy of 84%, the Recall rate for catching actual "Defaulters" remained at only 60%. The model showed a bias toward "trusting everyone."

Model 2 (Advanced - SMOTE & Leakage-Proof): Trained with synthetic data, this model saw a drop in overall Accuracy to 75.38%, but its Recall rate for catching Defaulters jumped to 70%.

Business Decision: In financial risk management, catching a bad customer is far more valuable than overall accuracy. Therefore, Model 2 was selected for integration into the bank's live system (Production).

💡 Business Insights for Management
According to the "Feature Importance" analysis of our best model, the top 5 critical questions that bank management must ask customers on loan application forms (accounting for ~80% of the decision weight) are:

Credit Score: "What is your current credit score?" (The model's most important factor with a 20% weight)

Current Loan Amount: "Exactly how much money are you requesting for this loan?"

Credit Utilization: "What is the ratio of your current debts to your total available credit limit?" (Our custom-engineered feature with an 8.9% impact)

Monthly Debt: "How much do you pay regularly each month for other debts?"

Maximum Open Credit: "What is your total available credit limit across other banks?"

💻 Technologies Used
Python (Pandas, NumPy)

Machine Learning: Scikit-Learn (Random Forest, Logistic Regression, XGBoost, etc.)

Imbalanced Data Handling: Imbalanced-learn (SMOTE)

Data Visualization: Matplotlib, Seaborn
