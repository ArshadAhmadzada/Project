# Project

# Car Pricing with Linear, Random Forest and Decision Tree Regression

## Introduction to the project

The given requirements of the project were to take an econometric / statistical analysis, translate it to a different language and improve the study. Based on the instructions, we choose Car Pricing with Linear Regression topic from Kaggle written in R code and translated it to Python and reproduced the results. Additionally, random forest and decision tree regression analysis also performed to compare the performance of the model with linear regression.

To predict car pricing, a linear regression model along with traditional and machine learning modelling was used. The main basis of the process was to predict and analyse how the price of cars responds based on the changes in their features.

The results of our study demonstrated the effectiveness of the linear regression model in predicting cars' prices.

As we stated above we used linear regression as it is one of the most common types of statistical analysis which is used to predict the relationship between two variables.

The coding process started with importing the necessary libraries and car pricing data.

## Overview of the data

The descriptions of the features on the dataset can be found below;

-   Car_ID - Unique id of each observation
-   Symboling - Insurance risk rating, +3 indicates risky auto, -3 indicates pretty safe auto
-   carCompany - Name of car company
-   fueltype - Car fuel type
-   aspiration - Aspiration used in a car
-   doornumber - Number of doors in a car
-   carbody - Body of car
-   drivewheel - Type of drive wheel
-   enginelocation - Location of car engine
-   wheelbase - Weelbase of car
-   carlength - Length of car
-   carwidth - Width of car
-   carheight - Height of car
-   curbweight - The weight of a car without occupants or baggage.
-   enginetype - Type of engine.
-   cylindernumber - Cylinder placed in the car
-   enginesize - Size of car
-   fuelsystem - Fuel system of car
-   boreratio - Boreratio of car
-   stroke - Stroke of the engine
-   compressionratio - Compression ratio of car
-   horsepower - Horsepower
-   peakrpm - Car peak rpm
-   citympg - Mileage in city
-   highwaympg - Mileage on highway
-   price(Dependent variable) - Price of car

Since it didn't have any impact on car prices we dropped *Car ID* from our data set. To gain a clearer understanding of the data, we plotted the prices to observe the distribution and determine if there is an asymmetry present. The distribution of the price is right-skewed, which could lead to outliers in the tail region and this could negatively affect the performance of the model.

## Data Cleaning

Before performing any analysis in order to get high-quality information and to improve the performance of the model, we did data cleaning and transformation. The CarName column was separated into two columns, 'Brand' and Model, to facilitate a clearer interpretation of the data. We had to check our data for any incorrect spellings to ensure accuracy and it turned out that 5 car brand names were spelled incorrectly. Correcting the spellings of brands in the dataset was done to improve the quality of the data. Symboling in our dataset indicates an insurance risk rating. Values of +3 signify the highest risk, while -3 indicates the lowest risk. We categorized these risk levels into high, medium, and low risk by using the lambda function.

## Feature Analysis

For the purpose of data understanding, model improvement and model interpretability, we conducted a features analysis. Firstly, we created barplots for feature distributions based on the prices. These barplots gave us the information that how there are more low price cars and type gas cars. We concluded from the barplots that prices typically increase as a result of factors including diesel fuel, turbo aspiration, four doors, rwd drivewheel, rear engine placement, and advanced engine type and the cost of the cars influenced by factors like fuel type, aspiration, door number, drivewheel, engine location, and engine type.

Secondly, we created scatter plots which show the distribution of the rest of the features based on prices. Those gave us clear understanding that car's price is positively correlated with features including wheel base, car length, car width, curb weight, engine size, bore ratio, and horsepower. Features such as larger wheel base, longer and wider cars, heavier curb weight, bigger engine size, larger bore ratio, and higher horsepower indicates more luxurious and higher-priced vehicles.This implies that the price of the car typically rises along with the value of these factors.

## Outlier check and Treatment

To have a high accurate result for the model one of the most important steps of data processing is to check if there is any outliers and to treat them.Outliers are data points which are significantly smaller or larger than the remaining data set. From the right-skewed distribution we already aware of the possibility of the outlier. Hence we started to detection of the outlier by listing all the numeric variables in dataframe and create Categorical and Continues columns. In order to check and remove outliers from Continues column we calculated the lower and upper boundaries and assigned highest and the lowest values to outliers. Finally, as an output we got a 0 which means there is not any NaN value.

As a next step, We had to make dataframe suitable for further implication of linear regression modeling. For this firstly, we changed categorical variables to numerical variable and used scaler function for continues columns and concatenated the results which transformed the data into numerical format to make inretpretation easy for us.

## Linear, Random Forest and Decision Tree Regression Analysis

Finally, we started the process of creating the linear regression model.For this, initially dataset into training and testing data with percentage 70% and 30% relatively.

Then we used training data to create modeling including all the features. From our first model, we got the result R squared -- 1 which means our model is perfectly fit to predict price while Adjusted R squared being nan indicates that we need to eliminate some variables since we 143 observations and 217 different independent variables for which we can not reject the hypothesis that their coefficient is not 0.

This is where we faced one of our challenges. On the project we took from Kaggle this part was used stepAIC function,so in order to solve this issue we had to use stepwise_regression library and since jupyter is unable to install and call functions of it, we manually added them here. This library is a great tool to help to select the most important variables for the model. Even though, we applied the code to select variables, it did not provide exactly same result we got from stepAIC - R library. So, we followed same logic used in R-Code to proceed further but due to issue mentioned above, we could not translate all the model from r-code exactly.

After the help of the library to choose the best fitted features for our model we started to create linear regression modeling.

This second model gave us R\^2 of 95%, so on Model 3 we dropped the variables with highest p value which was the enginesize. Afterwards we constructed 7 additional models stematically removing the variables with insignificant variables (Model_504(SW), Model_304, Model_CENTURY, highwaympg, Brand_SAAB, wheelbase, carbody_convertible, ) and those with the highest p-values one by one.

## Additional Models

On top of the models used in R-Code, we introduced 3 additional - Machine Learning models:

-   Linear Regression

-   Random Forest

-   Decision Tree

### Linear Regression by Machine Learning

We used sklearn library to model linear regression between price and independent variables and used RFECV function to find best hyper-parameters "*LinearRegression fits a linear model with coefficients w = (w1, ..., wp) to minimize the residual sum of squares between the observed targets in the dataset, and the targets predicted by the linear approximation."*

### Random Forest

After linear regression model, we created random forest regression model with GridSearchCV hyperparameter tunning.

Random forest is a machine learning algorithm which comparise many trees and provides average to give better results and improve performance of the model. We created the model with GridSearchCV to choose best hyperparameter which increases accuracy and performance of the model by avoiding over or underfitting.

As first step, data seperated once again as y_train1, x_train1, y_train1 and x_test1 to prevent the confusion with several splits from previous model linear regression and the base model rf = RandomForestRegressor() is provided.

Then, number of trees in the random forest, number of features, maximum number of levels in trees, minimum number of samples required to split a node and at each leaf node and method of selecting samples are defined to utilize on GridSearchCV. The numbers and features could be changed to increase performance and get better results. However, because of the time length of running, we keep them less.

param_grid defined with selected hyperparameters and GridSearchCV performed with param_grid, cv=5, verbose=2 and n_jobs = -1 for random forest model. GridSearchCV run all the possible combinations of the hyperparameters and provide the best combination with best results.

After running GridSearchCV, the model fit train data by rf_grid.fit(x_train1,y_train1) and best hyperparameters checked which are bootstrap = True, max_depth = 6, max_features = auto, min_samples_leaf = 3, min_samples_split = 3 and n_estimators = 41 with best score R2 almost 0.90 with rounding.

As last, model is validated with test data to check accuracy and performance. RMSE calculated and almost 0.31 RMSE result with rounding found.

### Decision Tree

Decision tree is also performed just to provide a visualization of the model with best hyperparameters found on previous model Random Forest regression. The model trained with train data and decision tree visualized to see dominant feature and how the tree built. It also predicted with test data and RMSE is calculated as the indicator of model accuracy. RMSE gave almost same result with random forest with hyperparameter tunning as 0.31 without rounding.

### Results of Models

As a results, Linear, Random Forest and Decision Tree regression models are performed to analyse car pricing dynamics. Linear regression technical anaylysis gives 0.33 RMSE result while Machine Learning Linear Regression gives 0.23 RMSE. Random Forest regression gives 0.30 RMSE and decision tree gives 0.31 RMSE.

Based on given results, it can be said that linear regression machine learning model perform better in comparison to others.
