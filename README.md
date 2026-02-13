
Overview

Customer churn represents a significant financial risk for telecommunications companies, as lost customers reduce recurring revenue and increase acquisition costs.

This project develops a machine learning classification model to predict whether a customer is likely to churn. The goal is to support SyriaTel’s customer retention team in proactively identifying at-risk customers and implementing targeted intervention strategies.

Business and Data Understanding
Stakeholder

The primary stakeholder is SyriaTel, specifically, The Customer Retention Manager .

Their objective is to reduce revenue loss by identifying customers who are likely to discontinue their service.

Business Problem

Only a small percentage of customers churn (approximately 14.5%), but these customers account for significant lost revenue.

The key expectation is whether we can we predict which customers are likely to churn using historical customer behavior data.

If successful, the model can help prioritize retention efforts toward high-risk customers.

Dataset Description

The dataset contains 3,333 customer records and 21 variables, including:

Customer demographics (e.g., state, account length)

Usage patterns (day, evening, night, and international usage)

Service features (international plan, voice mail plan)

Customer service interactions

Target variable: churn 

It is important to note that the dataset is imbalanced:

85.5% of customers did not churn

14.5% of customers churned

Because of this imbalance, evaluation metrics beyond accuracy were necessary.

Modeling

An iterative modeling approach was used:

1. Baseline Logistic Regression

A simple logistic regression model was trained as a baseline.

Although overall accuracy was high (86%), recall for churn was only 27%, meaning the model failed to identify most at-risk customers.

2. Tuned Logistic Regression

To address class imbalance, a logistic regression model using class_weight='balanced' was implemented.

This significantly improved churn recall (70%), but precision dropped to 33%, meaning many customers were incorrectly flagged as high risk.

3. Decision Tree (Nonparametric Model)

A decision tree classifier was trained to capture nonlinear relationships in customer behavior.

The decision tree achieved:

90% accuracy

65% recall for churn

64% precision for churn

Although the tree overfit the training data, it demonstrated strong generalization on the test set and provided the best balance between recall and precision.

Evaluation

Because the dataset is imbalanced, recall for the churn class was prioritized over accuracy.

Final Model Performance (Decision Tree):

Accuracy: 90%

Recall (Churn): 65%

Precision (Churn): 64%

This means:

65% of customers who churn are correctly identified.

64% of customers flagged as high risk truly churn.

This balance supports effective and efficient retention intervention.

Key Insights

Feature importance analysis identified several strong predictors of churn:

High number of customer service calls

International plan subscription

High daytime usage

Customers with frequent service interactions are significantly more likely to churn, suggesting dissatisfaction may be a major driver of customer loss.

Conclusion

The Decision Tree model was selected as the final model because it provides the best balance between identifying churners and minimizing unnecessary interventions.

By implementing this model, SyriaTel can:

Prioritize high-risk customers

Improve customer service experience

Offer targeted retention incentives

Reduce revenue loss from churn

Limitations and Next Steps

Limitations:

The model is based on historical data and does not capture future behavioral shifts.


The decision tree shows signs of overfitting on training data.

