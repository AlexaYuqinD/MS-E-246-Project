# MS&E 246-Final Project

## 1. Introduction

In order to better understand the factors that affect loan charge-off rate and its
potential influence on investors, we design and implement a model of small-business
loan charge-off based on a data set of roughly 150,000 equipment loans backed by the
US Small Business Administration between 1990 and 2014. 

## 2. Exploratory Data Analysis
### Missing Data
<img src="https://github.com/AlexaYuqinD/MS-E-246-Project/blob/master/images/missing.png" 
 width="400" height="290" />
### Geographical Distribution
Percentage of defaulted loans by borrower state

<img src="https://github.com/AlexaYuqinD/MS-E-246-Project/blob/master/images/geo1.png" 
title="Percentage of defaulted loans by borrower state" width="500" height="300" />

Percentage of defaulted loans by CDC state

<img src="https://github.com/AlexaYuqinD/MS-E-246-Project/blob/master/images/geo2.png" 
title="Percentage of defaulted loans by CDC state" width="500" height="300" />

### Distribution of Gross Approval
<img src="https://github.com/AlexaYuqinD/MS-E-246-Project/blob/master/images/gross_approval.png" 
 width="400" height="250" />
<img src="https://github.com/AlexaYuqinD/MS-E-246-Project/blob/master/images/log_gross.png" 
 width="400" height="250" />

### Feature Correlation
<img src="https://github.com/AlexaYuqinD/MS-E-246-Project/blob/master/images/corr.png" 
 width="500" height="400" />

## 3. Data Preprocessing
Including dropping data, handling missing values, adding features, data transformation, oversampling (RandomOversampler & SMOTE), and train-dev-test split.

## 4. Classification: Modeling Default Probability
<img src="https://github.com/AlexaYuqinD/MS-E-246-Project/blob/master/images/roc.png" 
 width="500" height="370" />


  Feature Importance of LightGBM Classifier

  <img src="https://github.com/AlexaYuqinD/MS-E-246-Project/blob/master/images/feature_class.png" 
 width="450" height="320" />

  Best hyperparameters of DNN picked by random search


  <img src="https://github.com/AlexaYuqinD/MS-E-246-Project/blob/master/images/hyper.PNG" 
 width="300" height="220" />