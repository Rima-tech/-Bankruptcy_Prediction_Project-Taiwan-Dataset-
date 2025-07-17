# -Bankruptcy_Prediction_Project-Taiwan-Dataset-

## Project Objective
The primary goal of this project is to predict the likelihood of bankruptcy for companies using their financial ratios and performance metrics. By analyzing historical data and applying multiple machine learning algorithms, the project aims to assist investors, credit agencies, and financial institutions in early risk identification and informed decision-making.
## Executive Summary
This project analyzes a Taiwanese bankruptcy dataset to build a reliable binary classification model. After a detailed EDA, correlation analysis, and feature curation, 35 relevant financial features were selected. Four machine learning models—Decision Tree, Random Forest, KNN, and XGBoost—were trained and compared. XGBoost emerged as the top performer in accuracy and consistency. The model was further validated on individual samples, highlighting its potential to support financial risk assessment and bankruptcy prediction.

## Data Overview - 
•	Source: UCI Machine Learning Repository – Taiwanese Bankruptcy Prediction Dataset <br>
•	Total records: 6,819 companies <br>
•	Total features: 96 columns (including target variable) <br>
•	Target variable: Bankrupt? (Binary: 1 = Bankrupt, 0 = Not Bankrupt) <br>
•	Feature types: All numeric financial ratios <br>
•	Data quality: No missing values <br>

## Strategy Exploratory Data Analysis (EDA) & Feature Engineering

* The dataset was inspected using .head(), .info(), and .describe() to understand its structure and value distribution. <br>

* An initial irrelevant column was dropped.<br>

* The target variable ('Bankrupt?') was highly imbalanced, with very few bankrupt cases.<br>

<img src="https://github.com/Rima-tech/-Bankruptcy_Prediction_Project-Taiwan-Dataset-/blob/c716a78688132bd49b079e72d503c91bd16e1445/Images/bankrupt_cls_.png" alt=" bankruptcey_class_dist" width="400" height="400">

* Features were grouped into five logical categories: Profitability, Liquidity, Leverage, Efficiency, and Miscellaneous.

* Correlation heatmaps (Fig 1–4) were used within each group to detect highly correlated features.
![corr_heatmap_1

<img src="https://github.com/Rima-tech/-Bankruptcy_Prediction_Project-Taiwan-Dataset-/blob/c716a78688132bd49b079e72d503c91bd16e1445/Images/bankrupt_cls_.png" alt=" corr_heatmap_1" width="800" height="800">
![corr_heatmap_2]()
![corr_heatmap_3]()
![corr_heatmap_4]()

* Columns with extreme outliers were capped at the 99th percentile to reduce skewness.

* Histograms were plotted to assess the spread  in financial features.
*Random Forest model is trained to find out most important features and to help decide irrelivant features from final model . 
* Final Dataset is spliited into rain test split  and Standard Sclaer used to Scale the data begore training . 

## Models Trained and Performance Comparison
After finalizing the feature set, four machine learning models were trained using an 80/20 train-test split:
1.	Decision Tree (with class weight balancing)
2.	Random Forest (with class weight balancing)
3.	k-Nearest Neighbors (kNN) enhanced with SMOTE to address severe class imbalance
4.	XGBoost, enhanced with SMOTE to address severe class imbalance<br>
The target variable "Bankrupt" is highly skewed, with bankrupt cases forming a small minority. Therefore, models were evaluated not just on accuracy, but on Precision, Recall, and F1-Score, which better reflect performance on the minority class (i.e., bankrupt companies).
![comparison_table]()

## Interpretation for Business Stakeholders:
•	XGBoost (with SMOTE) delivered the best balance between detecting bankrupt companies (Recall) and avoiding false positives (Precision).
•	Random Forest had slightly higher accuracy, but struggled with recall—meaning it missed many bankrupt companies, which is risky in a business context.
•	KNN performed poorly across all metrics, indicating it’s unsuitable for this problem.
•	Decision Tree offers simplicity and decent recall, but XGBoost still outperforms it overall.
In risk management, missing a potential bankruptcy can be far costlier than flagging a false alarm. Thus, XGBoost is the most business-aligned choice.

## Important Features 
### Key Financial Drivers (appearing across all models):
1. Persistent EPS in the Last Four Seasons
2. Net Income to Total Assets
3. Borrowing Dependency
4. Total Debt to Net Worth
5. Operating Profit / Paid-in Capital
6. Quick Ratio
7. Cash Turnover Rate
![imp_tab1]()
![imp_tab1]()
![imp_tab1]()
![imp_tab1]()

## Business Implications
The model enables early detection of bankruptcy risk, supporting proactive measures like credit limit adjustments, investment re-evaluation, or risk mitigation.

XGBoost’s high recall ensures most risky firms are flagged, reducing potential financial loss.

Financial institutions and analysts can use this model to automate risk scoring using firm-level financial ratios.

The 35 selected features are interpretable and rooted in domain knowledge, making the insights actionable and explainable for decision-makers.

