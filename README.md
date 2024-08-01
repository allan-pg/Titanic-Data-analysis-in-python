# Titanic Data Analysis in Python
![image](https://github.com/user-attachments/assets/e614f4bf-5a5d-423b-8a75-1b0c68bae942)

# Introduction

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
