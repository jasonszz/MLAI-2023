# MLAI-2023
UC Berkeley Machine Learning and Artificial Intelligence 2023

# Practical Application Assignment 3 (Module 17): Comparing Classifiers

With a given dataset that contains almost 42K input variables information that related with a Portuguese banking institution direct marketing campaigns throught directly phone call to their potential clients, the goal of this project is to build different models (K Nearest Neighbor, Logistic Regression, Decision Trees, and Support Vector Machines) for this classification task (predict if a client will subscribe the deposit, not regarding which amount is retained), and compare each model's performance efficiency.

## Overview

The provided dataset contains information on almost 42k clients information through phone calls with multiple atrributes that could potentailly help to classify whether a client will subscribe the deposit. While performing this classification task, we will also evaluate multiple different models' (clasifiers, including K Nearest Neighbor, Logistic Regression, Decision Trees, and Support Vector Machines) performace with a proper Performance Metric.

The analysis procedure will follow CRISP-DM Framework with standard process in the indestry for data projects.

## Business Understanding

According to **Materials and Methods** section of the paper [Here](https://archive.ics.uci.edu/dataset/222/bank+marketing), this dataset collected is related to total 17 campaigns that occurred between May 2008 and November 2010, corresponding to a total of 79354 contacts made.

According the to collected bank direct marketing data, the **Business Objective** here is to increase efficiency (success rate) of more productive campaign method, directed marketing campaigns, with offering attractive long-term deposit subscription, while saving the time and minimizing the cost by reducing the number of contacts that required to make.

## Data Understanding

Our dataset contains almost 42K clients data throuth phone call contacts. Because the goal is to build different models (K Nearest Neighbor, Logistic Regression, Decision Trees, and Support Vector Machines) for this classification task (predict if a client will subscribe the deposit, not regarding which amount is retained), and compare each model's efficiency, we should define a proper Performance Metric that could cover most importance factor, for exmample, computational cost (in term of time elapsed), model score (in term of Accuracy, Precision, Recall or F1 score from the common metric of Confusion Matrix).

In addition, according to the computation result of probability distribution rate of target value 'subscribe' (Count of Clients Subscribed a Term Deposit), this provided dataset is a highly **imbalanced dataset**, with rate of No (False or 0) as 88%, whereas Yes (True or 1) as 11%. This insight will impact the later decision making of model choosing based on the how well does the model handle imbalanced dataset.

Furthermore, after analyzed the data, no **missing data (Null value)** in the dataset; however, due to multiples features contains value as "unknown", This insight will also impact the later decision making of model choosing based on the how well does the model handle missing values.

Here is the list of factors/features that are involed in this analysis:

**bank client data:**
1 - age (numeric)
2 - job : type of job (categorical features)
3 - marital : marital status (categorical: features)
4 - education (categorical features)
5 - default: has credit in default? (categorical features)
6 - housing: has housing loan? (categorical features)
7 - loan: has personal loan? (categorical features)

**related with the last contact of the current campaign:**
8 - contact: contact communication type (categorical features)
9 - month: last contact month of year (categorical features)
10 - day_of_week: last contact day of the week (categorical features)
11 - duration: last contact duration, in seconds (numeric features). Important note: this attribute highly affects the output target (e.g., if duration=0 then y='no'). Yet, the duration is not known before a call is performed. Also, after the end of the call y is obviously known. Thus, this input should only be included for benchmark purposes and should be discarded if the intention is to have a realistic predictive model.

**other attributes:**
12 - campaign: number of contacts performed during this campaign and for this client (numeric features)
13 - pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric features; 999 means client was not previously contacted)
14 - previous: number of contacts performed before this campaign and for this client (numeric features)
15 - poutcome: outcome of the previous marketing campaign (categorical features)

**social and economic context attributes:**
16 - emp.var.rate: employment variation rate - quarterly indicator (numeric features)
17 - cons.price.idx: consumer price index - monthly indicator (numeric features)
18 - cons.conf.idx: consumer confidence index - monthly indicator (numeric features)
19 - euribor3m: euribor 3 month rate - daily indicator (numeric features)
20 - nr.employed: number of employees - quarterly indicator (numeric features)

**Output variable (desired target):**
21 - y - has the client subscribed a term deposit? (binary: 'yes','no')

**For details about Exploratory Data Analysis (EDA), Data Preparation, Modeling, and Evaluation, please click [Here]() for full Notebook.**

## Finding



## Conclusion



## Next step and Recommendations

For future model improvement, do keep in mind that due to the large missing value and duplicate data in the dataset, multiple actions, like dropping data and filling data (based on certain inference correlated relation) was required to be complete in order to make the data to be useful for our model training. In addition, features like model, state may also has significant influences to the price of a used cars' prices, but they were dropped due to their ambiguous data value. That being said, in order to improve our model, more data preparation process is required. With more precise data, we can re-introduce the dropping features and re-train our model, which will lead to produce a better model with more accurate prediction results.

For this project details (including dataset and images), please click [Here](https://github.com/jasonszz/MLAI-2023/tree/main/Module_17_Practical_Application_3).
