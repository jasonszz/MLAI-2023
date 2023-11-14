# Project: Will a Customer Accept the Coupon? 

**Author:**
Jason Su

## Executive summary
From a business perspective, we are tasked with identifying key drivers for what would make a Customer to accept the coupon while driving throught a town. In the CRISP-DM overview **[Here](https://github.com/jasonszz/MLAI-2023/tree/main/Module_20_Capstone_Project_Initial_Report_and_EDA/CRISP-DM%20Framework)**, we are asked to convert this business framing to a data problem definition. Using a few sentences, reframe the task as a data task with the appropriate technical vocabulary.

In current marketing advertising business, coupon distribution has been one of the effective ways to engage customers with business products or service promotion, whether is for preserving current customers or attracting new customers.

Rather than frequently and randomly sending out coupon to each customer, which could potentially damage a business reputation (such as junk solicitation) and waste limited advertising resource (such as budget), understanding the customers' preference first would help business send the right coupon that could match the customers' needs.

According to each customer's different profile character, such as shopping preference or spending limit, predicting whether a customer will accept the coupon is a difficult task. however, with the help of machine learning techniques, we can build a prediction model that could help the business get an insight of what are the most importance features that related to customers, based on customers' profile character and shopping history, and then distributing the correct coupon accordingly.

## Rationale
Advertise churn prediction is an significant factor to business marketing strategy. Understanding "Whether a driver is likely to accept a coupon?" will provide business insight regarding to which factor(s) are related to customers' needs or interests, which will help business create effective and profitable marketing campaign to the targeted (related) customers, with limited resource, such as budget funding.

In addition, the idea of this project can also be implemented into other field of the business's churn prediction task, such answering "whether a customer is likely to subscribe (to a service/plan)?", which will open up other business's opportunities. 

## Research Question
Imagine driving through town and a coupon is delivered to your cell phone for a restaraunt near where you are driving. 

- Would you accept that coupon and take a short detour to the restaraunt?
- Would you accept the coupon but use it on a sunbsequent trip?
- Would you ignore the coupon entirely?
- What if the coupon was for a bar instead of a restaraunt?
- What about a coffee house? Would you accept a bar coupon with a minor passenger in the car?
- What about if it was just you and your partner in the car?
- Would weather impact the rate of acceptance? What about the time of day?

Obviously, proximity to the business is a factor on whether the coupon is delivered to the driver or not, but what are the factors that determine whether a driver accepts the coupon once it is delivered to them? How would you determine whether a driver is likely to accept a coupon?

## Data Sources
This data comes to us from the UCI Machine Learning repository and was collected via a survey on Amazon Mechanical Turk **[Here](https://archive.ics.uci.edu/dataset/603/in+vehicle+coupon+recommendation)**. The survey describes different driving scenarios including the destination, current time, weather, passenger, etc., and then ask the person whether he will accept the coupon if he is the driver. Answers that the user will drive there ‘right away’ or ‘later before the coupon expires’ are labeled as ‘Y = 1’ and answers ‘no, I do not want the coupon’ are labeled as ‘Y = 0’. There are five different types of coupons -- less expensive restaurants (under $20), coffee houses, carry out & take away, bar, and more expensive restaurants ($20 - $50).

Keep in mind that these values mentioned below are average values.

The attributes of this data set include:

**1. User attributes:**

-  Gender: male, female
-  Age: below 21, 21 to 25, 26 to 30, etc.
-  Marital Status: single, married partner, unmarried partner, or widowed
-  Number of children: 0, 1, or more than 1
-  Education: high school, bachelors degree, associates degree, or graduate degree
-  Occupation: architecture & engineering, business & financial, etc.
-  Annual income: less than \\$12500, \\$12500 - \\$24999, \\$25000 - \\$37499, etc.
-  Number of times that he/she goes to a bar: 0, less than 1, 1 to 3, 4 to 8 or greater than 8
-  Number of times that he/she buys takeaway food: 0, less than 1, 1 to 3, 4 to 8 or greater
than 8
-  Number of times that he/she goes to a coffee house: 0, less than 1, 1 to 3, 4 to 8 or
greater than 8
-  Number of times that he/she eats at a restaurant with average expense less than \\$20 per
person: 0, less than 1, 1 to 3, 4 to 8 or greater than 8
-  Number of times that he/she goes to a bar: 0, less than 1, 1 to 3, 4 to 8 or greater than 8

**2. Contextual attributes**

- Driving destination: home, work, or no urgent destination
- Location of user, coupon and destination: we provide a map to show the geographical
location of the user, destination, and the venue, and we mark the distance between each
two places with time of driving. The user can see whether the venue is in the same
direction as the destination.
- Weather: sunny, rainy, or snowy
- Temperature: 30F, 55F, or 80F
- Time: 10AM, 2PM, or 6PM
- Passenger: alone, partner, kid(s), or friend(s)

**3. Coupon attributes**

- time before it expires: 2 hours or one day

## Methodology
The goal of this project is to select the most effective model to help predict whether a customer will accept the coupon. For customers who choose to accept the coupon are labeled as Y = 1 (True), whereas who choose to reject the coupon are labeled as Y = 0 (False), which turns this task into be a Classification problem, under supervised machine learning.

Thus, we will build and train multiple machine learning Classification models with customers' profile character (such as demographic and contextual attributes), compare each model's performance efficiency, and select the best model. With the selected best model, we will further identify which feature(s) that most effectively influence the predicting accuracy to whether a customer will likely accept the coupon.

This project will be utilizing CRISP-DM process model methodology, which including:

- Business Understanding
- Data Understanding
- Data Preparation
- Modeling
- Evaluation
- Deployment (not currently, but future plan) 

***For details about Exploratory Data Analysis (EDA), Data Preparation, Modeling, and Evaluation, please click [Here](https://github.com/jasonszz/MLAI-2023/blob/main/Module_20_Capstone_Project_Initial_Report_and_EDA/Module_20_Capstone_Project_Initial_Report_and_EDA_JasonSU_v2_Final.ipynb) for full Notebook.***

## Results
According to the provided dataset contain **partial balanced data**, we cannot rely on a performance metric that merely focus on Accuracy score, when comes to model performance comparison. Although all of our built models (Logistic Regression vs KNeighbors vs Decision Tree vs SVM vs Random Fores vs XGBClassifier) have their limitation, their performances all surpassed the baseline model (DummyClassifier). 

By tuning our models with Grid Search (to compute the best Hyperparameter) and utilizing the other two more proper Performance Metrics (**F1 score** and **ROC_AUC score**), we conclude that **XGBClassifier** has the best overall performance, in term of best "accuracy" (best F1 score and ROC_AUC score), but relatively high **computation cost** (2nd longest elapsed time consumption).

With our selected **best model (XGBClassifier)** and the help of permutation importance feature, we are able to compute and visualize the importance of features that may directly influence the Target feature (Wether Customer Will Accept the Coupon). Here are the top 5 features that may impact the decision making to our Target feature.

1. CoffeeHouse
2. expiration
3. income
4. destination
5. occupation

![Alt text](https://github.com/jasonszz/MLAI-2023/blob/main/Module_20_Capstone_Project_Initial_Report_and_EDA/images/Plot_important_features_from_permutation_importance_xgb.png)

**Note:** Feature "coupon" contains different type of coupon (Restaurant(<20 dollar), Coffee House, Carry out & Take away, Bar, Restaurant(20 dollar - 50 dollar)).

## Next steps
In order to achieve better performance and more meaningful result, here are some recommend steps:

- Gather more data for feature engineering, for example, gather features like clients' hobby (User attribute). This will require partner with domain expert
- Data cleaning, such as identify missing value in data point
- Utilize other technique, such as SMOTE and CatBoost Classifier to handle class partial balance or imbalanced concern
- Introduce Time Series analysis for feature group (like time) 
- Utilize other technique for high dimensionality reduction (such as PCA or k-means clustering)

## Outline of project
For this project details (including dataset and images), please click **[Here](https://github.com/jasonszz/MLAI-2023/tree/main/Module_20_Capstone_Project_Initial_Report_and_EDA)**.

## Contact and Further Information
**Author:**
Jason Su
