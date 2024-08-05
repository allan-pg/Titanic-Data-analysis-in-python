# Titanic Data Analysis in Python and Dashboard in Excel
![image](https://github.com/user-attachments/assets/07a38ef2-021a-4843-b5e0-11c7ea4e4c50)


# Introduction

## Tools Used
- Pandas
- Seaborn
- Matplotlib
- Linear Regression
- Numpy
## 1.1 import python libraries 
```
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
import os
import missingno as msn
plt.style.use('ggplot')
```
## 1.2 load your data
```
dataset = pd.read_csv(r'C:\Users\Admin\Desktop\csv files\train_and_test2.csv')
dataset.head(2)
```
## 1.3 get a information of dataset
```
dataset.info()
```

![image](https://github.com/user-attachments/assets/33444591-75df-4426-865b-7d2aef7734ed)

- The dataset has 1309 columns and their data types have been defined

## Copy your dataframe so as to remain with an original copy 
```
df = dataset.copy()
```
## 1.4 Check columns
```
df.columns
```
![Capture](https://github.com/user-attachments/assets/9489da07-40a6-4a33-b23b-9cf084e32746)

**Drop unnecessary columns**
```
df = df.drop(['zero', 'zero.1',
       'zero.2', 'zero.3', 'zero.4', 'zero.5', 'zero.6',
        'zero.7',
       'zero.8', 'zero.9', 'zero.10', 'zero.11', 'zero.12', 'zero.13',
       'zero.14',  'zero.15', 'zero.16', 'zero.17',
       'zero.18'  ], axis = 1)
df.head()
```
## 1.5 Rename columns to have a clear view about them  
```
df = df.rename(columns = {'2urvived' : 'Survived'})
```
## 1.6 Check for null values
```
df.isna().sum()
```
![Capture](https://github.com/user-attachments/assets/8b5d41f1-5f62-4154-ab32-c9a7feb26ea3)

- **Drop rows wit null values since they do not make up to 5%**
```
df = df.loc[~df['Embarked'].isna()].reset_index(drop = True)
```
- **Null values were droped**
![image](https://github.com/user-attachments/assets/965ec2e9-798a-43f4-b8fd-71dc2fb06df2)

- our rows ave reduced from 1309 to 1307
## 1.7
