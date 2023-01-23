# Predicting-Property-Maintenance-Fines-in-Detroit
Final project of Applied Machine Learning in Python in Coursera. More compelete and detailed info about the prject can be found on: 
https://joseanmarsol.com/portfolio/predicting-property-maintenance-fines-in-detroit/

## Intro and scope
The project consists of supporting the City of Detroit to help solve one of the most pressing problems facing Detroit – blight violations. 
Blight violations are issued by the city to individuals who allow their properties to remain in a deteriorated condition. 
Every year, the city of Detroit issues millions of dollars in fines to residents and every year, many of these fines remain unpaid. 
Enforcing unpaid blight fines is a costly and tedious process, so the city wants to know: how can we increase blight ticket compliance?

The first step in answering this question is understanding when and why a resident might fail to comply with a blight ticket. 
This is where predictive modeling comes in. The task is to predict whether a given blight ticket will be paid on time. 

The complete project is done in Python.

## Data collection
We are provided two data files for use in training and validating the models: train.csv and test.csv. 
Each row in these two files corresponds to a single blight ticket, and includes information about when, why, and to whom each ticket was issued.

## Data reading and cleaning
The project starts by reading the train csv file. After that some cleaning is needed. First those features which won’t be available during the test are removed 
from the dataframe. Thanks to this we know that we can remove the violation_zip_code, non_us_str_code and grafitti_status because they are only filled with NaN.
After that we convert the NaN from the target value column which we need to predict, the compliance. 
Compliance, as well as a handful of other variables that will not be available at test-time, are only included in train.csv.

## Machine Learning model
Using a Random Forest algorithm to predict. First we check the correlation between all the columns and the compliance target column.
Then we split the dataset, assigning X to the features column and y to the target column. 
The function train_test_split is used to divide both X and y into train and test. 
As explained at the beginning of the project explanation, a random forest model uses two main parameters: number of estimators (n_estimators) and maximum depth (max_depth). 
We will use GridSearchCV to obtain the best parameters for a random forest classifier, taking he roc_auc as scoring metric.
