# Project
# Car Pricing with Linear, Random Forest and Decision Tree Regression

The given requirements of the project were to take an econometric / statistical analysis, translate it to a different language and improve the study. 
Based on the instructions, we choose Car Pricing with Linear Regression topic from Kaggle written in R code and translated it to Python and reproduced the results. Additionally, random forest and decision tree regression analysis also performed to compare the performance of the model with linear regression.

To predict car pricing, a linear regression model along with traditional and machine learning modelling was used. The main basis of the process was to predict and analyse how the price of cars responds based on the changes in their features. 

The results of our study demonstrated the effectiveness of the linear regression model in predicting cars’ prices.

As we stated above we used linear regression as it is one of the most common types of statistical analysis which is used to predict the relationship between two variables. 

The coding process started with importing the necessary libraries and car pricing data. Below, the descriptions of the features on the dataset can be found;

Car_ID                     - Unique id of each observation 
Symboling                  - Insurance risk rating,  +3 indicates risky auto, -3 indicates pretty safe auto
carCompany                 - Name of car company 
fueltype                   - Car fuel type 
aspiration                 - Aspiration used in a car 
doornumber                 - Number of doors in a car 
carbody                    - Body of car 
drivewheel                 - Type of drive wheel 
enginelocation             - Location of car engine 
wheelbase                  - Weelbase of car 
carlength                  - Length of car 
carwidth                   - Width of car 
carheight                  - Height of car 
curbweight                 - The weight of a car without occupants or baggage. 
enginetype                 - Type of engine. 
cylindernumber             - Cylinder placed in the car 
enginesize                 - Size of car
fuelsystem                 - Fuel system of car 
boreratio                  - Boreratio of car 
stroke                     - Stroke of the engine
compressionratio           - Compression ratio of car 
horsepower                 - Horsepower 
peakrpm                    - Car peak rpm
citympg                    - Mileage in city 
highwaympg                 - Mileage on highway
price(Dependent variable)  - Price of car 

Since it didn't have any impact on car prices we dropped Car ID from our data set. To gain a clearer understanding of the data, we plotted the prices to observe the distribution and determine if there is an asymmetry present. The distribution of the price is right-skewed, which could lead to outliers in the tail region and this could negatively affect the performance of the model. Therefore, log-linear regression might be better suited than simple linear regression for our model. 

## Cleaning 

Before performing any analysis in order to get high-quality information and to improve the performance of the model, we did data cleaning and transformation. The CarName column was separated into two columns, 'Brand' and Model, to facilitate a clearer interpretation of the data. We had to check our data for any incorrect spellings to ensure accuracy and it turned out that 5 car brand names were spelled incorrectly. Correcting the spellings of brands in the dataset was done to improve the quality of the data. Symboling in our dataset indicates an insurance risk rating. Values of +3 signify the highest risk, while -3 indicates the lowest risk. We categorized these risk levels into high, medium, and low risk by using the lambda function.

## Feature Analysis

For the purpose of data understanding, model improvement and model interpretability, we conducted a features analysis. Firstly, we created barplots for feature distributions based on the prices.
These barplots gave us the information that how there are more low price cars and type gas cars. We concluded from the barplots that prices typically increase as a result of factors including diesel fuel, turbo aspiration, four doors, rwd drivewheel, rear engine placement, and advanced engine type and the cost of the cars influenced by factors like fuel type, aspiration, door number, drivewheel, engine location, and engine type.

Secondly, we created scatter plots which show the distribution of the rest of the features based on prices. Those gave us clear understanding that car's price is positively correlated with features including wheel base, car length, car width, curb weight, engine size, bore ratio, and horsepower. Features such as larger wheel base, longer and wider cars, heavier curb weight, bigger engine size, larger bore ratio, and higher horsepower indicates more luxurious and higher-priced vehicles.This implies that the price of the car typically rises along with the value of these factors.

## Outlier check and Treatment

To have a high accurate result for the model one of the most important steps of data processing is to check if there is any outliers and to treat them.Outliers are data points which are significantly smaller or larger than the remaining data set. From the right-skewed distribution we already aware of the possibility of the outlier. Hence we started to detection of the outlier by listing all the numeric variables in dataframe and create Categorical and Continues columns. In order to check and remove outliers from Continues column we calculated the lower and upper boundaries and assigned highest and the lowest values to outliers. Finally, as an output we got a 0 which means there is not any NaN value. 

As a next step, We had to make dataframe suitable for further implication of linear regression modeling. For this firstly, we changed categorical variables to numerical variable and used scaler function for continues columns and concatenated the results which transformed the data into numerical format to make inretpretation easy for us.

Finally, we started the process of creating the linear regression model.For this, initially dataset into training and testing data with percentage 70% and 30% relatively. 

Then we used training data to create modeling including all the features.
From our first model, we got the result R squared – 1 which means our model is perfectly fit to predict price while Adjusted R squared being nan indicates that we need to eliminate some variables since we 143 observations and 217 different independent variables for which we can not reject the hypothesis that their coefficient is not 0. 

This is where we faced one of our challenges. On the project we took from Kaggle this part was used stepAIC function,so in order to solve this issue we had to use  stepwise_regression library and since jupyter is unable to install and call functions of it, we manually added them here. This library is a great tool to help to select the most important variables for the model.

After the help of the library to choose the best fitted features for our model we started to create linear regression modeling.

This second model gave us R^2 of 95%, so on Model 3 we dropped the variables with highest p value which was the enginesize. Afterwards we constructed 7 additional models stematically removing the variables with insignificant variables (Model_504(SW), Model_304, Model_CENTURY, highwaympg, Brand_SAAB, wheelbase, carbody_convertible, ) and those with the highest p-values one by one.

## Random Forest and Decision Tree Regression Analysis







