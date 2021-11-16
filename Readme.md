# Predicting Red Hat Business Value
Red Hat has a large amount of data about the behavior of individuals over time. They wanted to use this data to predict which individual they should approach.

# Table of Contents
* [Overview](https://github.com/yash-meshram/kaggle/tree/main/predicting-red-hat-business-value#overview)
* [Data Description](https://github.com/yash-meshram/kaggle/blob/main/predicting-red-hat-business-value/Readme.md#data-description)
* [Approach](https://github.com/yash-meshram/kaggle/blob/main/predicting-red-hat-business-value/Readme.md#approach)
  * [Data Cleaning](https://github.com/yash-meshram/kaggle/blob/main/predicting-red-hat-business-value/Readme.md#data-cleaning)
  * [Feature Engineering](https://github.com/yash-meshram/kaggle/blob/main/predicting-red-hat-business-value/Readme.md#feature-engineering)
  * [Feature Selection](https://github.com/yash-meshram/kaggle/blob/main/predicting-red-hat-business-value/Readme.md#feature-selection)
  * [Traning Model](https://github.com/yash-meshram/kaggle/blob/main/predicting-red-hat-business-value/Readme.md#traning-model)

# Overview
* Predicted the potential business value of a person based on its characteristics and activities.
* Done Data Cleaning, Feature Engineering, and Feature Selection
* Build the Machine Learning model (Random Forest Classifier) for predicting the business value

# Data Description
Data Source: [Kaggle](https://www.kaggle.com/c/predicting-red-hat-business-value/data)

The dataset contains 3 files:

| File Name      | Contains      |  Description of file                                                                                     |
| -----------    | -----------   | -----------                                                                                             |
| act_train.zip  | act_train.csv | Contains all the activities that each person had performed, characteristic of these activities, and the outcome (whether or not the company approach them or not)|
| act_test.zip   | act_test.csv  | Contains all the activities that each person had performed and characteristics of these activities       | 
| people.zip     | people.csv    | Contains all the unique people who have performed activities and their characteristics |

# Approach

## Data Cleaning
* Covert the string elements to int or float elements
* Change the formate of dates

## Feature Engineering
In act_train.csv, we have a column named "date" which gives the date on which the person does an activity. There is also a column labeled "date" in the people.csv file which gives you the date at which people characteristics is been noted. When we merge these two files we have columns named "date_x" (representing date column from act_train.csv file) and "date_y" (representing date column from people.csv file). Both of these features can be useful for our prediction. Thus we will introduce a new feature "date" which will be the difference of date_x and date_y.\
\
date = date_x - date_y

## Feature Selection
Lets have a look in training datset. Here we can observe that almost 92% of the elements in columns (from char_1 to char_9) are non-null. Thus we can eliminate these features.
![image](https://user-images.githubusercontent.com/64315038/141825289-6ed55df4-17b7-4f00-bdc9-7bf3b1f9fbe6.png)

## Traning Model
Build **RandomForestClassifier** model to predict the outcome

## Evaluation
The model had been evaluated using **AUC Metric**. Got an accuracy of 99%
