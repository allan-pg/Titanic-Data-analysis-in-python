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
# Statistical Analysis 
## 1.7  Descriptive Statistics
```
df.describe()
```
![image](https://github.com/user-attachments/assets/8ced9615-2b9b-45d7-a5ee-75f77b8a96ff)

## Explanation
- From the above image we have the mean, max, min, std, count... and this is performed only on mumerical columns
- To perform a descriptive analysis on non numerical columns
```
df.describe(include = 'object')
```
## 1.8 Data Correlation
- Check how your data is related
```
s = df.corr()
```
![image](https://github.com/user-attachments/assets/448e0c1a-7805-47b6-b112-56406383a3c8)

# Questions
## 1.0 Show the distribution of data on numerical columns
- I used box plots in order to also check for outliers
```
for i in df.select_dtypes(include = 'number').columns:
    sns.boxplot(data = df, x = i)
    plt.show()
```
![image](https://github.com/user-attachments/assets/715d0d85-f70b-4826-8261-c1922926f0a7)

## 2 Show how your data appears column wise
- I used a histogram
- A histogram is a graph that shows the frequency of numerical data using rectangles.
```
for i in df.select_dtypes(include = 'number').columns:
    sns.histplot(data = df, x = i)
    plt.show()
```
![image](https://github.com/user-attachments/assets/e31bf360-1131-421c-a3ce-7ecb15c23149)

- From above histogram age 28 appeared to be of most passengers
## 3 How many male vs female passengers were onboard
```
df['Sex'].value_counts()
```
![image](https://github.com/user-attachments/assets/c628e45f-37bf-4d35-a861-7053170ece3e)

- Male passengers were onboard more than female passengers
## 4 Visualize male and female passengers
```
plt.figure(figsize = (18, 6))

plt.subplot(1, 2, 1)
df['Sex'].value_counts().plot(kind = 'bar')
plt.title("Male vs Female Passengers")
plt.ylabel('Number of passengers')
plt.show()
```
![image](https://github.com/user-attachments/assets/5d9e4532-5f75-4e34-b00d-fac9c4062923)

## 5 How many people Survived in Gender form
```
df['Survived'].value_counts()
```
- More males survived because they were many but overall more females survived

## 6 Visualize how passengers survived
```
plt.subplot(1, 2, 2)
df['Survived'].value_counts().plot(kind = 'bar')
plt.title('Passengers who died vs survived')
plt.ylabel('NO. of passengers')


plt.show()
```
![image](https://github.com/user-attachments/assets/3b66af48-148b-47ca-afe3-6b53b757eb58)

## 7 Show how passengers were distributed per class and gender
```
plt.figure(figsize = (18, 6))

plt.subplot(1, 2, 1)
sns.countplot(x = df['Sex'], hue = df['Pclass'])
plt.title('Passenger class to Gender')
plt.xlabel('Gender')
plt.ylabel('Number of passengers')
plt.show()
```
![image](https://github.com/user-attachments/assets/9eb30f0c-4160-4c46-962e-b328bc1896be)
- There were more passengers in third class than in first class and second class

## 8 Show how passengers survived were distributed per class and gender
```
plt.subplot(1, 2, 2)
sns.countplot(x = df['Survived'], hue = df['Pclass'])
plt.title('Survived Passenger to class of Passenger')
plt.xlabel('Survived')
plt.ylabel('Number of passengers')
plt.show()
```
![image](https://github.com/user-attachments/assets/d237cb5a-dc22-4857-9f2a-22420255956c)
- Many passengers from third class did not survive
- Most first class passengers survived

## 9 show passengers age in each passenger class
```
plt.figure(figsize = (15, 7))
sns.pointplot(x = 'Pclass', y = 'Age', data = df, linestyles = '--', capsize = .3)
plt.show(
```
- I used a point plot to show age distribution per class

# Excel Titanic Dashboard


