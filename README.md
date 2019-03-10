# MS-E-246-Project
## Tasks to do before Weekend:
1. Preprocessing 
- difference: add difference of: gsp, s&p 500, unemploy_borr, unemploy_proj
- Total loan amount
- date: continuous

2. VaR: 课件, piazza

3. plot: map

4. 画PPT

5. DNN: 1)loan age; 2)drop loans which start late
   - choose the end of observation date to be the last day of your data: compare with the latest charge-off day with the latest issue day of new loan, and take the later day as the last day of data.
   - For those very late loans which starts say only one year before the last day of your data I recommend just delete 
   
4. bagging
   - random forest
   
5. RNN-LSTM

6. ? date should be transformed into a continuous duration variable. 




## Data Exploration&Visualization
- explore the data set: maybe some plots?


## Variables
complex model(DNN etc.): let the model choose the form of transformation; simple model: take log, etc.

1. continuous: (5)
- ThirdPartyDollars
- GrossApproval: Total loan amount (need to add log)
- InitialInterestRate: Initial interest rate - total interest rate (base rate plus spread) at time loan was approved
- TermInMonths: Length of loan term
- GrossChargeOffAmount

Things to add/change: 
- log(Gross approval)
- log(GSP) in the borrower state and year (from BEA)
- log(S&P500) on the loan approval date
- Unemployment rate in the borrower state and year (from BLS) 
- Unemployment rate in the project state and year (from BLS) 
- difference: add difference of the last 4

- ？Age of loan


2. categorical: (24)
- Program: whether loan was approved under 7a/504 loan program
- BorrName: Name of borrower
- BorrStreet: Borrower street address
- BorrCity: Borrower city
- BorrState: Borrower state
- BorrZip: Borrower zip code
- CDC_Name: name of CDC
- CDC_Street: CDC street address
- CDC_City: CDC city
- CDC_State: CDC state
- CDC_Zip: CDC zip code
- ThirdPartyLender_Name
- ThirdPartyLender_City
- ThirdPartyLender_State
- ApprovalDate: Date the loan was approved
- ApprovalFiscalYear: Fiscal year the loan was approved
- DeliveryMethod: Specific delivery method loan was approved under
- subpgmdesc: Subprogram description - specific subprogram loan was approved under
- NaicsCode: North American Industry Classification System (NAICS) code (specifying industry)
- NaicsDescription: NAICS description
- ProjectCounty: County where project occurs
- ProjectState: State where project occurs
- BusinessType: Borrower Business Type - Individual, Partnership, or Corporation
- ChargeOffDate: Total loan balance charged off (includes guaranteed and non-guaranteed portion of loan)

Things to add/change: 
- ？indicator: Term not an integer multiple of a year
- ？borrower state != CDC state
- ？borrower state != ThirdPartyLender_State
- ？borrower state != Project state


3. Outcome: (1)
- LoanStatus: Current status of loan



## Pre-processsing
* over-sampling: treat unbalanced data 
* add time-varying risk factors at the regional level: GSP, Unemployment Rate, S&P 500 
* partitioning: 70%train, 10% validation, 20% test
  - random partitioning
  - or: take the most recent observations as test cases
* normalization: normalize the continuous variables
* dummy: add 
* missing: encode missing values of explanatory variables by indicator variables
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
- select the penalty weight: AUC on validation set
Coefficient estimates are biased in the presence of penalty and missing value terms; standard errors could be found by bootstrapping

## Model
* logistic regression
* hazard models (model the timing of event, in influence of time-variation of X)
* neural networks

## Prediction
* probability
* loss at default: simulation

## Measuring predictive performance
* In an out of sample
* Confusion Matrix
* ROC curve, AUC(both training and test)

## Explanation
* the fitting results
* the fitted model
* important variables

## Estimate loss 
* build a model for the loss at default: E(l |Default, X), is the empirical mean of the realized loss given default
* estimate the distribution of total loss on a portfolio of 500 randomly selected loans over one and five year periods (state the loan selection method). Measure the risk in terms of the VaR and the Average VaR (also known as expected shortfall) at the 95% and 99% levels (include confidence bands for your estimates). 
* Finally, estimate the distributions for the one and five year losses of an investor who has bought a [5%,15%] tranche backed by the chosen portfolio. Also consider a [15%, 100%] senior tranche. Interpret and compare the distributions from a risk management perspective. 

## Results
* Write up a final report, detailing your models, statistical estimation approaches, tests, and results to the extent that the results could be replicated.
* Presentation: PPT

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
1. Intro to classification problem: James, Witten, Hastie & Tibshirani (2013) 


