
# churn_case_study

# Data Cleansing

## Missing Values:
The dataset was missing data from 3 columns ('avg_rating_by_driver','avg_rating_of_driver', and 'phone'). Rather than drop these columns, we imputed the values in 2 ways. The first method was using SimpleImputer that calculates the mean value for the column and replaces the missing values with the mean. This was used for the rating columns. The second method used was the KNNImputer which used the 5 nearest neighbor (k=5) to determine the value. This was used for the phone column. 

## Removing Data Leakage from the dataset
We realized after running a logistic regression that the last_trip_date column was causing data leakage since it was a transformation of our dependent variable/target value. We also dropped the signup date column since all the signups happened in the same month and therefore thought this column had no signficant value.

# Michael / James 
|Model Name|Hyperparameters|Score (mean accuracy on Test data)|notes|
|----------|---------------|-----|----|
| Gradient Boost Classifier|estimators=100, learning_rate=1.0, max_depth=3, min_samples_split=2| .7878|total default "hot garbage"|
| Gradient Boost Classifer|estimators=100, learning_rate=.1, max_depth=3, min_samples_split=2| .7898| tweaking down learning rate|
| Gradient Boost Classifier|estimators=200, learning_rate=.1, max_depth=6, min_samples_split=4|.7964|staged_predict, grid_search, hyperparameter tuning|


# Daniel
|Model Name|Hyperparameters|Score (mean accuracy on Test data)| notes|
|----------|---------------|-----|-----|
| RandomForestClassifier|estimators=100| 0.7606| first attempt with default hyperparameters |
| RandomForestClassifier|estimators=500, param_max_depth=8| 0.7875| bestmodel from gridsearch |


# charles
|Model Name|Hyperparameters|Score (mean accuracy on Test data)| notes|
|----------|---------------|-----|-----|
| || |  |
| || |  |

# How did you compute the target?
We computed the target by engineering a new binary feature "active" that takes the value of 1 if the rider did have a ride within the last 30 days, and 0 otherwise. 

# What model did you use in the end? Why? 
Ultimately, gradient boost with hyperparameter tuning achieved the best scores. 
    
# Alternative models you considered? Why are they not good enough?
We considered random forest and logistic models, however the logistic model does not account for 

# What performance metric did you use to evaluate the model? Why?
We decided on mean accuracy against Test data (typically the .score method of the models in sci kit learn). 

# Based on insights from the model, what plans do you propose to reduce churn?

# What are the potential impacts of implementing these plans or decisions? What performance metrics did you use to evaluate these decisions, why?





