# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
 import pandas as pd
 df=pd.read_csv("SAMPLEIDS.csv")
 df
```
![image](https://github.com/user-attachments/assets/fa0661ff-792b-4c76-81e5-6ded23acc908)
```
 df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/a70080e4-5fd0-444e-9f9a-946151d18b11)
```
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/9250830b-78b5-4d8e-9f7b-e243cea5adce)
```
 df.dropna()
```
![image](https://github.com/user-attachments/assets/22beb27c-4d44-44ce-ba65-e486b78824ee)
```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/d108ba53-41d3-4a91-994e-6e638ded9268)
```
 df.fillna(method = 'ffill')
```
![image](https://github.com/user-attachments/assets/2b3fea23-b0ab-4a49-b73f-1fa1bac30d63)

```
 df.fillna(method = 'bfill')
```
![image](https://github.com/user-attachments/assets/1a419e59-85f5-4fc2-9b5f-9dc5b06d4ceb)
```
 df_dropped = df.dropna()
 df_dropped
```
![image](https://github.com/user-attachments/assets/ba830db5-e445-451a-b9e4-d8c4de9b811c)
```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/669f6760-1548-4c4c-be82-f4dae5081c94)
```
IQR(Inter Quartile Range)

import pandas as pd
import seaborn as sns
ir=pd.read_csv('iris.csv')
ir
```
![image](https://github.com/user-attachments/assets/fa9167b5-cd7c-455b-8b09-2bb2326c21e8)
```
 ir.describe()
```
![image](https://github.com/user-attachments/assets/3a16f9b0-1dbe-468e-9ca8-41e1474c4cbc)
```
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/2b4f1e12-7d6f-4200-a575-f23007caaddd)
```
 c1=ir.sepal_width.quantile(0.25)
 c3=ir.sepal_width.quantile(0.75)
 iq=c3-c1
 print(c3)
```
![image](https://github.com/user-attachments/assets/e8070d8d-d3e7-4a10-89b1-4b93993d1393)
```
 rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
 rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/bdd8a78d-bf70-4d33-9eeb-d22317f25c82)
```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
 delid
```
![image](https://github.com/user-attachments/assets/cb0bfacd-2a25-4953-9d19-ed29cd61d770)
```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/99341382-e945-4085-aa84-56b5cbf4768b)
```
Z-SCORE

 import matplotlib.pyplot as plt
 import pandas as pd
 import numpy as np
 import scipy.stats as stats
 dataset=pd.read_csv("heights.csv")
 dataset
```
![image](https://github.com/user-attachments/assets/6d058473-fc96-4b45-b22b-a919c5a6f8a3)
```
df = pd.read_csv("heights.csv")
 q1 = df['height'].quantile(0.25)
 q2 = df['height'].quantile(0.5)
 q3 = df['height'].quantile(0.75)
 iqr = q3-q1
 iqr
```
![image](https://github.com/user-attachments/assets/7133d85c-3c30-4634-9c35-689e87773a8f)
```
 low = q1- 1.5*iqr
 low
```
![image](https://github.com/user-attachments/assets/cdac70a0-bcea-47b4-acca-46b0ee84c96b)
```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/491f02d0-31bd-4a29-bc29-f0383a801585)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
 df1
```
![image](https://github.com/user-attachments/assets/12684264-defa-4684-8243-0f6d0840e5a3)
```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/27b78025-e10d-4d62-97b7-a38b20219460)
```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/3b12fcca-48b2-48f9-8c50-1db799d6b72d)

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
