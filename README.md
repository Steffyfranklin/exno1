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

df=pd.read_csv("/content/SAMPLEIDS (1).csv")

df
```
![image](https://github.com/user-attachments/assets/6182b1fc-804f-4ec4-885f-32495f90ced0)

```
df.isnull()
```
![image](https://github.com/user-attachments/assets/296092e0-19f9-4339-a29b-7a46c1cfa36f)

```
df.notnull()
```
![image](https://github.com/user-attachments/assets/11f02fed-d2da-4f56-9021-61c680d3c0a4)

```
df.dropna(axis=1)
```
![image](https://github.com/user-attachments/assets/e0c34335-2b90-4033-bce0-b1a2d7f99c67)

```
df.dropna(axis=0)
```
![image](https://github.com/user-attachments/assets/12e0c3bc-9cb2-4313-aa9a-48af10902088)

```
dfs = df[df['TOTAL'] > 270]

dfs
```
![image](https://github.com/user-attachments/assets/1d61aecb-a0a8-4c31-b479-7c77e75e87c6)

```
dfs = df[df['NAME'].str.startswith(('A','C'))&(df['TOTAL']>250)]

dfs

df.iloc[:4]
```
![image](https://github.com/user-attachments/assets/3454e647-899b-4285-9885-c7eabbe1765a)

```
df.iloc[0:4,1:4]
```
![image](https://github.com/user-attachments/assets/b4e1b3e1-b6d6-4303-b74b-2364ffe56d01)

```
df.iloc[[1,3,5],[1,3]]
```
![image](https://github.com/user-attachments/assets/a44c59a4-198e-471c-af34-123ba670dedd)

```
df
```
![image](https://github.com/user-attachments/assets/0b5ba6b1-05c0-41ef-8756-7fb97fb8cc95)

```
dff=df.fillna(0)

dff
```
![image](https://github.com/user-attachments/assets/c5226444-6934-490b-b3cc-749fbdd72c9f)

```
df['TOTAL'].fillna(value=df['TOTAL'].mean())
```
![image](https://github.com/user-attachments/assets/5ee77db7-0ec8-46a0-9f0b-819f68f53587)

```
df.fillna(method='ffill')
```
![image](https://github.com/user-attachments/assets/7a263fb8-e2e0-42e6-bf73-e079415d5660)

```
df.fillna(method='bfill')
```
![image](https://github.com/user-attachments/assets/4acaa5d6-c2b1-4c4b-9270-55604e1a11b2)

```
df['TOTAL'].fillna(value=df['TOTAL'].mean(),inplace=True)

df
```
![image](https://github.com/user-attachments/assets/c01e7a30-ad4e-4205-983e-6b6b5bc7b372)

```
import pandas as pd
import seaborn as sns
import numpy as np

age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```
![image](https://github.com/user-attachments/assets/4d7c316a-8c15-4d70-8b37-2b6c42240266)
```
sns.boxplot(data=af)
```
![image](https://github.com/user-attachments/assets/9247bd34-9cf6-4b40-b362-83ce1998b9b1)
```
sns.scatterplot(data=af)
```
![image](https://github.com/user-attachments/assets/75ae9681-7982-4557-8c82-bedd498298e5)
```
q1=af.quantile(0.25)
q2=af.quantile(0.5)
q3=af.quantile(0.75)
iqr=q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/d911db5c-7a7c-442d-b1fd-23b3195ce543)
```
Q1=np.percentile(af,25)
Q3=np.percentile(af,75)
IQR=Q3-Q1
IQR
```
![image](https://github.com/user-attachments/assets/3cba056f-fecd-4623-99f1-f2caa379c195)
```
lower_bound=Q1-1.5*IQR
upper_bound=Q3+1.5*IQR

lower_bound
```
![image](https://github.com/user-attachments/assets/827736bf-9ce2-4b99-bf0f-f7c41e28e3b1)
```
upper_bound
```
![image](https://github.com/user-attachments/assets/d358e833-9add-41b2-a75c-68b13c84293c)
```
outliers=[x for x in age if x<lower_bound or x>upper_bound]

print("Q1:",Q1)
print("Q3:",Q3)
print("IQR:",IQR)
print("Lower bound:",lower_bound)
print("Upper bound:",upper_bound)
print("Outliers:",outliers)
```
![image](https://github.com/user-attachments/assets/13bc46b0-178c-4ab9-85b4-8bdfbf50f21e)
```
af=af[((af>=lower_bound)&(af<=upper_bound))]
af
```
![image](https://github.com/user-attachments/assets/c84a6f31-ba88-4b5c-9ff1-0f251230c03d)
```
af.dropna()
```
![image](https://github.com/user-attachments/assets/dc53e415-9322-4241-b285-957606e3400c)
```
sns.boxplot(data=af)
```
![image](https://github.com/user-attachments/assets/1e8d4525-7867-408f-83ba-9cfd58ac1a8a)
```
sns.boxplot(data=af)
```
![image](https://github.com/user-attachments/assets/157efd27-d153-47b9-934b-6037ad6ab0ab)
```
sns.scatterplot(data=af)
```
![image](https://github.com/user-attachments/assets/dc911456-ef2f-4883-9b11-4d94875bdc4e)
```
data=[1,2,2,2,3,1,1,15,2,2,2,3,1,1,2]
mean=np.mean(data)
std=np.std(data)
print('mean of the dataset is',mean)
print('std.deviation is',std)
```
![image](https://github.com/user-attachments/assets/f3ab9e03-19ec-4ea3-9059-0cfd2de1aa75)
```
threshold=3
outlier=[]
for i in data:
  z=(i-mean)/std
  if z>threshold:
    outlier.append(i)
print('outlier in dataset is',outlier)
```
![image](https://github.com/user-attachments/assets/35aa8a09-9e7b-4b9e-a07c-f87674ba7c07)
```
data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}

import pandas as pd
import numpy as np
import seaborn as sns
import pandas as pd
from scipy import stats

data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,80,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df
```
![image](https://github.com/user-attachments/assets/bd9db4ee-f99b-44c1-b4a3-395e51532b54)
```
z=np.abs(stats.zscore(df))
print(df[z['weight']>3])
```
![image](https://github.com/user-attachments/assets/b4011db0-1346-41f5-8234-3b6435daf498)
```
val=[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]

Out=[]
def d_o(val):
  ts=3
  m=np.mean(val)
  sd=np.std(val)
  for i in val:
    z=(i-m)/sd
    if np.abs(z)>ts:
      Out.append(i)
  return Out

op=d_o(val)

op
```
![image](https://github.com/user-attachments/assets/022b6db2-2f28-4798-b0ee-f21e838a3e88)

# Result
         the given data and perform data cleaning and successfully saved the cleaned data to a file.
