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

<img src="https://github.com/Rima-tech/-Bankruptcy_Prediction_Project-Taiwan-Dataset-/blob/089050848642212fdfcca1249bf854a141b6f5de/Images/prof_corr.png" alt=" corr_heatmap_1" width="900" height="900">

<img src="https://github.com/Rima-tech/-Bankruptcy_Prediction_Project-Taiwan-Dataset-/blob/089050848642212fdfcca1249bf854a141b6f5de/Images/corr_2.png" alt="corr_2" width="900" height="900">

<img src="https://github.com/Rima-tech/-Bankruptcy_Prediction_Project-Taiwan-Dataset-/blob/089050848642212fdfcca1249bf854a141b6f5de/Images/corr_3.png" alt="corr_3" width="900" height="900">

<img src="https://github.com/Rima-tech/-Bankruptcy_Prediction_Project-Taiwan-Dataset-/blob/089050848642212fdfcca1249bf854a141b6f5de/Images/corr_4.png" alt="corr_4" width="900" height="900">


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

<img src="https://github.com/Rima-tech/-Bankruptcy_Prediction_Project-Taiwan-Dataset-/blob/a3b03dfa68b11032ab8f1a1325ddc3a64c983440/Images/comparison_tab.png" alt="comparision_table " width="400" height="400">

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
<img src="https://github.com/Rima-tech/-Bankruptcy_Prediction_Project-Taiwan-Dataset-/blob/a3b03dfa68b11032ab8f1a1325ddc3a64c983440/Images/DT_imp_f.png" alt="DT_imp" width="800" height="800">
<img src="https://github.com/Rima-tech/-Bankruptcy_Prediction_Project-Taiwan-Dataset-/blob/a3b03dfa68b11032ab8f1a1325ddc3a64c983440/Images/RF_imp_f.png" alt="RF_imp" width="800" height="800">
<img src="https://github.com/Rima-tech/-Bankruptcy_Prediction_Project-Taiwan-Dataset-/blob/a3b03dfa68b11032ab8f1a1325ddc3a64c983440/Images/XGB_imp_f.png" alt="XGB_imp" width="800" height="800">

## Business Implications
1. Banks & Financial Institutions<br>
Use: Loan risk assessment<br>
* How it helps: Traditional credit checks may miss deeper financial issues. This model can spot hidden risks like poor profitability or high debt—even if surface numbers look good.
Benefit: Fewer bad loans (NPAs), better loan quality, and easier compliance.

2. Investors & Private Equity<br>
Use: Monitoring portfolio companies<br>
* How it helps: Manually checking financial health for hundreds of firms is tough. This model highlights early warning signs like unstable earnings or weak liquidity.
Benefit: Smarter investment calls, timely exits, and higher confidence.

3. B2B Vendors & Suppliers<br>
Use: Setting credit terms for customers<br>
* How it helps: Avoid giving credit to firms likely to default. The model flags risky buyers so vendors can shorten credit periods or demand upfront payment.
Benefit: Protects cash flow and keeps supply chains healthy.

4. Finance Teams (Large Companies)<br>
Use: Tracking partners or internal units<br>
* How it helps: Finance teams can use this model to watch subsidiaries or partners showing financial stress—like low cash flow or rising debt.
Benefit: Acts early to avoid losses or brand damage.

## Conclusion
This project demonstrates how financial ratio analysis combined with machine learning can effectively predict bankruptcy risk. By narrowing down to 35 key features and testing multiple models, XGBoost emerged as the most reliable predictor. The model's interpretability and accuracy make it a valuable decision-support tool for various stakeholders in finance, investment, and operations.

