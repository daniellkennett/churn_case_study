
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



![GitHub Logo](https://github.com/daniellkennett/churn_case_study/blob/main/images/Michael/gridsearch_heatmap.png?raw=true)





# Daniel
|Model Name|Hyperparameters|Score (mean accuracy on Test data)| notes|
|----------|---------------|-----|-----|
| RandomForestClassifier|estimators=100| 0.7606| first attempt with default hyperparameters |
| RandomForestClassifier|estimators=500, param_max_depth=8| 0.7875| bestmodel from gridsearch |


# Charles
|Model Name|Hyperparameters|Score (mean accuracy on Test data)| notes|
|----------|---------------|-----|-----|
| LogisticClassifier|iter= 100,000| 0.7256| loses accuracy if the model cycles through too many iterations |

# How did you compute the target?
We computed the target by engineering a new binary feature "active" that takes the value of 1 if the rider had a ride within the last 30 days, and 0 otherwise. 

### TLDR;

1: active user

0: churned user

# What model did you use in the end? Why? 
Gradient boosting, radom forest and logistical regression were all tested.
Ultimately, gradient boost with hyperparameter tuning achieved the best scores. 


# What performance metric did you use to evaluate the model? Why?
We decided on mean accuracy against Test data (typically the .score method of the models in sci kit learn). 

# Based on insights from the model, what plans do you propose to reduce churn?

![GitHub Logo](https://github.com/daniellkennett/churn_case_study/blob/main/images/Michael/gdbc_feature_importance.png?raw=true)


![GitHub Logo](https://github.com/daniellkennett/churn_case_study/blob/main/images/Michael/gb_partial_dependence_plots.png?raw=true)

1. The company should reevaluate their advertisement budget in King’s Landing, Astapor, Winterfell. For example, if the company equally distributes the budget among all three, they are getting more activity from city one, so it may be more in the interest of the company to focus their spending more. 

2. When customers are getting hit by surge pricing, they trend towards churning. Reduce surge price rates. 

3. Based on the partial dependence plot for the phone feature, we recommend the mobile team work on ensuring the same customer experience between iPhone and Android platform. We are seeing a slightly downward trending slope between Android and iPhone customers which implies iPhone customers were more likely to churn given all else equal.
# What are the potential impacts of implementing these plans or decisions? What performance metrics did you use to evaluate these decisions, why?





