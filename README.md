# ODD2023-Datascience-Ex-04
# Ex-04-Multivariate-Analysis
# AIM
To perform Multivariate EDA on the given data set.

# Explanation:
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

# ALGORITHM:
## STEP 1
Import the built libraries required to perform EDA and outlier removal.

## STEP 2
Read the given csv file

## STEP 3
Convert the file into a dataframe and get information of the data.

## STEP 4
Return the objects containing counts of unique values using (value_counts()).

## STEP 5
Plot the counts in the form of Histogram or Bar Graph.

## STEP 6
Use seaborn the bar graph comparison of data can be viewed.

## STEP 7
Find the pairwise correlation of all columns in the dataframe.corr()

## STEP 8
Save the final data set into the file

# PROGRAM
```
import pandas as pd
from scipy import stats
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```
```
from google.colab import files
uploaded = files.upload()
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/f333ee32-22ef-45ce-b80c-04295978efd9)
```
df = pd.read_csv('diabetes.csv')
df
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/2a00aacf-1b9a-474b-b512-6e4f4831ce8f)
```
df.isnull().sum()
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/5385dd90-bafd-4b4f-bf71-4720d6b26166)
```
q1 = df.quantile(0.25)
q3 = df.quantile(0.75)
iqr = q3 - q1
iqr
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/6769f857-6a0b-46d5-878c-231b0d08200c)
```
low = q1 - 1.5*iqr
high = q1 + 1.5*iqr
df = df[(df >= low) & (df <= high)]
df
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/99a40faf-45c0-4356-9e02-1bee9f25fd82)
```
sns.boxplot(df)
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/2fb9cd21-f853-485e-b71d-03bf7e4e29d9)
```
plt.figure(figsize = (14,6))
sns.scatterplot(x = 'Glucose',y='BloodPressure',data = df)
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/ca13ed60-088e-42e7-b775-48e12858545e)
```
sns.scatterplot(x = 'Glucose',y='Insulin',data = df)
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/e9795f5a-138f-4331-b453-600e737f7460)
```
sns.scatterplot(x = 'Glucose',y='DiabetesPedigreeFunction',data = df)
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/292ff48f-4f73-4f47-88b1-47b63d08a986)
```
sns.scatterplot(x = 'Glucose',y='Age',data = df)
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/e380a82d-4188-48f5-95f5-c4c42a95a1f2)
```
sns.heatmap(df.corr(),annot = True)
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/2becb23e-c0a3-4f2d-8b09-fbfc7bf13986)
```
from google.colab import files
uploaded = files.upload()
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/240d17b3-d8b8-47cc-833d-4489e61ea9dd)
```
df = pd.read_csv('employeesal.csv')
df
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/f83c27b6-7668-46d0-879b-ba4c0441ff28)
```
df.isnull().sum()
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/d63878c9-9d8e-4a98-82a9-1d66044839c8)
```
numeric_cols = df.select_dtypes(include=[int, float])
q1 = numeric_cols.quantile(0.25);
q3 = numeric_cols.quantile(0.75);
iqr = q3 - q1
iqr
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/9b8bc57c-5d28-4793-8d75-0f3f5494944b)
```
low = q1 - 1.5*iqr
high = q1 + 1.5*iqr
numeric_cols = numeric_cols[(numeric_cols >= low) & (numeric_cols <= high)]
numeric_cols.dropna()
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/0d7f8dc0-da50-4597-b283-3ec6d2e06f3c)
```
sns.boxplot(numeric_cols)
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/a601c0a2-2ef5-405a-bb91-c53652e4fd9e)
```
sns.scatterplot(x = 'Salary',y='Age',data = numeric_cols)
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/3afff68d-6371-43df-8f8a-ceada7a1e76c)
```
sns.scatterplot(x = 'Experience_Years',y='Salary',data = numeric_cols)
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/85d5f194-7a56-4d24-949a-f75b4d6a9f6c)
```
sns.scatterplot(x = 'Experience_Years',y='Age',data = numeric_cols)
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/ca4c0e39-a6a9-4eff-a8f6-25be9701da97)
```
sns.heatmap(numeric_cols.corr(),annot = True)
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/3ec3974b-7d24-468d-baf5-2fdcd6fe7abb)
```
from google.colab import files
uploaded = files.upload()
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/90a01b93-23a5-4bcb-b8d2-0fb7f1ebcf55)
```
df = pd.read_csv('SuperStore.csv')
df
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/6a02623e-dad9-49a1-89f2-c186105fbfde)
```
df.isnull().sum()
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/33652faf-53bc-465c-85af-de2554cb8061)
```
df.dropna()
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/845e87be-538f-4ae9-9698-db2fa682c6de)
```
df.dtypes
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/dcd2349f-3ee9-47f4-96d7-0bc88960de5e)
```
numeric_cols = df.select_dtypes(include=[int,float])
q1 = numeric_cols.quantile(0.25);
q3 = numeric_cols.quantile(0.75);
iqr = q3 - q1
iqr
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/1201713a-71f1-4b7e-be7e-0cb5d3f857a2)
```
low = q1 - 1.5*iqr
high = q1 + 1.5*iqr
numeric_cols = numeric_cols[(numeric_cols >= low) & (numeric_cols <= high)]
```
```
sns.boxplot(numeric_cols)
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/928a091f-f407-4685-9519-e24e1a6a86c4)
```
sns.heatmap(numeric_cols.corr(),annot = True)
```
![image](https://github.com/madhi43/ODD2023-Datascience-Ex-04/assets/103943383/434d2b1b-5813-47be-a245-6dd1436a1832)

# RESULT
Thus we have read the given data and performed the multivariate analysis with different types of plots
