# MS-E-246-Project
## Variables
continuous:
- log(Gross approval)
- log(SBA guaranteed approval)
- Term in months
- Age of loan
- log(GSP) in the borrower state and year (from BEA)
- log(S&P500) on the loan approval date
- Unemployment rate in the borrower state and year (from BLS) 
- Unemployment rate in the project state and year (from BLS) 

1. add the differences: log(GSP) in the borrower state and year (from BEA), log(S&P500) on the loan approval date,  Unemployment rate in the borrower state and year (from BLS), Unemployment rate in the project state and year (from BLS) 
2. complex model: let the model choose the form of transformation; simple model: take log, etc. 

categorical:
- Business type (Corporation, Individual, Partnership) 
- 2-digit NAICS code
- Delivery method 
- Indicator: Term an integer multiple of a year 
- Indicator: Repeat borrower
- Indicator: Bank state 6= borrower state
- Indicator: Project state 6= borrower state 
- Approval fiscal year (from 1990 to 2014) 
- Borrower state 

## Pre-processsing
* partitioning: 70%train, 10% validation, 20% test
* normalization
* dummy: add 
* missing: add 


## Selecting variables/penalty
* ridge
* lasso
* elastic net
* bagging

## Model
* logistic regression
* hazard models 
* neural networks

## Prediction
* probability
* loss at default: simulation

## Measuring predictive performance
* In an out of sample
* ROC curve

## Explanation
* the fitting results
* the fitted model
* important variables

## Estimate loss 
* estimate the distribution of total loss on a portfolio of 500 randomly selected loans  over one and five year periods (state the loan selection method). Measure the risk in terms of the VaR and the Average VaR (also known as expected shortfall) at the 95% and 99% levels (include confidence bands for your estimates). 
* Finally, estimate the distributions for the one and five year losses of an investor who has bought a [5%,15%] tranche backed by the chosen portfolio. Also consider a [15%, 100%] senior tranche. Interpret and compare the distributions from a risk management perspective. 

### Piazza notes
1. macroecon variables: you can include both the amount and return
2. deep learning, LSTM model 
3. end of observation perioid: 
choose the end of observation date to be the last day of your data: compare with the latest charge-off day with the latest issue day of new loan, and take the later day as the last day of data.

For those very late loans which starts say only one year before the last day of your data I recommend just delete 

4. Preprocesssing:
centering and scaling continuous variables 

5. date should be transformed into a continuous duration variable. 
6. approval fiscal year: It could potentially be categorical but you need to make sure there won't be new categories in your test set that were not in you training set. 

### Paper
1. James, Witten, Hastie & Tibshirani (2013) 


