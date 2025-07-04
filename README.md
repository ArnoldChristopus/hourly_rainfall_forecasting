# Hourly Rainfall Forecasting Using Hybrid LSTM Model
## Overview
This project applies a hybrid LSTM-based machine learning model to predict hourly rainfall. It combines classification and regression tasks into a multitask learning framework.
The classification head predicts whether it rains or not, and if it rains, the regression head predicts how much.

## Data
Hourly rainfall data is collected from https://sdatelemetry.com/newfms/datach.php using webscraping.

## Model
A hybrid LSTM model with a binary classifier predicting rain occurence and a regressor predicting rainfall amount.
Rainfall data is inherently dominated by 0, regular regression model fails to differentiate between dry and rainy event and tends to predict a consistent pattern without taking dry periods into consideration. Adding a classification head enhances the model performance due to classification task being easier than regression task. With the addition of classification, the regression head only predicting how much it rains if the classification head predicts there is rain.
Weighted loss functions are applied to address the class imbalance. Specifically, the classification loss is weighted to address the class imbalance by amplifying the loss during rainy events. Meanwhile, the regression loss is weighted to prioritize extreme values by amplifying the loss based on rainfall intensity (bigger rainfall has bigger weight).
Hyperparameter tuning is performed using Optuna library.

## Dependencies
1. PyTorch -> machine learning model
2. Numpy, Pandas, Matplotlib -> data processing and visualization
3. Scikit-learn -> metrics calculation
4. Optuna -> hyperparameter tuning
