# New-York-Taxi-Fare-Prediction
## Description
This project is about predicting the average fare of a taxi in New York City.This is a supervised regression problem as we are predicting the amount that needs to be spend on a taxi ride per hour.

## Problems fixed
Data contains some outliers and negative values as shown in the figure below
![Graph with all the data](/images/total_values_graph.png)

Removed the negative and zero values because they might affect the model and also outliers because the fare values are very high which is abnormal.
![Graph without outliers and negative values](/images/values_graph_without_outliers_and_negative)


## Feature Engineering
New columns have been extracted from the existing data like transaction_day, transaction_month etc. Added some external features like holidays and weekends from a calendar module, New York city weather data and borough information.

You can find the taxi data used in this project ![here]([https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page,file:///D:/New-York-Taxi-Price-Prediction/Data/data_dictionary_trip_records_yellow.pdf]) and information about the features ![here](file:///D:/New-York-Taxi-Price-Prediction/Data/data_dictionary_trip_records_yellow.pdf) 

## Algortithms used
Used Decision Tree Regressor as a benchmark model. Benchmark model is the model that is used on the available data without any feature engineering to see if the model predicts the target without any overfitting or underfitting. 
After feature engineering, again Decision Tree is used along with Random Forest and Gradient Boosting algorithms.

Performances of the models before tuning:
| Algorithm         |  MAE  |  RMSE  |   R2   |
|-------------------|:-----:|:------:|:------:|
| Benchmark model   | 9.024 | 14.121 | 0.373 |
| Decision tree     | 8.379 | 13.345 | 0.334 |
| Random forest     | 8.211 | 12.952 | 0.373 |
| Gradient boosting | 8.315 | 12.721 | 0.395 |

## Tuning
Random forest model is selected for performing hyperparameter tuning. Found out the values of the parameters that give the best performance possible with less computation time and used those values in the model.

Performance comparision after tuning:
| Algorithm           |  MAE  |  RMSE  |   R2   |
|---------------------|:-----:|:------:|:------:|
| Benchmark model     | 9.024 | 14.121 | 0.373 |
| Decision tree       | 8.379 | 13.345 | 0.334 |
| Random forest       | 8.211 | 12.952 | 0.373 |
| Gradient boosting   | 8.315 | 12.721 | 0.395 |
| Tuned Random forest | 7.156 | 11.871 | 0.473 |

True vs Predicted values graph for the tuned random forest model:
![true vs predicted values graph](/images/tuned_random_forest.png)
*x-axis represents the true values and y-axis represents the predicted values*
