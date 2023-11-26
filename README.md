# Detecting the next data breach

## Problem Statement
The dataset df_1.csv is a mostly numeric, tabular dataset which contains over 351 company data breach data totaling 30,000 records.
There are 7 columns: Entity, year, records, organization type, method, sources, and id.

The goal of the project is to leverage the dataset and develop an ML algorithm that can analyze the data and identify how the next data breach will occur. This will be particularly useful to companies that are looking to prevent data breaches from occurring in the future.

The scenario can be considered as a regression or classification problem.

Regression: Predicting the scale of the breach based on the organization type and method of breach.
Classification: Predicting the method of breach based on the organization type and scale of the breach.

## Overview of the approach
1. Data cleaning and preprocessing
2. Exploratory data analysis
3. Feature engineering
4. Model building
5. Model evaluation

## Overview of the dataset
Entity: Name of the company that was breached. This could be useful in future iterations of the project to identify if there are any patterns in the names of the companies that are breached. (NLP)
Year: Year in which the breach occurred. Some entries are non-numeric.
Records: Number of records that were breached. Some entries are non-numeric.
Organization type: Type of organization that was breached. This is a categorical variable. Some entries are similar but have different names.
Method: Method of breach. This is a categorical variable. Some entries are similar but have different names.
Sources: Hyperlinked sources to the articles that were used to collect the data.

## Data cleaning and preprocessing
The Years column had some ill formatted entries. For example, some entries had the year as 2004-05, 2004-06, etc. In these cases, the rows were duplicated for each year in the range, and the number of records split evenly between the years.

For the Records column, ill formatted entries were replaced with the mean of the organization type.

## Exploratory data analysis
The dataset is not fully representative of real world data breaches – for example, looking at the healthcare industry alone, there are years where no entries were lost. Cursory research shows that this is not the case. This could be due to the fact that the dataset is not fully representative of all data breaches that have occurred in the past 15 years. It is also worth noting that the range of entries in the dataset are between 2004 and 2019, so more recent data breaches are not included.

## Feature engineering
The categorical variables were one-hot encoded. The numerical variables were scaled using the StandardScaler.

## Model building
The features consist of the encoded categorical variables and the scaled numerical variables. The target variable is the method of the breach. The neural network consists of linear layers with activation functions. The MSE was used as the loss function, and the Adam optimizer is used to update the model's weights during training. The model was trained for 20 epochs, and cross validation was used to tune the model on different subsets of the data.

## Model evaluation
Classification – predicting the method of the data breach: The model performs relatively well with a 82.61% accuracy score. 
Regression - predicting the scale of the breach: The model performs relatively well with a 0.89 MSE