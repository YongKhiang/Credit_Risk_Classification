# Credit Risk Classification

## Problem Statement

The goal of this project is to explore a bank customers' dataset comprising demographic data and payment history to gain insights on the features which could accurately separate customers into high credit or low credit risk using machine learning classification techniques.

The performance of the different classifier models would be evaluated using the Receiver Operating Characteristic-Area Under Curve (ROC-AUC) metric which tells how good the classifier is in distinguishing between high and low credit risk customers, while preserving model generalizability.

## Executive Summary

Through the exploratory analysis, it was observed that the dataset is imbalanced, with high risk customers forming only 20% of the data. The customer's demographic features, namely `fea_2` and `fea_4` have some differences in the distribution between low risk and high risk customers. For `fea_2`, there is a bimodal distribution for high risk customers; for `fea_4`, the distribution of values is clustered at the lower end for high risk customers. With regards to the card payment history features, it can be seen that those high risk customers generally have higher overdue times and overdue days, lesser normal payment times, and higher current balance across various credit types which is not a surprise. In addition, high risk customers generally have a lower card payment history counts and mean credit limit, probably due to more stringent bank approvals for various credit products given their high risk attributes. 

Four different machine learning classification algorithms were evaluated. **Random Forest** model was chosen as it has a lower variance between train and test scores, and was able to achieve a high AUC score of 0.779 and respectable recall of 0.667 on the test set, at expense of lower precision (higher false positives).

From the feature importance scores, it can be seen that `prod limit_mean`, `fea_4`, `fea_2`, `new_balance_sum` and `history_count` are the top 5 important features for predicting the credit risk of a customer. 

## Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|id|int|customer_data/ payment_data|customer id|
|label|int|customer_data|whether or not the customer has high credit risk (1 = high; 0 = low)| 
|fea_1 to fea_11|int/ float|customer_data|customer’s demographic data and category attributes which have been encoded|
|OVD_t1|int|payment_data|number of times overdue type 1|
|OVD_t2|int|payment_data|number of times overdue type 2|
|OVD_t3|int|payment_data|number of times overdue type 3|
|OVD_sum|int|payment_data|total overdue days|
|pay_normal|int|payment_data|number of times normal payment|
|prod_code|int|payment_data|credit product code|
|prod_limit|float|payment_data|credit limit of product|
|update_date|datetime|payment_data|account update date|
|new_balance|float|payment_data|current balance of product|
|highest_balance|float|payment_data|highest balance in history|
|report_date|datetime|payment_data|date of recent payment|
