# Project
Project RR
Car Pricing with Linear Regression

The given requirements of the project were to take an econometric / statistical analysis, translate it to a different language and improve the study. 
Based on the instructions, we choose Car Pricing with Linear Regression topic from Kaggle written in R code and translated it to Python and reproduced the results. 

To predict car pricing, a linear regression model along with traditional and machine learning modelling was used. The main basis of the process was to predict and analyse how the price of cars responds based on the changes in their features. 

The results of our study demonstrated the effectiveness of the linear regression model in predicting cars’ prices.

As we stated above we used linear regression as it is one of the most common types of statistical analysis which is used to predict the relationship between two variables. 

The coding process started with importing the necessary libraries and car pricing data. Since it didn't have any impact on car prices we dropped Car ID from our data set. To gain a clearer understanding of the data, we plotted the prices to observe the distribution and determine if there is an asymmetry present. The distribution of the price is right-skewed, which could lead to outliers in the tail region and this could negatively affect the performance of the model. Therefore, log-linear regression might be better suited than simple linear regression for our model. 

Cleaning 

Before performing any analysis in order to get high-quality information and to improve the performance of the model, we did data cleaning and transformation. The CarName column was separated into two columns, 'Brand' and Model, to facilitate a clearer interpretation of the data. We had to check our data for any incorrect spellings to ensure accuracy and it turned out that 5 car brand names were spelled incorrectly. Correcting the spellings of brands in the dataset was done to improve the quality of the data. Symboling in our dataset indicates an insurance risk rating. Values of +3 signify the highest risk, while -3 indicates the lowest risk. We categorized these risk levels into high, medium, and low risk by using the lambda function.


