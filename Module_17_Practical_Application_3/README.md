# MLAI-2023
UC Berkeley Machine Learning and Artificial Intelligence 2023

# Practical Application Assignment 3 (Module 17): Comparing Classifiers

With a given dataset (from UCI Machine Learning repository [Here](https://archive.ics.uci.edu/ml/datasets/bank+marketing)) that contains almost 42K input variables information that related with a Portuguese banking institution direct marketing campaigns throught directly phone call to their potential clients, the goal of this project is to build different models (K Nearest Neighbor, Logistic Regression, Decision Trees, and Support Vector Machines) for this classification task (predict if a client will subscribe the deposit, not regarding which amount is retained), and compare each model's performance efficiency.

## Overview

The provided dataset contains information on almost 42k clients information through phone calls with multiple atrributes that could potentailly help to classify whether a client will subscribe the deposit. While performing this classification task, we will also evaluate multiple different models' (clasifiers, including K Nearest Neighbor, Logistic Regression, Decision Trees, and Support Vector Machines) performace with a proper Performance Metric.

The analysis procedure will follow CRISP-DM Framework with standard process in the indestry for data projects.

## Business Understanding

According to **Materials and Methods** section of the paper [Here](https://github.com/jasonszz/MLAI-2023/blob/main/Module_17_Practical_Application_3/CRISP-DM-BANK.pdf), this dataset collected is related to total 17 campaigns that occurred between May 2008 and November 2010, corresponding to a total of 79354 contacts made.

According the to collected bank direct marketing data, the **Business Objective** here is to increase efficiency (success rate) of more productive campaign method, directed marketing campaigns, with offering attractive long-term deposit subscription, while saving the time and minimizing the cost by reducing the number of contacts that required to make.

## Data Understanding

Our dataset contains almost 42K clients data throuth phone call contacts. Because the goal is to build different models (K Nearest Neighbor, Logistic Regression, Decision Trees, and Support Vector Machines) for this classification task (predict if a client will subscribe the deposit, not regarding which amount is retained), and compare each model's efficiency, we should define a proper Performance Metric that could cover most importance factor, for exmample, computational cost (in term of time elapsed), model score (in term of Accuracy, Precision, Recall or F1 score from the common metric of Confusion Matrix).

In addition, according to the computation result of probability distribution rate of target value 'subscribe' (Count of Clients Subscribed a Term Deposit), this provided dataset is a highly **imbalanced dataset**, with rate of No (False or 0) as 88%, whereas Yes (True or 1) as 11%. This insight will impact the later decision making of model choosing based on the how well does the model handle imbalanced dataset.

Furthermore, after analyzed the data, no **missing data (Null value)** in the dataset; however, due to multiples features contains value as "unknown", This insight will also impact the later decision making of model choosing based on the how well does the model handle missing values.

Here is the list of factors/features that are involed in this analysis:

**bank client data:**

1. age (numeric)
2. job : type of job (categorical features)
3. marital : marital status (categorical: features)
4. education (categorical features)
5. default: has credit in default? (categorical features)
6. housing: has housing loan? (categorical features)
7. loan: has personal loan? (categorical features)

**related with the last contact of the current campaign:**

8. contact: contact communication type (categorical features)
9. month: last contact month of year (categorical features)
10. day_of_week: last contact day of the week (categorical features)
11. duration: last contact duration, in seconds (numeric features). Important note: this attribute highly affects the output target (e.g., if duration=0 then y='no'). Yet, the duration is not known before a call is performed. Also, after the end of the call y is obviously known. Thus, this input should only be included for benchmark purposes and should be discarded if the intention is to have a realistic predictive model.

**other attributes:**

12. campaign: number of contacts performed during this campaign and for this client (numeric features)
13. pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric features; 999 means client was not previously contacted)
14. previous: number of contacts performed before this campaign and for this client (numeric features)
15. poutcome: outcome of the previous marketing campaign (categorical features)

**social and economic context attributes:**

16. emp.var.rate: employment variation rate - quarterly indicator (numeric features)
17. cons.price.idx: consumer price index - monthly indicator (numeric features)
18. cons.conf.idx: consumer confidence index - monthly indicator (numeric features)
19. euribor3m: euribor 3 month rate - daily indicator (numeric features)
20. nr.employed: number of employees - quarterly indicator (numeric features)

**Output variable (desired target):**

21. y - has the client subscribed a term deposit? (binary: 'yes','no')

**For details about Exploratory Data Analysis (EDA), Data Preparation, Modeling, and Evaluation, please click [Here](https://github.com/jasonszz/MLAI-2023/blob/main/Module_17_Practical_Application_3/Module_17_prompt_III_JasonSU_v2_Final.ipynb) for full Notebook.**

## Finding
According above model comparison chart, all models (Logistic Regression, KNeighbors, Decision Tree, and Support Vector Machines(SMV)) are surpass the baseline model (DummyClassifier), with higher Train Score (Accuracy) and Test Score (Accuracy).

However, although the high **Accuracy** scores from each model looks great, there may still be issue, such as overfitting concern. For example, Decision Tree computed to the "best score" in Train Score (Accuracy) (approximate 99%), but holds the relatively "low" Test Score (Accuracy) (approximate 85%), which indicates that this model contains overfitting issue. 

In addition, according to the low **Recall** scores (all of them less than 0.5) from each model, another concern that raises up is that due to the current imbalanced dataset (as previously mentioned in the **EDA** phrase, as No (False or 0) as 88%, whereas Yes (True or 1) as 11%), all models (classifiers) have a high number of False negatives. Therefore, the model accuracy score calculation may not be useful, in term of basic (transitional) classification task processing, or model performance comparison and evaluation. 

Therefore, the following step will be model improving and introducing another two more proper Performance Metric for this kind of dataset, called **ROC_AUC** and **F1 Score**. ROC_AUC is well-known and widely used evaluation metric that can be implemented to optimistically handle heavily imbalanced dataset only with few samples from the minority class, while F1 Score is also a great evaluation metric which can handle well uneven class distribution by providing the measure of the harmonic mean of precision and recall.

ROC_AUC plots the False Positive Rate (FPR) versus the True Positive Rate (TPR), which allows visualizing how well the model's performance by identifying the class discrimination (in other words, distinguishing between the Postive classes and Negative classes). An ROC_AUC score is within a range from 0 to 1, as ideal model with score of 1, meaning the classifier can perfectly distinguish between all the Positive class points and the Negative class points. In general, a model with ROC_AUC score less than 0.5 indicates that the selected classifier may not work properly with the current dataset.

According the above model comparison chart, by focusing on the F1 score and ROC_AUC score, **Decision Tree** has the best overall performance (as approximate 0.37 in F1 score and approximate 0.8 in ROC_AUC score), despite it is ranked 2nd shortest elapsed time consumption (in term of computational cost). 

## Conclusion

Due to the provided dataset contain **high imbalanced data**, we cannot rely on a performance metric that merely focus on Accuracy score, when comes to model performance comparison. Although all of our built models (Logistic Regression vs KNeighbors vs Decision Tree vs SVM) have their limitation, their performances all surpassed the baseline model (DummyClassifier). 

By tuning our models with Grid Search (to compute the best Hyperparameter) and utilizing the other two more proper Performance Metrics (**F1 score** and **ROC_AUC score**), we conclude that Decision Tree has the best overall performance, in term of best "accuracy" (best F1 score and ROC_AUC score) and relatively less **computation cost** (2nd shortest elapsed time consumption).

With our selected **best model (Decision Tree)**, we then utilize one of its advantages, Tree Visualization, to help easy understand the interpret the decision split results. In addition, with the help of Grid Search tuning, our best model also demonstrates its ability of handling missing values (our dataset also contains some portion of "Unknown" data). 

***Note: Please download the image from folder named "images" for optimal visulization***

![Alt text](https://github.com/jasonszz/MLAI-2023/blob/main/Module_17_Practical_Application_3/images/decision_tree_graphivz.png)

Furthermore, with the help of permutation importance feature, we are able to compute and visualize the importance of features that may directly influence the Target Value (Wether Clients Subscribed a Term Deposit). Here are the top 3 features that may impact the decision making to our target value.

1. emp.var.rate
2. euribor3m
3. nr_employed

![Alt text](https://github.com/jasonszz/MLAI-2023/blob/main/Module_17_Practical_Application_3/images/Plot_important_features_from_permutation_importance.png)

However, due the high percentage of imbalanced data, despite the effort of building our best model, the outcome may seem to be lack of persuasiveness. 

## Next step and Recommendations

In order to achieve better performance and more meaningful result, here are some recommend steps:

- Gather more data, for example, informations like clients' income vs spending
- Data cleaning, such as identify "Unknown" data point
- Utilize other technique, such as SMOTE, XGBoost, and Random Forest to handle class imbalance concern
- Introduce Time Series analysis for feature group (like Day.of.Week) 

For this project details (including dataset and images), please click [Here](https://github.com/jasonszz/MLAI-2023/tree/main/Module_17_Practical_Application_3).
