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
* add time-varying risk factors at the regional level: 
* partitioning: 70%train, 10% validation, 20% test
* normalization
* dummy: add 
* missing: add 
* add: Unemployment, GSP, Zip-housing price
* date: change to continuous
* add the difference: 
1. log(GSP) in the borrower state and year (from BEA)
2. log(S&P500) on the loan approval date
3. Unemployment rate in the borrower state and year (from BLS) 
4. Unemployment rate in the project state and year (from BLS) 

* total amount: gross approval + 3rd party dollars = total loan amount.
There are loans whose charge off amount is greater than the gross approval amount. In order to deal with that please read the quote from professor Giesecke:
"Here's a clarification regarding the meaning of the fields "Third Party Dollars" and "Gross Approval" in the data for the project.With 504 loans, there are two sources of funding. There is a CDC (Community Development Corporation) that sponsors the loan. The CDC the finds a bank to contribute funds to cover a portion of the loan. The CDC issues bonds to fund its lending, and these bonds are guaranteed by the SBA. So that is how the SBA guarantee works for the 504 program (fairly different in mechanism to how the guarantee works for the 7a program, which we discussed in class). Thus, the "third party dollars" and other terms relating to third party in the 504 program refer to how much money is contributed by the partner bank, and also then to how much of the loan value is not guaranteed by the SBA.

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
7. An investor who has bought a [5%, 15%] tranche: This designates the attachment points of a tranche: the investor starts being exposed to losses if they reach 5% of the total, and stops being exposed if they reach 15% of the total. 
- if x < 5%: nothing happens
- if 5% < x < 15%: then the mezzanine tranche will get a loss in excess of 5% which means a loss equal to x-5%
- if x > 15%: then the mezzanine tranche will get a loss of 10% (15% - 5%) and the senior tranche will get the remaining loss in excess of 15%, i.e x - 15%

8. when we are estimating the distribution of total loss on a portfolio of 500 randomly selected loan over one and five year periods, how are we defining the 1/5 year time horizon? 
When does the 1/5 year time horizon start and end? Do we apply the hazard model to our loss dataset and at 1 year, we say all the loans to the left of the 1 year cut off are the loans that have defaulted and calculate the loss? 
Answer: Here’s my crude understanding - please correct me if I’m wrong. Look at the last year of the dataset (end of sample period). Randomly select 500 of all loans still living then. Use hazard model to simulate default times. If time to default < 1 then tally the losses of those loans. Repeat for default times < 5. 

9. are you predicting loss of those loans through a regression model? if the loans are you selecting are still alive, the wouldn't have any gross charge off correct? 
Yes, you need to train a second model that would predict a loss amount or percentage given a defaulted loan.


### Paper
1. James, Witten, Hastie & Tibshirani (2013) 


