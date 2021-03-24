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

## Visual1:

The heatmap plot were generated to find the features that are most correlated with the SalePrice target.

![graph1](reports/Model1.png)

In this heatmap SalePrice is highly correlated to SqFtTotLiving. Saleprice is fairly correlated to SqFt1stFloor, SqFt2ndFloor, BathFullCount, SqFtFinBasement.

## Visual2:

Starting with a simple model. The targeted variable is SalePrice and i'm taking one independent variable which is highly correlated with Saleprice. Building a simple model.

![graph1](reports/Model3.png)

- This model predicts a saleprice of -27,650 USD when square feet to living is 0 sqft.
- With an increase in 1 sqft, the saleprice is expected to increase by 382.8579 USD.

## Visual3:

Performing log transformation for both the targeted and predictor variables to see if we could improve the R-squared performance.

![graph2](reports/Model4.png)

- p-value(0.9999) is greater than (alpha=0.05) alpha value.
- We fail to reject the null hypothesis. 


## Evaluation

This analysis have iterated through seven regression models, proceeding from a baseline model using one independent feature(SqFtTotLiving), I increased complexity of the model by adding additional predictors and applying transformations to both the predictors and the target. After each model was developed the assumptions of linear regression were evaluated. My baseline model had an r squared of 0.398 and violated the linearity and homoscedasticity assumptions. My final model had an R squared of 0.532 and violated the linearity and homoscedasticity assumptions. This final model used these features 'HeatSystem', 'HeatSource', 'Bedrooms', 'BldgGrade' as predictors. 

## Conclusion

Home buyers who are looking to maximize their dollars should carefully consider the locations in which they search. The second most important factor in housing is the square footage of the house.

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
