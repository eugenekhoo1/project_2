# Project 2: Predicting House Prices with Linear Regression

## Problem Statement

While there are a variety of valuation models to predict house prices, the objective of this exercise is to predict using non-financial related factors (such as mortgage rates, rental yields, comparables etc.). The factors considered in this exercise will consider features of houses instead. This includes quality of exterior, zoning, lot area, etc. 

As we attempt to model house prices, we are also interested in interpreting the factors that contribute to the dependent variable. From these objectives, we derive our problem statement: __How can we statistically predict and understand factors influencing house prices__.

## Methodology

Of the 80 independent variables in the dataset, we classified them into various categories and selected one from each. The selection was made based on the type of variables (with continuous preferred) and on the correlation with house prices.

|Column Name|Category|Variable Type|  
| --- | --- | --- |
|  __Overall Qual__     |General|Nominal (num scale)|
|   __MS Zoning__        |Location|Nominal|
|   __Lot Area (log)__         |Land|Continuous|
|  __Year Remod/Add__   |Age|Discrete|
|  __Exter Qual__       |Exterior|Ordinal|
|  __Total Bsmt SF__    |Basement|Continuous|
|  __Utilities__        |Utilities|Ordinal|
|  __Gr Liv Area__      |Built-up Area|Continuous|
|  __Full Bath*__        |Bathroom|Discrete|
|  __Half Bath*__        |Bathroom|Discrete|
|  __TotRms AbvGrd__    |Bedroom|Discrete|
|  __Fireplaces__       |Fireplace|Discrete|
|  __Garage Area__      |Garage|Continuous|

*Full Bath and Half Bath were combined to Total Bath

Non-residential properties were removed from the dataset for the regression (although a separate regression including them was done specifically for Kaggle due to the requirements)

We ran 3-fold cross validations on Linear, Lasso and Ridge regressions and found Linear Regression to be the best performing model.

## Summary

The regression results provide a R2 score of 0.848, implying that the variables selected are able to explain 84.8% of the variability in house prices.

#### Interpreting coefficients
Our baseline is for houses with Fair external quality, with no MS Zoning specified

<img src="https://github.com/eugenekhoo1/project_2/blob/main/images/regression-coefficients.png">

_Dummy Variables_
<br>An excellent (Ex) external quality is predicted to have a sale price approximately 23.8% more than a Fair (Fa) external quality home, ceteris paribus

_Continuous Variables_
<br>An increase in the overall quality score of the house by one unit is predicted to have a sale price approximately 10.4% higher, ceteris paribus

## Conclusion & Recommendation

To build on our earlier linear regression, we also ran it with standardized variables to show the magnitude of impact.

<img src="https://github.com/eugenekhoo1/project_2/blob/main/images/std-regression-coefficients.png">

Using standardized independent variables allows us to compare the magnitudes of impact for each coefficient. Overall quality has the largest impact on predicted sale prices. An increase in one standard deviation in overall quality will lead to a 0.162 standard deviation increase in house price.

Therefore, overall quality, exterior quality and lot area would be the top few factors to consider. This can be used for potential sellers/house flippers who are looking to profit from real estate.