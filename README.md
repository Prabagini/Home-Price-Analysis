![img1](https://user-images.githubusercontent.com/70337178/110574559-5126b480-812b-11eb-9546-63d0d86c6649.jpeg)
# King County Home Price Analysis

This repository offers an analysis of factors that influence housing prices in King County, WA



Environment setup process:

- conda create --name ENV

- conda activate ENV


## Business Understanding

King County is located in the U.S. state of Washington. The population was 2,252,782 in the 2019 census estimate, making it the most populous county in Washington, and the 12th-most populous in the United States. All this growth has increased demand for housing and caused home prices to skyrocket. A client in King County, WA wants to advise homeowners on home improvement projects that will add sale value of their homes.


This is a complex market for home buyers and my goal is to build a linear regression model to represent home sale prices in King County, and use it to advise homeowners on which home improvement projects will add to their home sale values.

## Data Understanding

 I have been provided with King County House Sales datasets: 
 
- Real Property Sales 
- Residential Building 
- Parcel 

There were total of 2,51,300 rows and 136 columns in the given datasets. 

## Data Preparation

Started with initial cleaning of the given datasets. In the parcel,rpsale,residential building tables there are columns with null values and i have dropped those columns. concatenating three tables using (Major and Minor)columns. There were about (2,51,300 rows and 136 columns) in my initial data process. After the thorough data cleaning, i have narrowed down to (18204 rows and 57 columns). Since my focus of the project is on 2019, I decided to only look at transactions that were documented within 2019 and For my analysis i'm going to Focus on the Data for 'Single Family Units' property type because it has more data. The final dataframe used for my analysis contains 18,204 rows and 57 columns. CRISP-DM stands for cross-industry process for data mining. I have followed CRISP-DM process for my data modelling process. 

## Modeling

I have used OLS Regression Results and Scikit Learn to build a multilinear regression model to predict house prices using the King County House Sales dataset.

Visual1:

The heatmap plot were generated to find the features that are most correlated with the SalePrice target.

![graph1](reports/Model1.png)

In this heatmap SalePrice is highly correlated to SqFtTotLiving. Saleprice is fairly correlated to SqFt1stFloor, SqFt2ndFloor, BathFullCount, SqFtFinBasement.

Visual2:

Starting with a simple model. The targeted variable is SalePrice and i'm taking one independent variable which is highly correlated with Saleprice. Building a simple model.

![graph1](reports/Mode2.png)

OLS Regression Results
Dep. Variable:	SalePrice	R-squared:	0.398
Model:	OLS	Adj. R-squared:	0.398
Method:	Least Squares	F-statistic:	1.205e+04
Date:	Fri, 05 Mar 2021	Prob (F-statistic):	0.00
Time:	12:39:28	Log-Likelihood:	-2.6297e+05
No. Observations:	18204	AIC:	5.259e+05
Df Residuals:	18202	BIC:	5.260e+05
Df Model:	1		
Covariance Type:	nonrobust		
coef	std err	t	P>|t|	[0.025	0.975]
Intercept	-2.765e+04	8226.230	-3.361	0.001	-4.38e+04	-1.15e+04
SqFtTotLiving	382.8579	3.487	109.793	0.000	376.023	389.693
Omnibus:	23583.917	Durbin-Watson:	1.994
Prob(Omnibus):	0.000	Jarque-Bera (JB):	13528011.140
Skew:	6.802	Prob(JB):	0.00
Kurtosis:	135.854	Cond. No.	5.76e+03

![graph1](reports/Model3.png)

![graph2](reports/Model4.png)



## Evaluation

Started with simple linear regression model. In model2 added log transform for both targeted variable and predictor but there was a drop in R-squared value. In model3 removied outliers from targeted variable and proceed with analysis. With an increase in 1 sqft, the saleprice is expected to increase by $200.44. In the model4 performed square root scaling and With an increase in 1 sqft, the saleprice is expected to increase by $1.825e+04. In the model5 added new predictors and the R-squared value has increased from 0.313 to 0.399. In the model6 added additional predictors such as SqFt1stFloor, SqFt2ndFloor, BathFullCount and the  R-squared value has increased from 0.399 to 0.40.

In the model7 added categorical features. Adding categorical features such as 'HeatSystem', 'HeatSource', 'Bedrooms', 'BldgGrade', Model 7 tells that about 53.2% variance of SalePrice. But the p-value(0.03777) is lesser than (alpha=0.05) alpha value. So we reject the null hypothesis. It fails to the linearity assumptions. 


## Conclusion

Home buyers in this market who are looking to maximize their dollars should carefully consider the locations in which they search. This will make the biggest impact on how far their budget will go. The second most important factor in housing is the square footage of the house.

This model can account for 53.2% of the variability in house prices in King County, which is a 10% increase from my initial model. I think the model is a decent start, but could be improved by doing more to work out the best transformation method for each feature.

## Next Step

- The model has some limitations to satisfy regression assumptions.

- Our model has multicollinear relationship between the variables. Hence futher processing needs to be done on removing the multicollinearity.

- Stepwise selection can be done to further narrowdone the feature of the model.

## This Repository

### Repository Directory

```
├── README.md        <-- Main README file explaining the project's business case,
│                        methodology, and findings
│
├── data             <-- Data in CSV format
│   ├── processed    <-- Processed (combined, cleaned) data used for modeling
│   └── raw          <-- Original (immutable) data dump
│
├── notebooks        <-- Jupyter Notebooks for exploration and presentation
│   ├── exploratory  <-- Unpolished exploratory data analysis (EDA) notebooks
│   └── report       <-- Polished final notebook(s)
│
├── references       <-- Data dictionaries, manuals, and project instructions
│
└── reports          <-- Generated analysis (including presentation.pdf)
    └── figures      <-- Generated graphics and figures to be used in reporting
```
