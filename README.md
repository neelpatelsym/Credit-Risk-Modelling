# Credit-Risk-Modelling
The project focuses on utilizing a machine learning approach to address a crucial challenge faced by financial institutions: predicting instances of customers defaulting on payments in Taiwan. The objective is to employ advanced algorithms to tackle this significant problem in the financial sector.

## Variables
There are 25 variables:

ID: ID of each client
<br>LIMIT_BAL: Amount of given credit in NT dollars (includes individual and family/supplementary credit
<br>SEX: Gender (1=male, 2=female)
<br>EDUCATION: (1=graduate school, 2=university, 3=high school, 4=others, 5=unknown, 6=unknown)
<br>MARRIAGE: Marital status (1=married, 2=single, 3=others)
<br>AGE: Age in years
<br>PAY_0: Repayment status in September, 2005 (-1=pay duly, 1=payment delay for one month, 2=payment delay for two months, ... 8=payment delay for eight months, 9=payment delay for nine months and above)
<br>PAY_2: Repayment status in August, 2005 (scale same as above)
<br>PAY_3: Repayment status in July, 2005 (scale same as above)
<br>PAY_4: Repayment status in June, 2005 (scale same as above)
<br>PAY_5: Repayment status in May, 2005 (scale same as above)
<br>PAY_6: Repayment status in April, 2005 (scale same as above)
<br>BILL_AMT1: Amount of bill statement in September, 2005 (NT dollar)
<br>BILL_AMT2: Amount of bill statement in August, 2005 (NT dollar)
<br>BILL_AMT3: Amount of bill statement in July, 2005 (NT dollar)
<br>BILL_AMT4: Amount of bill statement in June, 2005 (NT dollar)
<br>BILL_AMT5: Amount of bill statement in May, 2005 (NT dollar)
<br>BILL_AMT6: Amount of bill statement in April, 2005 (NT dollar)
<br>PAY_AMT1: Amount of previous payment in September, 2005 (NT dollar)
<br>PAY_AMT2: Amount of previous payment in August, 2005 (NT dollar)
<br>PAY_AMT3: Amount of previous payment in July, 2005 (NT dollar)
<br>PAY_AMT4: Amount of previous payment in June, 2005 (NT dollar)
<br>PAY_AMT5: Amount of previous payment in May, 2005 (NT dollar)
<br>PAY_AMT6: Amount of previous payment in April, 2005 (NT dollar)
<br>default.payment.next.month: Default payment (1=yes, 0=no)

## Objective
Our focus would be to generate a machine learning model that predicts whether the customer will default payment next month or not?
Through correctly predecting the default state of customers, bank can take appropriate steps and can reduce the loss of millions of dollars incurred by default behaviour.
Upon reviewing data, it is decided to solve the issue through following approach:
1. Data Cleaning and exploration
2. Exploratory Data Analysis (EDA)
3. Feature Generation
4. Feature Selection
5. Model training
6. Model Evaluation
7. Model Selection

### Data Cleaning and exploration
The data contained many unlabeled values in education, marriage and pay columns. Those unlabeled values are merged them with the nearest label based on assumption of data entry error.
Moreover the data is checked for dupilates and null values. There were no duplicates or null values in the data.
Also the column names are renamed in order to convey meaningful information.

### Exploratory Data Analysis (EDA)
Following were major insights derived from EDA:
1. Men are more likely to default then women.
<br>![image](https://github.com/neelpdesai/Credit-Risk-Modelling/assets/137664550/2919531d-fff7-4b48-8602-14d50a7c1d44)
2. Default probability changes with combination of defaulter's education, marriage and sex state.
<br>![image](https://github.com/neelpdesai/Credit-Risk-Modelling/assets/137664550/0293c040-c48b-4f30-bbb8-bad9d02c1700)
<br>![image](https://github.com/neelpdesai/Credit-Risk-Modelling/assets/137664550/cf72ce1e-f439-48c6-82cd-3cd9e9e0d37f)
3. Outlier analysis revealed that the data points infered as outliers are the crediters belonging to specific group.
<br>![image](https://github.com/neelpdesai/Credit-Risk-Modelling/assets/137664550/b14adec0-4aad-4c7d-9c1c-e17270a77c19)
4. People with high bill amount,less payment amount and less credit balance are more prone to default.
<br>![image](https://github.com/neelpdesai/Credit-Risk-Modelling/assets/137664550/706bc18c-4a42-4a61-83e2-87367cc58545)
5. There is a possibility of people from one age group is more likely to default.
<br>![image](https://github.com/neelpdesai/Credit-Risk-Modelling/assets/137664550/2da4c69f-e773-483b-b49b-0eeb74786590)

### Feature Generation and Feature Selection
With significant information available from EDA, additional features were generated.
Following is the few examples of the feature generated:
1. EDUCATION_MARRIAGE_BUCKET
2. EDUCATION_SEX_BUCKET
3. MARRIAGE_SEX_BUCKET
4. EDUCATION_MARRIAGE_SEX_BUCKET
5. AGE_BUCKET
6. CREDIT_LIMIT_BUCKET
7. PAY_AMT_BUCKET
and many more...
Also this feature are encoded to impute suitable numerical information for categories.

### Model training
The credit card default problem is a classic case of unbalanced machine learning problem.
We have 20% information of customers who has defaulted. This introduce a biasness in result of our model.
Thus, to balance the problem additional datapoints of defaulters are generated through Synthetic Minority Oversampling Technique (SMOTE).
After balancing the data is divided into train and test set.
The train data was trained on logistic regression, support vector classifier,Xtreme Gradient Boosting and Random Forest Classifier.

### Model Evaluation
As this is a binary classification problem, the F1 score become base for model evaluation.
Please refer to confusion matrix of all models
1. Logistic Regression:
<br> ![image](https://github.com/neelpdesai/Credit-Risk-Modelling/assets/137664550/92ec34d4-20e6-4517-b3c6-2593b06eabb1)
   ![image](https://github.com/neelpdesai/Credit-Risk-Modelling/assets/137664550/2a7e724a-3cb2-4f8a-8da8-b6bdbeaa280b)
2. Support Vector Classifier:
   <br>![image](https://github.com/neelpdesai/Credit-Risk-Modelling/assets/137664550/e0efd62c-d629-4562-ab8b-88f55891457e)
   ![image](https://github.com/neelpdesai/Credit-Risk-Modelling/assets/137664550/1e66633a-c2a6-4959-bfb9-af21960da880)
3. Random Forest Classifier:
  <br>![image](https://github.com/neelpdesai/Credit-Risk-Modelling/assets/137664550/d162ab65-1314-4716-9a55-81ec89fde609)
  ![image](https://github.com/neelpdesai/Credit-Risk-Modelling/assets/137664550/2d498616-32a9-4cb6-9772-cab3ce49b6ea)
4. Xtreme Gradient Boosting Classifier:
  <br>![image](https://github.com/neelpdesai/Credit-Risk-Modelling/assets/137664550/744e9ed0-bf22-4f2f-9b26-7911af189eca)
  ![image](https://github.com/neelpdesai/Credit-Risk-Modelling/assets/137664550/3799d49d-4db1-4c35-91ad-f9480d4bb5c8)

### Model Selection
Based on comparing F1 score and Confusion Matrix,the Random Forest Classifier model is selected for predicting default state of crediter in next month.
F1 score: 0.89
Accuracy : 89%

 
