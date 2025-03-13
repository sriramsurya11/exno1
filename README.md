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
df=pd.read_csv('/content/SAMPLEIDS.csv')
df
```
![Screenshot 2025-03-12 133152](https://github.com/user-attachments/assets/6589d151-4108-449a-858e-fc7fddd78672)

```
df.head()
```
![Screenshot 2025-03-12 133313](https://github.com/user-attachments/assets/08d7faed-3bbf-4a0b-8c31-3340b83ffbcb)

```
df.tail()
```
![Screenshot 2025-03-12 133346](https://github.com/user-attachments/assets/4b44512e-5da8-4bca-b35c-6da5afd68e02)

```
df.isnull()
```
![Screenshot 2025-03-12 133432](https://github.com/user-attachments/assets/b7b68d69-53ae-44de-a741-02a82f00c3e6)

```
df.notnull()
```
![Screenshot 2025-03-12 133501](https://github.com/user-attachments/assets/2b69732d-4b58-4b4c-9713-31e181577c6e)

```
df.fillna(55)
```
![Screenshot 2025-03-12 133530](https://github.com/user-attachments/assets/ef385ead-d6a9-46bf-a4d1-a8e5c37127c6)

```
df.dropna()
```
![Screenshot 2025-03-12 133614](https://github.com/user-attachments/assets/4e6a3ae8-3159-4769-a428-f67cf44f02bf)

```
df.isnull().sum()
```
![Screenshot 2025-03-12 133635](https://github.com/user-attachments/assets/fb438f27-e7f6-4e6b-870f-961f40875413)

```
df.isnull().any()
```
![Screenshot 2025-03-12 133654](https://github.com/user-attachments/assets/38f18d16-7b0b-48a1-93cc-60e780d81b78)

```
df.dropna()
```
![Screenshot 2025-03-12 133722](https://github.com/user-attachments/assets/fbf640a5-2d57-4fdc-8425-c0e545746130)

```
df.fillna(0)
```
![Screenshot 2025-03-12 133812](https://github.com/user-attachments/assets/c0cd7fd2-30dd-4b96-8d02-910611881389)

```
df.fillna(method = 'ffill')
```
![Screenshot 2025-03-12 133848](https://github.com/user-attachments/assets/41d33cea-3240-4091-95e5-6fa426063fe7)

```
df.fillna(method = 'bfill')
```
![Screenshot 2025-03-12 133912](https://github.com/user-attachments/assets/e5b5a099-abd6-47f0-ad39-d9b4d7137a5c)

```
df_dropped = df.dropna()
df_dropped
```
![Screenshot 2025-03-12 133935](https://github.com/user-attachments/assets/ba4e75f5-1023-44bf-8b87-8637ef7c2830)

```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![Screenshot 2025-03-12 134008](https://github.com/user-attachments/assets/29a7fb13-be25-411c-b98d-ec1eac8a50d8)

```
df.fillna({'GENDER':'MALE','NAME':'HARI','ADDRESS':'CHENNAI','M4':'87.0'})
```
![Screenshot 2025-03-12 134036](https://github.com/user-attachments/assets/6ff695ab-abdf-42fa-8945-884d9984331d)

```
iris=pd.read_csv('/content/iris.csv')
iris
```
![Screenshot 2025-03-12 134121](https://github.com/user-attachments/assets/e7ea07f7-8a6d-4735-862a-b50f49ef49e1)

```
iris.info()
```
![Screenshot 2025-03-12 134147](https://github.com/user-attachments/assets/c955db79-bf3f-440e-8ff8-024dfeef2fb5)

```
iris.describe()
```
![Screenshot 2025-03-12 134215](https://github.com/user-attachments/assets/6c3ef03e-8665-42cb-9c01-69bcc0c2f5e8)

```
iris.shape
```
![Screenshot 2025-03-12 134326](https://github.com/user-attachments/assets/d8739150-b34d-4ffc-ba45-2262ed04d4cb)


```
import seaborn as sns
sns.boxplot(x='sepal_width',data=iris)
```
![Screenshot 2025-03-12 134348](https://github.com/user-attachments/assets/5fc80d4e-b21c-45d0-b868-04963133b3bb)

```
iris.isnull().sum()
```
![Screenshot 2025-03-12 134406](https://github.com/user-attachments/assets/e847a4c9-509d-4165-9c4c-14ffa8c62b78)

```
q1=iris.sepal_width.quantile(0.25)
q3=iris.sepal_width.quantile(0.75)
iqr=q3-q1
iqr
```
![Screenshot 2025-03-12 134424](https://github.com/user-attachments/assets/8ac2e7b8-3b1b-4f71-bad0-d1f771f889fd)

```
rid=iris[((iris.sepal_width<(q1-1.5*iqr))|(iris.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```
![Screenshot 2025-03-12 134453](https://github.com/user-attachments/assets/1dcebe50-2566-4c01-b5a6-49fb799b72af)

```
rid=iris[~((iris.sepal_width<(q1-1.5*iqr))|(iris.sepal_width>(q3+1.5*iqr)))]
rid
```
![Screenshot 2025-03-12 134522](https://github.com/user-attachments/assets/2c1fec7b-ed12-4dac-9f90-192beed502e2)

```
rid=iris[((iris.sepal_width>(q1-1.5*iqr))&(iris.sepal_width<(q3+1.5*iqr)))]
rid
```
![Screenshot 2025-03-12 134600](https://github.com/user-attachments/assets/5ca24360-69f5-44c8-a7d7-d28a3cd32638)

```
sns.boxplot(x='sepal_width',data=rid)
```
![Screenshot 2025-03-12 134626](https://github.com/user-attachments/assets/165d3642-895b-40e1-84bb-81b85610daa4)

```
import numpy as np
import scipy.stats as stats
z=np.abs(stats.zscore(iris['sepal_width']))
z
```
![Screenshot 2025-03-12 134646](https://github.com/user-attachments/assets/6d8f93ea-9c49-42dd-8875-f3827b0d7591)

```
iris=iris[(z<3)]
iris
```
![Screenshot 2025-03-12 134707](https://github.com/user-attachments/assets/7e49a52a-b6bd-44b1-a2c9-06defaf0557f)

# Result
 Hence the data was cleaned , outliers were detected and removed.
