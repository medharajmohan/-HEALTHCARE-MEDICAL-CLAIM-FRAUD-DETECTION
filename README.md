# Healthcare-Medical-Claim-Fraud-Detection

To predict whether a provider is potentially fraudulent or the probability score of that provider’s fraudulent activity and also find the reasons behind it as well to prevent financial loss.

Recognize and identify fraudulent medical claims and study its pattern of occurrences by discovering important attributes of patient and beneficiary data.

Exploratory Data Analysis Results:

![image](https://user-images.githubusercontent.com/89947247/201002012-6d61100c-d1a7-4882-9621-c02b63126b55.png)

Observation:
1. Number of cases of non-fraudulent transactions is around 35000. 

2. Number of cases of fraudulent transactions is around 22000.
 
3. As this is the aggregated data for each transaction of a beneficiary, the number of fraudulent transactions are slightly higher than expected because the single healthcare provider is performing fraud with multiple beneficiaries.

![image](https://user-images.githubusercontent.com/89947247/201002082-6fd4e60c-1de8-4e23-b4ec-2c095d6088ac.png)

1. The number of providers who do not have a single case of fraud registered against them is approximately 5000.

2. The number of providers who have a case of fraud registered against them is approximately 500. 3. The ratio of non-fraudulent to fraudulent providers is around 10:1

![image](https://user-images.githubusercontent.com/89947247/201002180-1fb10c25-158c-440c-949f-a2e59413c2cd.png)

1. Number of male beneficiaries is around 32000. 

2. Number of female beneficiaries is around 24000.

![image](https://user-images.githubusercontent.com/89947247/201002245-c6e62ec0-5778-4287-adcb-14a35b225728.png)

1. As the critical age is between 60 to 100, this distribution is right tailed.

2. Average age of the beneficiaries is around 72 which makes sense because many chronic health problems are common at this age.

![image](https://user-images.githubusercontent.com/89947247/201002435-955e5398-5c2b-4f87-90f2-84b1be16d4f0.png)

1. Among the top 10 states, state 5 has the highest number of beneficiaries i.e 50000.

2. State 11 has around 18000 beneficiaries.

3. Chances of more fraudulent transactions increases where the number of people who are seeking help from healthcare providers are more.

![image](https://user-images.githubusercontent.com/89947247/201002718-0ca6c268-503e-4c10-8e47-5a2068c8e337.png)

1. For the patients who were not admitted, the claim amount reimbursed is very low.

2. Logically, there are more chances for fraud when the amount reimbursed is high. Therefore, chances of fraudulent activities in outpatient data is very low.

![image](https://user-images.githubusercontent.com/89947247/201002867-d16da1ea-1ae5-41ee-8355-9a38dd947353.png)

1. For inpatient data, the claim amount reimbursed is very high as there were proper diagnoses performed.

2. Naturally, the probability of fraud happening in the case of patients who were admitted should be high.

![image](https://user-images.githubusercontent.com/89947247/201002989-dd106e44-65da-42df-b6cb-294f708d8fb8.png)

1. For the patients who were not admitted and there was fraudulent activity detected, the number of patients with high reimbursement amounts are more in terms of absolute percentage.

![image](https://user-images.githubusercontent.com/89947247/201003064-eb12047c-fc80-456f-b6a9-851cf3131057.png)

1. For the patients with age>60, when the reimbursement amount is >60000, the percentage of fraudulent activity is high.

2. It is quite evident that as the claim amount reimbursed is high, the probability of fraud increases.

## Feature Selection:

Some of the features were created to understand the data better- like average insurance claim per provider and per attending physician. To understand which of the features are of highest importance, we used feature importance plots from a random forest library.
The most important features after our analysis are Insurance Claim Amount Reimbursed, Average of Insurance Claim Amount Reimbursed by a provider, and Average of Insurance Claim Amount Reimbursed by an Attending Physician. Hence, features “Attending Physician” and “Providers” are the highest contributors towards claims being fraudulent.

![image](https://user-images.githubusercontent.com/89947247/201003931-b0ca83df-56e6-4f2c-a33f-8a14fd1ae3e6.png)

## Methodologies:

After carrying out adequate data pre-processing and exploratory data analysis we employ three classification models to accurately classify a presented healthcare claim as fraudulent or non-fraudulent. The three models employed here, and the results produced by them are as follows:

1) Logistic Regression : On applying this model, AUC value comes out to be 0.94 which is pretty decent. Logistic Regression gives very good values of accuracy and specificity. At the same time, sensitivity is too low which is very important in our project. Furthermore, logistic regression is not easily interpretable and therefore difficult to understand.
ROC curve of Logistic Regression

![image](https://user-images.githubusercontent.com/89947247/201003456-2bccc6f7-a12d-4acd-bda0-ce5b72c93c48.png)

2) Random Forest Classifier: Tree based models are much more interpretable and come with properties like feature importance. They are easy to understand and are much more useful when we are dealing with a lot of features which is the case with our problem. Results shown below show that random forest results in very high AUC, accuracy, and sensitivity. It also gives us important features which are later covered in this answer.
ROC Curve of Random Forest

![image](https://user-images.githubusercontent.com/89947247/201003622-21a7763f-abb9-49c5-bf4a-33b31a7a0ae8.png)

3) Gradient Boosting Classifier: Boosting is an example of ensemble decision trees which improves the performance of decision trees. The Gradient Boosting algorithm builds a series of trees in which each tree is trained so that it attempts to correct the mistakes of previous trees in the series. After looking at the train accuracy, it is quite evident that this model overfits.
ROC curve of Gradient boosting classifier

![image](https://user-images.githubusercontent.com/89947247/201003717-2ed25998-7a2e-44e2-a8e1-e32f7d2f07ac.png)

## User Interface:
To showcase our concept, we created a user interface (UI) using the Flask framework and Bootstrap.

The user will receive a brief summary of our project as well as all statistical measures such as data distribution, trends in reimbursed claims, and the effect of age on reimbursed amount.

The user may also obtain an overview of the models which Includes,

1. Models brief description and how does it work to perform predictions

2. Receiver Operating Characteristics, When the distinguishing threshold of a binary classifier
system is changed, the ROC Curve shows its diagnostic capabilities.

3. Performance metrics such as confusion matrix, A confusion matrix is a table that is used to define the performance of a classification method. Such as Accuracy, Sensitivity, Specificity, Kappa Value, AUC, F1-Score Train, F1-Score Validation. 

Finally, there is a tab called Most Efficient Model where the user may go through all of the most significant and least important features and make an informed selection about which model to utilize for their forecast.

The UI consists of four tabs:
1. Home: It contains a brief introduction of our project, motivation, potential challenges, scope of this project.

![image](https://user-images.githubusercontent.com/89947247/201004524-1e78f18b-5dfc-4deb-b5be-0dcb044b5c9d.png)

2.Statistics: It contains all the Exploratory Data Analysis and their corresponding observations. It will help the users to have a better understanding of the data by looking at some observations.

![image](https://user-images.githubusercontent.com/89947247/201004642-7b04b378-7cfb-4490-a75b-8d285954275b.png)

3.Models: It consists of three sub-menus providing ROC curve and Performance metrics of all three models. Users can look at the evaluation of the models and make better decisions.

![image](https://user-images.githubusercontent.com/89947247/201004720-e5f13404-f869-4888-bb39-e6cb4c166541.png)

4.Most Efficient Model: It consists of three submenus providing ROC curve and performance metrics of all three Random Forest models. These three random forest models are distinguished based on the hyper-parameters. Furthermore, users will be able to look at important features provided by Random Forest Algorithm.

![image](https://user-images.githubusercontent.com/89947247/201004808-2770a876-436e-4f63-a5dc-b4847b5cd142.png)

## Conclusion:

Upon analyzing the performance metrics of all three classifiers we can infer that all of them produce good accuracy values. However, accuracy cannot be considered as the only metric while evaluating various classification models. In this specific classification task, the sensitivity or recall score plays a very vital role in evaluating our models as the cost of not classifying an observation as positive correctly (I.e as fraudulent) is huge. From the above obtained results, we observe that random forest classifiers exhibit the best sensitivity scores. Our gradient boosting classifier exhibits a perfect training accuracy score which is only possible in a hypothetical scenario and hence overfits our data.
