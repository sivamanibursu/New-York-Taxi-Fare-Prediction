# New York Taxi Fare Prediction
## Description
This project is about predicting the average fare of a taxi in New York city. This is a supervised regression problem as we are predicting the amount that needs to be spend on a taxi ride per hour.

## Problems fixed
Data contains some outliers and negative values as shown in the figure below.

![Graph with all the data](/images/total_values_graph.png)

Removed the negative and zero values because they might affect the model and also outliers because the fare values are very high which is abnormal.

![Graph without outliers and negative values](/images/values_graph_without_outliers_and_negative.png)

## Data Preprocessing and Benchmark Model
After removing Outliers, negative and zero values from the data, some of the features which I think would contribute in predicting the target feature have been selected as input features. The input features selected are PULocationID, transaction_month, transaction_day, transaction_hour, trip_distance where some of these are extracted from the transaction_date and total_amount is selected as the target feature as we are predicting the average fare of a taxi. Applied decision tree regressor on the data and found that it is overfitting through the metrics and the graph as shown in the figure below.

![True vs Predicted values of the overfitting model](/images/overfitting_benchmark.png)
*x-axis represents the true values and y-axis represents the predicted values*

This overfitting might be due to the trip_distance feature which is directly related to the transportation cost. So the trip_distance feature is removed from the input feature and used the decision tree regressor on the updated features which gives the result as shown in the table.
| Algorithm                  |  MAE  |  RMSE  |   R2   |
|----------------------------|:-----:|:------:|:------:|
| Overfitting Benchmark model| 4.949 | 9.392  | 0.722 |
| Benchmark model            | 9.024 | 14.121 | 0.373 |

Note: Here the Benchmark model is any desired machine learning model that is used before feature engineering.  

## Feature Engineering
New columns have been extracted from the existing data like transaction_week_day, transaction_weekend etc. Added some external features like holidays from a calendar module, New York city weather data and borough information. Only selected the boroughs Manhattan, Brooklyn, Queens, Bronx which are the major areas in which taxis are operating. Other locations with less taxi operations have been removed as they would affect the machine learning model. There are problems with the values and data types of the weather data which are fixed by replacing the values with accurate values and converting those to correct data types. Missing values in the weather data are fixed with interpolation, backward and forward filling techniques.

## Algorithms used
Used Decision Tree Regressor as a benchmark model. Benchmark model is the model that is applied on the available data without any feature engineering to see if the model predicts the target without any overfitting or underfitting. 
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

## Sources
The data used in this project is available here:
* [Taxi data](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
* [Information about the features](https://www.nyc.gov/assets/tlc/downloads/pdf/data_dictionary_trip_records_yellow.pdf)
