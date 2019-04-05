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

### Distribution of Gross Approval Before and After Log Transformation
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


  Best hyperparameters of DNN picked by random search


  <img src="https://github.com/AlexaYuqinD/MS-E-246-Project/blob/master/images/hyper.PNG" 
 width="300" height="180" />



  Feature importance of LightGBM Classifier

  <img src="https://github.com/AlexaYuqinD/MS-E-246-Project/blob/master/images/feature_class.png" 
 width="450" height="340" />

## 5. Regression: Modeling Loss at Default

  Performance of all regression models on test set

  <img src="https://github.com/AlexaYuqinD/MS-E-246-Project/blob/master/images/allreg.PNG" 
 width="530" height="270" />

  Feature importance of LightGBM Regressor

   <img src="https://github.com/AlexaYuqinD/MS-E-246-Project/blob/master/images/feature_reg.png" 
 width="430" height="320" />

## 6. Portfolio Simulation

### Generating Samples
To formulate the portfolio, we set a date 2006-02-15 as the start of our observation
period and randomly select 500 loans from the test set that had not defaulted or paid
in full before that date.

### Loan Simulation
Note: Distribution over 500 loans

   <img src="https://github.com/AlexaYuqinD/MS-E-246-Project/blob/master/images/loansim1.png" 
 width="390" height="250" />
 <img src="https://github.com/AlexaYuqinD/MS-E-246-Project/blob/master/images/loansim5.png" 
 width="390" height="250" />

### Portfolio Simulation
Note: Distribution over 1000 simulations

   <img src="https://github.com/AlexaYuqinD/MS-E-246-Project/blob/master/images/portsim1.png" 
 width="390" height="250" />
 <img src="https://github.com/AlexaYuqinD/MS-E-246-Project/blob/master/images/portsim5.png" 
 width="390" height="250" />

  VaR and Average VaR of portfolio loss

   <img src="https://github.com/AlexaYuqinD/MS-E-246-Project/blob/master/images/var.PNG" 
 width="350" height="100" />

### Tranche Simulation
   <img src="https://github.com/AlexaYuqinD/MS-E-246-Project/blob/master/images/tranche11.png" 
 width="390" height="250" />
 <img src="https://github.com/AlexaYuqinD/MS-E-246-Project/blob/master/images/tranche15.png" 
 width="390" height="250" />

   <img src="https://github.com/AlexaYuqinD/MS-E-246-Project/blob/master/images/tranche21.png" 
 width="390" height="250" />
 <img src="https://github.com/AlexaYuqinD/MS-E-246-Project/blob/master/images/tranche25.png" 
 width="390" height="250" />


