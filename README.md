# Salary Prediction Based on Job Description
# Problem

Backgroud : Employers need to offer competitive salaries to attract right talent. Job seekers need to be aware of the prevailing wages/salaries. 

Goal : Predict salaries given Industry, position, education, degree, number of years for experience and distance from metro

# Data collection 
Train dataset has total of 1000000 rows and 8 columns. Following are the deatails of data:

jobId-jobId is the unique id for each job posting.

companyId- There are total of 63 unique company id, representing each company.

jobType-jobType column represents individual job type. Such as ECO, manager, Vice_precident, CFO etc.

degree-degree column refers to 5 different types of degree employee has. They are doctoral, masters, bachelor, High school and None.

major-This represents what major they have. For example, Physics, chemistry, biology, engineering, business etc.

industry -industry column represents about different types of industries like Web, financical service, health, education, service, oil and auto.

yearsExperience- This difines how many years of experiences employee has

milesFromMetropolis-This indicates how far the job location from the metropliton area.

Six of them are categorical columns and two are numerical columns. There are no missing and duplicate values in the dataset. Following are the descriptions of the columns

# File Guide
Salary Prediction EDA.ipynb- This notebook describes obtaining data, EDA and data preprocessing.

SalaryPrediction.ipynb-This notebook contains data preprocessing, modeling, parameter tuning and predictions.

# Data preprocessing

As a part of data cleaning I have impelemented following steps

- There are no duplicate rows
- Few rows have salary as 0.Removed these rows as these rows are tiny fraction of overall dataset
- It might help to build two datasets - one with Janitor/Junior staff and one with every other job type
- Degree does not seem like great differentiator
- Salary is directly proportional to the Years of experience (correlation coefficient 0.38)
- Salary is inversely proportional to miles from Metro (correlation coefficient -0.3)
- Highly paid industries are OIL and FINANCE and lowest paid is Education. 
- CEO is paid highest followed by CTO, CFO, Vice_president, Senior, Juior and Janitar. 
- Label encoding to convert the categorical data into numerical.
- There is interaction between yearofExperience and MilesfromMetro

# Evaluation metric
- MSE has been used to evaluate best model. MSE addresses both bias and variance

# Modeling
Two models were tries 
1.  Multivariate Regression : MVR model as been built with interaction variable, average salary for all individual group and rest of the variables provided in the dataset. Got an MSE of 907. This is not great score considering expected MSE of 360

2. XGBoost : XGBoost has been built to understand if there were any non linear relationship. Rightly so MSE has come down from 907 to 355, less than expected score of 360. Same set of  variable have been used.

# Deployment and follow up
XGBoost model can be deployed as baseline model until better model is found. Instead of trying to tune the parameters for this model, it is advisable to train the model using additional variables/feature to get better results

