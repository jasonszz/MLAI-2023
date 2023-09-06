# MLAI-2023
UC Berkeley Machine Learning and Artificial Intelligence 2023

# Practical Application Assignment 2: What drives the price of a car?

With a given dataset that contains more than 426K cars information, this assignment focuses on identifying what are the key factors that play an important role, when comes to deciding the price of a user car.

## Overview

The provided dataset contains information on 426K cars with multiple atrributes that could potentailly influence the prices of the cars. The goal is to understand what factors make a car more or less expensive. As a result of this analysis, the final report will provide clear recommendations to the client -- a used car dealership -- as to what consumers value in a used car.

The analysis procedure will follow CRISP-DM Framework with standard process in the indestry for data projects.

## Business Understanding

Unliked the fixed retail price of a new car, the price of a used car could be driven by multiple additional features, such as its overall condition, current driven odometer, title status, etc. As a dealer can act as both Seller and Buyer at the same time, it is crucial to have a used car price prediction model that could assist to identify what are the key factors that play an important role, when comes to deciding the price of a user car.

## Data Understanding

Our dataset contains more than 426K cars information. Because the goal is to understand what are the key factor that influence the price of a car, we should really focus on features that are actually coming from the car itself, such as its made of year, its condition, and its odometer, etc.

On the other hand, geographical information, such as region and state, which will be considered as "outlier" because if the price is depended on local government's unique policy, then it would be out of slope of this analysis. In addition, because different model of cars will have a different prices which are associated to its unique configuration, comparing the car price based on its model does not seem to be fair, due to lack of information about the detail of the car model configuration in our current dataset; however, in order to cover customers' personal preference, this analysis will keep manufacturer as one of the factor, which make it relatively reasonable especially after removing the model factor.

Here is the list of factors/features that are involed in this analysis:

1. price: Price of the car. Will be used as Prediction target value
2. id: An unique number to a car from dealership
3. year: Year of built or Year of model release of the car
4. manufacturer: manufacturer of the car
5. model: model of the car (e.g., Toyota, BMW, etc)
6. condition: condition of the car (e.g., excellent, good, like new, etc.)
7. cylinders: number of cylinders of the car (e.g., 4 cylinders, 6 cylinders, etc.)
8. fuel: fuel type of the car (e.g., gas, diesel, etc.)
9. odometer: number of miles the car has been driven
10. title_status: title status of the car (e.g., clean, missing, etc.)
11. transmission: transmission type of the car (e.g., automatic, manual, etc.)
12. VIN: Vehicle Identification Number of the car (A unique number to a car)
13. drive: drive type of the car (e.g., fwd, rwd, etc.)
14. size: size of the car (e.g., compact, mid-size, etc.)
15. type: type of the car (e.g., SUV, sedan, etc.)
16. paint_color: color of the car (e.g., Silver, Red, etc.)
17. state: state where the car is listing to sale

**For details about Exploratory Data Analysis (EDA), Data Preparation, Modeling, and Evaluation, please click [Here](https://github.com/jasonszz/MLAI-2023/blob/main/Module_11_Practical_Application_2/Module_11_prompt_II_JasonSU_v3_Final.ipynb) for full Notebook.**

## Finding

![Alt text](https://github.com/jasonszz/MLAI-2023/blob/main/Module_11_Practical_Application_2/images/Plot_important_features_from_permutation_importance.png)

Age (difference conversion from Year of the car) and Odometer (of the car) are the top 2 features that have the most impact to the used car prices. This results make sense because in general, car with younger age contains less odometer number (less driven time), which make people assume that the car has relatively better condition.

On the other hand, features like size (of the car), paint color (of the car), and title status (of the car) show the least important when coms to predict the price of a used car.

## Conclusion

As our primary goal is to identify the key drivers for used cars' prices, understand the relationship between each features to the target object, price, and their weight of influence to the target object, price, becomes an extreme crucial task.

In order to do make a useful predictive model which can help to estimate the uses cars's prices, we cleaned the dataset, create and run multiple regression models with the same preprocessed dataset, train and cross-validate all models by tuning up their Polynomial degree and Hyper-parameters in order to achieve their best performances, and then evaluating them along with one additional model, Random Forest Regressor, which is built as an actual machine learning algorithm.

Final decision to choose Random Forest Regressor as the best model, because it achieved the best scores in our evaluation system, despite its longest time consuming. Along with Permutation Importance feature, we concludes primary features, like Age (difference conversion from Year of the car) and Odometer (of the car) are the most important features, whereas other features like size (of the car), paint color (of the car), and title status (of the car) show the least important when coms to predict the price of a used car.

## Next step and Recommendations

For future model improvement, do keep in mind that due to the large missing value and duplicate data in the dataset, multiple actions, like dropping data and filling data (based on certain inference correlated relation) was required to be complete in order to make the data to be useful for our model training. In addition, features like model, state may also has significant influences to the price of a used cars' prices, but they were dropped due to their ambiguous data value. That being said, in order to improve our model, more data preparation process is required. With more precise data, we can re-introduce the dropping features and re-train our model, which will lead to produce a better model with more accurate prediction results.

For this project details (including dataset and images), please click [Here](https://github.com/jasonszz/MLAI-2023/tree/main/Module_11_Practical_Application_2).
