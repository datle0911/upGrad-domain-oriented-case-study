# Customer Churn Prediction Case Study
This project aims to predict customer churn among high-value customers for a telecom company. 
Main objectives:

1. Predict whether a customer will churn in the near future, allowing the company to take proactive action.
2. Identify the factors that are most indicative of churn, providing insights that could inform strategies to reduce churn.

## Main Contents
- Exploratory Data Analysis (EDA)
- Handling Multicollinearity (VIF)
- Model Building
- Feature Importance Visualization

## Exploratory Data Analysis (EDA)
The EDA phase focused on understanding the dataset, uncovering patterns, and identifying trends that may contribute to customer churn. Key steps included:

1. **Data Inspection:** We examined basic statistics, missing values, and data types to ensure data quality and identify any potential issues.

2. **Outlier Detection and Handling:** Outliers were identified using box plots and histograms, especially in columns related to customer usage and recharge amounts. We applied techniques such as capping to manage extreme values.

3. **Class Imbalance Check:** The churn rate was found to be significantly imbalanced, with approximately 8% churners and 92% non-churners. We noted this for use in later model training, where we applied class balancing techniques.

4. **Churn Trends Analysis:** We analyzed key usage metrics like total recharge amount, call durations, and data usage by churn and non-churn classes to identify features with different distributions across churners and non-churners. These trends indicated potential predictors of churn, such as lower recharge amounts and usage patterns.

## Handling Multicollinearity (VIF)
To identify and mitigate multicollinearity (highly correlated predictor variables) that could impact model stability:

1. **Correlation Heatmap:** A correlation heatmap was created to visually inspect relationships between variables. This helped identify pairs of features with high correlations.
2. **Variance Inflation Factor (VIF):** We calculated the VIF for each predictor variable. Variables with high VIF values (>10) were considered highly collinear.
3. **Feature Selection:** Based on VIF values, we dropped or transformed some variables to reduce multicollinearity, ensuring more reliable coefficient estimates in our logistic regression model.

## Model Building
We built two models to address the project goals: Logistic Regression and Random Forest.

**1. Logistic Regression**
- **Objective:** To predict churn probability and identify important predictor variables. Logistic regression is interpretable and useful for identifying key churn drivers.
- **Class Imbalance Handling:** We used the class_weight='balanced' parameter to handle the class imbalance in the dataset.
- **Multicollinearity Handling:** The logistic regression model required multicollinearity mitigation through VIF analysis, as discussed above.
- **Evaluation:** The model was evaluated using AUC-ROC and F1 Score. The AUC-ROC score indicated how well the model could distinguish between churners and non-churners, while the F1 score balanced precision and recall.

**2. Random Forest**
- **Objective:** Random Forest is a non-linear, tree-based model that handles feature interactions well and is effective in identifying feature importance.
- **Class Imbalance Handling:** The class_weight='balanced' parameter was also applied here.
- **Evaluation:** Random Forest outperformed Logistic Regression in both AUC-ROC and F1 score, showing better predictive power and robustness against the class imbalance in the dataset.

### Model Evaluation Summary:

- **Logistic Regression AUC-ROC:** 0.898
- **Logistic Regression F1 Score:** 0.476
- **Random Forest AUC-ROC:** 0.928
- **Random Forest F1 Score:** 0.564

Random Forest emerged as the preferred model due to its higher performance on both metrics, making it more reliable for deployment.

## Feature Importance Visualization

We visualized the most important features for both models to gain insights into the key drivers of customer churn.

**1. Logistic Regression:**
- Coefficients of the logistic regression model were plotted to show the top 10 most influential features.
- Features with positive coefficients increase the likelihood of churn, while negative coefficients reduce it.

**2. Random Forest:**
- Feature importances were extracted from the Random Forest model and plotted, revealing the top 10 factors contributing to churn prediction.
- The Random Forest model emphasized features related to recent usage and recharge behaviors, indicating these variables are significant churn indicators.

The visualizations provided actionable insights into which factors most strongly influence churn behavior, supporting business decisions on customer retention strategies.

## Insights and Strategy Contribution
Based on the findings from our customer churn model, several insights have emerged that can guide strategic actions for the telecom company to retain high-value customers:

**1. Key Churn Indicators:**

- **Recharge Amounts and Usage Patterns:** The model indicates that churners tend to have lower average recharge amounts and lower call or data usage in recent months. This trend suggests that customers may be disengaging with the service before fully churning.
- **Roaming and International Usage:** High usage of roaming and international call minutes (as shown in the Random Forest feature importance) appears to be a significant churn indicator. Customers with high roaming usage might be at risk if they find better international plans elsewhere.
- **Last Interaction Metrics:** Features such as last recharge amount and frequency of recent transactions have strong predictive power. Customers who have lower recharges in the most recent months may signal a risk of disengagement.

**2. Segmented Retention Strategies:**

- **Low Recharge and Low Usage Customers:** For customers identified with low recharge and usage patterns, offering personalized incentives such as bonus minutes, additional data, or limited-time discounts could encourage continued engagement.
- **High Roaming Customers:** For customers with high roaming or international usage, targeted offers that provide better roaming rates or international calling plans can increase loyalty and reduce the likelihood of churn.
- **Infrequent Rechargers:** Customers who recharge infrequently might benefit from reminders or special offers before they are due for recharge, potentially preventing disengagement.

**3. Proactive Customer Engagement:**

- **Predictive Alerts for At-Risk Customers:** Implement an early warning system based on the model's churn probabilities to flag high-risk customers. Customer service teams can proactively reach out to these customers to offer tailored retention plans or solve potential pain points.
- **Loyalty Programs:** Offer loyalty points or rewards for long-standing customers or those with high usage, especially among the features identified as churn drivers. Rewarding loyalty can improve customer satisfaction and reduce the likelihood of churn among high-value customers.

**4. Product and Service Improvements:**

- **Enhanced Data and Voice Plans:** Based on the significant influence of usage features, the company could develop data and voice plans that better fit the needs of its customer base, particularly addressing patterns of high roaming or domestic usage.
- **Feedback Collection:** For customers identified as high-risk, collect feedback on what improvements or additional features they would like. Understanding customer needs could help reduce churn by adapting services accordingly.