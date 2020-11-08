# Energy Consumption Modelling
An analysis and modelling of data provided from **Individual household electric power consumption Data Set**.

## Data Description
The data used in this notebook was sourced from [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets.php). Name of dataset is **Appliances energy prediction Data Set**. Link: https://archive.ics.uci.edu/ml/datasets/Appliances+energy+prediction .
The data is targetted on predicting power consumption of a household given atmospheric conditions such as temprature and atmospheric pressure at certain places around the house and date and time. Electric consumption of light fixtures is also provided as a feature in dataset.

## Data Cleaning and Preparation
Data is fairly clean. No missing values.Some outliers were observed for which standard scaling was done before modeling.

## Feature Engineering
Some new features were created based on date and time of record. Day of week, hour of day, month were important features that we engineered from data and time which later helped in drawing insights from data.

## Exploratory Data Analysis
Upon checking correlation of all features with total energy consumption, other than consumption of light appliances, tempratures at particular position inside house, outside temprature, windspeed and hour of the day had highest correlation. Outside atmospheric pressure and atmospheric pressure inside at certain places had high negative correlation with energy consumption.
Downward trend was shown in energy consumption as recordings moved from January to May depicting increase in temprature and hence lesser consumption of electricity by heaters and radiators.
Sunday experienced highest energy consumption and monday the least. Practical cause may be presence of family members in the house. Evening hours before 9 p.m showed highest energy consumption.

## Scaling
Standard scaling was done because of outliers were observed in energy consumption readings of light and total electric appliances both.

## Modelling.
Multiple regression models were created to check and compare there performances. Following modelling techniques were used:
* Linear Regression
* Support Vector Regressor
* Decision Tree Regressor
* Random Forest Regressor
* AdaBoost Regressor
* Gradient Boosting Regressor

At the end after comparing performances of above mentioned regressors, we tried to create a neural network based model to see if neural networks are able to capture all information and draw better predictions.

### Hyperparameter Tuning
GridSearchCV was used to tune hyperparameters of all models except linear regression model.

### Metrics
All models were evaluated on R<sup>2</sup> score. Training and testing score were compared to check for overfitting models. We tried with root-mean-square error but for R<sup>2</sup> better when comparing results of GridSearch.

## Final Results
Gradient Boosting model was able to give best result without overfitting. Whereas AdaBoost model overfitted the most. Attached notebook contains performance comparison of all models.

#### Performance note on neural networks
We developed a simple neural and fairly shallow neural network with only 3 deep layers between input and output layers. Initially it showed overfitting which I try to control by adding dropout between fully connected layers. It was able to control overfitting only slightly. But performance was not matched with GradientBoosting or Random Forest.