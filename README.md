# JOB-A-THON---April-2022

# Problem Statement
ABC is a car rental company based out of Bangalore. It rents cars for both in and out stations at affordable prices. The users can rent different types of cars like Sedans, Hatchbacks, SUVs and MUVs, Minivans and so on.

In recent times, the demand for cars is on the rise. As a result, the company would like to tackle the problem of supply and demand. The ultimate goal of the company is to strike the balance between the supply and demand inorder to meet the user expectations. The company has collected the details of each rental. Based on the past data, the company would like to forecast the demand of car rentals on an hourly basis.

# Objective
The main objective of the problem is to develop the machine learning approach to forecast the demand of car rentals on an hourly basis.

# Approach
The data given had no features except date and hour. So, I had to generate extra features from date and hour columns by feature engineering. And comparing the graph of hour and car demand according to that I noticed that in the afternoon time there is more demand of rental cars than other hours. After that I applies cosine and sine transformation for cyclical features like hour, month and day_of_week. Then I calculated Variance Inflation factor using statsmodels library and found that year and is_quarter_date are the ones with most collinearity. So, I removed them. And by the way if I'm predicting for next year then previous year won't matter so I removed these 2 features and once again I checked Variance Inflation factor and every other features score was lower thatn 5. So I scaled and splitted the other features.

# ML Approach
Basic time related features such as month, day, day_of_week, is_weekend, Time_of_day(Early Morning, Morning, Afternoon, Evening, Night, Late Night) and Seasons from month column(Spring, Summer, Autumn, Winter) were created. For cyclical features like hour, month and dayofweek I applies cosine and sine transformation. Then for categorical features I applied one hot encoder and that's it.

##### One thing I did in this model that is I created a value using the count, mean and standard deviation of the target feature and created a higher value and subtracted from target feature. After that target feature has all negative values. And somehow when i train test splitted the data and trained some model and compared with the normal target feature, I got great result using this method. And yes I applied log transformation, cos transformation and scaled the target feature but didn't get any good result than this idea.

I used Ridge, MLP Regressor, random forest, catboost, xgboost, linear regression and lgbmregressor. But Light Gradient Boosting Machine regressor(LGBMRegressor) gave good accuracy as well as less rmse. So I fall towards this light gradient boosting model. And I got the rmse of 33.07 and r^2 score of 35.44. It's better than all the other models. 

The same preprocessing, feature engineering I did for train set I did for test and then using LGBM regressor model I predicted the demand for car rental and then added with the number which I created before and subtracted from the target feature to get the actual / final predicted values.

## Final Result

Private Leaderboard Rank - 3

Public Leaderboard Rank - 54
