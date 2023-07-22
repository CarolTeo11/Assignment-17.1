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

## Step 3: Data Preparation 

First, I digitised and transformed the non-numeric columns to numeric ones.  For fields with “yes” and “no” option, I replaced them with 1 and 0 respectively.  For the other fields such as “marital” and “job” data, they were digitised using LabelEncoder.  

![image](https://github.com/CarolTeo11/Assignment-17.1/assets/130137674/0f322a81-7dcf-47ab-a142-0910c601298e)

Since the fields ‘day’ and ‘month’ were already featured in ‘pdays’, they were not included as features.  All the numerical fields and ‘y’ were also dropped to form the dataframe for X.  The data was then divided into training set and development sets in the ratio of 70-30. 

![image](https://github.com/CarolTeo11/Assignment-17.1/assets/130137674/9f85be7b-6712-4f96-b493-4b647c5d381b)

## Step 4: Modelling

### Statistical Analysis - Understanding the data.

First, I split the data into 2 groups, one containing customers who were previously contacted; the other containing customers who weren’t. It was observed that 18% of the customers were contacted in the previous campaign.  

![image](https://github.com/CarolTeo11/Assignment-17.1/assets/130137674/cc03dd61-9e1d-482b-9a71-b885f2aeb1b2)

Based on the results, customers who were contacted during the previous campaign had a much higher chance of subscribing to the term deposit.  Hence, it was important that efforts be targeted at customers who have high probability of signing up for the term deposit.  

![image](https://github.com/CarolTeo11/Assignment-17.1/assets/130137674/99646438-645b-4935-bf01-8609c3433ab9)

I also looked at the count of customers in each group and it was clear that it is not possible to contact all customers and hence, there is a need to target the effort at only potential customers.  

![image](https://github.com/CarolTeo11/Assignment-17.1/assets/130137674/e8bbfc88-1b4f-47e7-9aaf-f76c0f14e823)

Since this is a classical classification problem, 4 different models were used, namely logistic regression, decision tree, k nearest neighbors and support vector machine.  

![image](https://github.com/CarolTeo11/Assignment-17.1/assets/130137674/41db2bee-1a8b-41bb-8639-4074c2e2de93)

## Step 5: Evaluation 

### Original Model: Using the full data set 

The accuracy scores for the training and development sets, fitting time and were recorded.

![image](https://github.com/CarolTeo11/Assignment-17.1/assets/130137674/43f4908d-02d3-49a4-afa4-80e12eead442)

From the above, logistic regression recorded the best accuracy score for the development set, followed by the SVM, KNN and Decision Tree.  However, the KNN took the shortest time to fit the model, followed by the Decision Tree, Logistic Regression and SVM.  Since the fitting times were all tolerable and the accuracy score was the measure of effectiveness, the Logistic Regression Model appears to be the best model.  In addition, the workload for the Logistic Regression was 3.5% which is way lower than the original 18%.  The confusion matrix of the 4 models is shown below:

![image](https://github.com/CarolTeo11/Assignment-17.1/assets/130137674/f4cfe938-4d5a-4948-91c8-4917897df7e2)

### Sensitivity analysis: Analysing without data from customer who were not contacted and did not subscribe to the term deposit.  

As it was hard to tell if the group of customers who were not contacted and did not subscribe to the term deposit were indeed not interested in the term deposit or was simply unaware of the campaign, I decided to rerun the model without the group of customers who were not contacted and did not subscribe to the term deposit.   To re-use the code, I filtered the data to the sample set that I wanted and re-run the model.  The results are shown below.  

![image](https://github.com/CarolTeo11/Assignment-17.1/assets/130137674/6e3658d8-57c1-4a23-ad12-2bc73d4d52a9)

Here, the Logistic Regression continues to be the best model based on its test score.  However, the Logistic Regression has the highest fitting time and the workload was high at 45%.  It must be noted that the workload ended up higher as the percentage of success was way higher in this sample set.  

## Step 6: Deployment

Since the accuracy of the model was no better off in the sensitivity study but the workload becomes significantly higher, it was better to deploy the original Logistic Regression model for 2 reasons.  First, test score was slightly better and next, the workload was significantly lower for the original model.  

Next Steps and recommendations:

a.	It is recommended that Logistic Regression model be deployed for the next campaign and new data be collated to further refine the model

b.	Even though this is a classification model, a time series model can be deployed if there is sufficient data collated over a few campaign

c.	External data such as economic data can be collated to enrich the analysis as state of the economy can have an impact on people’s propensity to take up term deposit.  

