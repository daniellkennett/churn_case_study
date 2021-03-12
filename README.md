
# churn_case_study

# Data Cleansing

## Missing Values:
The dataset was missing data from 3 columns ('avg_rating_by_driver','avg_rating_of_driver', and 'phone'). Rather than drop these columns, we imputed the values in 2 ways. The first method was using SimpleImputer that calculates the mean value for the column and replaces the missing values with the mean. This was used for the rating columns. The second method used was the KNNImputer which used the 5 nearest neighbor (k=5) to determine the value. This was used for the phone column. 

## Removing Data Leakage from the dataset
We realized after running a logistic regression that the last_trip_date column was causing data leakage since it was a transformation of our dependent variable/target value. We also dropped the signup date column since all the signups happened in the same month and therefore thought this column had no signficant value.

# Michael
|Model Name|Hyperparameters|Score (mean accuracy on Test data)|notes|
|----------|---------------|-----|----|
| Gradient Boost Classifier|estimators=100, learning_rate=1.0, max_depth=3, min_samples_split=2| .7878|total default "hot garbage"|
| Gradient Boost Classifer|estimators=100, learning_rate=.1, max_depth=3, min_samples_split=2| .7898| tweaking down learning rate|
| Gradient BOost Classifier|estimators=200, learning_rate=.1, max_depth=6, min_samples_split=4|.7947|staged_predict, grid_search, hyperparameter tuning|
|         |               |      |
|         |               |      |
|         |               |      |
|         |               |      |
|         |               |      |


# Daniel
|Model Name|Hyperparameters|Score (mean accuracy on Test data)|
|----------|---------------|-----|
| RandomForestClassifier|estimators=100| 0.7606|
| RandomForestClassifier|estimators=100| |
|         |               |      |
|         |               |      |
|         |               |      |
|         |               |      |
|         |               |      |
|         |               |      |


