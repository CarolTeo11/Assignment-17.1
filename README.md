# Assignment-17.1

The goal in this assignment is to compare the performance of the classifiers (k-nearest neighbors, logistic regression, decision trees, and support vector machines).

## Step 1: Business Understanding: 

Problem Statement: Accurately classify potential customers into those with high propensity to subscribe to a term deposit so that sales/ telemarketers can target the right group of customers to contact.

Measure of Effective:  Here, the accuracy score is used to score the performance of the classification models.  Two measures of performance were also included, i.e. the fitting time of the model and the percentage of customers to call (predicted == “Yes”) should not exceed the percentage called in the previous campaign = 18%.  This latter metric is added so that the number of customers to call is manageable otherwise it would be costly to the banks to employ too many telemarketers.   

## Step 2: Data Understanding

It was expected that client data, business data, outcome of previous campaign data (if contacted by sales personnel) and if the client subscribed to the term deposit was important.  Hence, the bank data set was acquired and used and this data can be found in https://archive.ics.uci.edu/dataset/222/bank+marketing.

The data set is created by: Paulo Cortez (Univ. Minho) and Sérgio Moro (ISCTE-IUL) @ 2012.  Please refer to the data fields and citation below:

### Bank Client Data

   1 - age (numeric)

   2 - job : type of job (categorical: "admin.","unknown","unemployed","management","housemaid","entrepreneur","student",
                                       "blue-collar","self-employed","retired","technician","services") 
   
   3 - marital : marital status (categorical: "married","divorced","single"; note: "divorced" means divorced or widowed)
   
   4 - education (categorical: "unknown","secondary","primary","tertiary")
   
   5 - default: has credit in default? (binary: "yes","no")
   
   6 - balance: average yearly balance, in euros (numeric) 
   
   7 - housing: has housing loan? (binary: "yes","no")
   
   8 - loan: has personal loan? (binary: "yes","no")
   
### related with the last contact of the current campaign:
   9 - contact: contact communication type (categorical: "unknown","telephone","cellular") 
  
  10 - day: last contact day of the month (numeric)
  
  11 - month: last contact month of year (categorical: "jan", "feb", "mar", ..., "nov", "dec")
  
  12 - duration: last contact duration, in seconds (numeric)
  
### other attributes:
  
  13 - campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)
  
  14 - pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric, -1 means client was not previously contacted)
  
  15 - previous: number of contacts performed before this campaign and for this client (numeric)
  
  16 - poutcome: outcome of the previous marketing campaign (categorical: "unknown","other","failure","success")

### Output variable (desired target):
  
  17 - y - has the client subscribed a term deposit? (binary: "yes","no")

Citation Request for use of data:
[Moro et al., 2011] S. Moro, R. Laureano and P. Cortez. Using Data Mining for Bank Direct Marketing: An Application of the CRISP-DM Methodology. 
In P. Novais et al. (Eds.), Proceedings of the European Simulation and Modelling Conference - ESM'2011, pp. 117-121, Guimarães, Portugal, October, 2011. EUROSIS.
Available at: [pdf] http://hdl.handle.net/1822/14838
                [bib] http://www3.dsi.uminho.pt/pcortez/bib/2011-esm-1.txt

