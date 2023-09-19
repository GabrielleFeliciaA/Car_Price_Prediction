# Forecasting Car Prices with Linear Regression: A Data-Driven Approach

## Introduction
Creating a model using the linear regression algorithm to predict car prices and identify the most influential features affecting price fluctuations. The data used is relatively clean but still undergoes some data cleaning and processing steps, such as removing outliers in specific variables and performing other data transformations. In building the model, six linear regression models are developed and compared to identify the best-performing model. Model evaluation is conducted by examining the F-statistic value, Residual Standard Error, P-value, Adjusted R-squared value, and accuracy.

## Exploratory Data Analysis
In this phase, several steps were taken to understand the existing data, including outlier detection using three methods: the three sigma edit rule, hample identifier, and boxplot. Additionally, correlation analysis between attributes was conducted. The results of the analysis show that the strongest correlated attribute pairs are car width and curb weight with a correlation value of 0.87. The car width attribute describes the width of the car, while the curb weight attribute describes the weight of the car with a full fuel tank and all standard equipment, without passengers or baggage. These two attributes are strongly positively correlated, meaning that the wider the car, the greater the curb weight, and vice versa. In the real world, increasing the width of the car also adds more material, hence increasing the curb weight.

On the other hand, the strongest negatively correlated attribute pairs are horsepower and city mpg with a value of -0.80. Horsepower measures the car engine's power, while city mpg measures how many miles a car could go through per gallon inside a city (with stopping and braking). A strong negative correlation means that when one of the attributes goes up, the other one goes down. In this case, it could be assumed that more horsepower will result in fewer city miles per gallon, as more power will be generated, and vice versa.

Finally, the weakest correlated attribute pairs are the wheelbase attribute and the car name attribute with a value of 0.01. Car name is the name of the car model, while wheelbase measures the horizontal distance between the front wheels and the rear wheels. Wheelbase usually doesn't determine the car name.

It is also important to note that this data does not have any missing values.

## Data Processing
In the data processing phase, variables with character data types are converted to numeric data types to standardize all data types, and irrelevant columns are removed from the prediction process. Subsequently, outliers in the dependent variable `price` are also eliminated. Finally, before modeling, the data is divided into two parts, with 70% used for training and 30% for testing.

## Modelling
`Model 1` was initially created by modeling the dependent variable using all predictor variables. However, upon further examination, it was discovered that `Symboling`, `CarName`, `FuelType`, `Aspiration`, `CarBody`, and `CylinderNumber` variables had weak correlations with the dependent variable (`Price`). As a result, these variables were decided to be removed. Subsequently, `Model 2` was developed, modeling the dependent variable with the data after eliminating the aforementioned variables. The outcome of `Model 2` indicated an increased F-statistic to 104.3 and highly significant p-values for the predictors, signifying that this model outperformed the previous one (`Model 1`).

Additionally, a normality check was conducted for the remaining variables, revealing that the dependent variable (`Price`) did not follow a normal distribution (bell-shaped). Therefore, optimization was performed by applying the log() function to the dependent variable in `Model 3`. `Model 3` also demonstrated superior results compared to both `Model 1` and `Model 2`.

Subsequent to this, `Model 4` was created by modeling the dependent variable with only the curb weight and horsepower variables, as these two independent variables exhibited a strong linear relationship. The evaluation of `Model 4` further confirmed its improved performance compared to `Model 3`.

Moreover, an attempt was made to create a similar model to `Model 4` but with the application of natural logarithm to the `price` variable in `Model 5`. The results showed even better performance compared to `Model 4`.

Finally, `Model 6` was developed by modeling the natural log of the price variable and fitting it with the HorsePower variable. However, the evaluation of `Model 6` indicated a decline in performance, making it inferior to `Model 5`.


## Best Model Evaluation & Conclusion
The best model is `Model 5` due to its small Residual Standard Error value, the highest F-statistic value, the lowest P-value, and a high Adjusted R-squared value. `Model 5` boasts a Residual Standard Error value of 0.1701, which is sufficiently small, an Adjusted R-squared value of 0.8303, indicating a high degree of explanatory power, an impressive F-statistic value of 326.3, and a very low p-value of 1.321704e-51. Furthermore, `Model 5` achieves an accuracy of 82%. Consequently, `Model 5` performs linear regression for predicting car prices using the `curbweight` and `horsepower` attributes.

The equation line for Model 5 is as follows:
`log(Price) = 7.393 + CurbWeight*(0.0006371) + HorsePower*(0.002942)`

From the above equation, it can be simplified that there is a 0.00064% increase in the Price for every 1% increase in CurbWeight and a 0.0029% increase in the Price for every 1% increase in HorsePower.




