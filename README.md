# Assignment-17.1

The goal in this assignment is to compare the performance of the classifiers (k-nearest neighbors, logistic regression, decision trees, and support vector machines).

## Step 1: Business Understanding: 

Problem Statement: Accurately classify potential customers into those with high propensity to subscribe to a term deposit so that sales/ telemarketers can target the right group of customers to contact.

Measure of Effective:  Here, the accuracy score is used to score the performance of the classification models.  Two measures of performance were also included, i.e. the fitting time of the model and the percentage of customers to call (predicted == “Yes”) should not exceed the percentage called in the previous campaign = 18%.  This latter metric is added so that the number of customers to call is manageable otherwise it would be costly to the banks to employ too many telemarketers.   

## Step 2: Data Understanding

Split the data into sales call made within 3 months and those that didnt
