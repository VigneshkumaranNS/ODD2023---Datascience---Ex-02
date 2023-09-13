# Ex02-Outlier

# AIM:
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

# ALGORITHM:
# STEP 1:
Read the given Data.
# STEP 2:
Get the information about the data.
# STEP 3:
Detect the Outliers using IQR method and Z score.
# STEP 4:
Remove the outliers:
# STEP 5:
Plot the datas using box plot.
# PROGRAM:
```
DEVELOPED BY: CHAITANYA
REGISTER NUMBER: 212222230024

import pandas as pd
df=pd.read_csv("/content/bhp.csv")
df.head()
df.describe()
df.info()
df.shape

import seaborn as sns
sns.boxplot(x="price_per_sqft",data=df)

### removing ouliers of bhp.csv file using IQR
Q1=df['price_per_sqft'].quantile(0.25)
Q3=df['price_per_sqft'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
newdata=df[(df['price_per_sqft']>=lower) & (df['price_per_sqft']<=upper)] 
print(newdata)   #new dataframe.
outliers=df[(df['price_per_sqft']<lower) | (df['price_per_sqft']>upper)]
print(outliers)
newdata.shape
sns.boxplot(x="price_per_sqft",data=newdata)


### removing ouliers of bhp.csv file using Zscore of 3

from scipy import stats
import numpy as np
z_score=np.abs(stats.zscore(df['price_per_sqft']))
newdata2=df[(z_score<3)]
print(newdata2)
outlier2=df[(z_score>=3)]
print(outlier2)
newdata2.shape
sns.boxplot(x="price_per_sqft",data=newdata2)

import pandas as pd
dataset=pd.read_csv("/content/height_weight.csv")
dataset.shape
dataset.describe()
dataset.info()
import seaborn as sns
sns.boxplot(x='height',data=dataset)

### Using IQR detect height outliers and print them( height_weight.csv)

Q1_height=dataset['height'].quantile(0.25)
Q3_height=dataset['height'].quantile(0.75)
IQR_HEIGHT=Q3_height-Q1_height
l_height=Q1_height-1.5*IQR_HEIGHT
u_height=Q3_height+1.5*IQR_HEIGHT
outliers_height=dataset[(dataset['height']<l_height) | (dataset['height']>u_height)]
print(outliers_height)
newdata_height=dataset[(dataset['height']>=l_height) & (dataset['height']<=u_height)]
print(newdata_height)
sns.boxplot(x='height',data=newdata_height)


### Using IQR, detect weight outliers and print them( height_weight.csv)

Q1_weight=dataset['weight'].quantile(0.25)
Q3_weight=dataset['weight'].quantile(0.75)
IQR_WEIGHT=Q3_weight-Q1_weight
l_weight=Q1_weight-1.5*IQR_WEIGHT
u_weight=Q3_weight+1.5*IQR_WEIGHT
outliers_weight=dataset[(dataset['weight']<l_weight) | (dataset['weight']>u_weight)]
print(outliers_weight)
newdata_weight=dataset[(dataset['weight']>=l_weight) & (dataset['weight']<=u_weight)]
print(newdata_weight)
sns.boxplot(x='weight',data=newdata_weight)
```
# OUTPUT:
# bhp.csv:
# df.head():
![image](https://github.com/chaitanya18c/ODD2023---Datascience---Ex-02/assets/119392724/ff0f3585-5697-4b0d-9de9-4e68a0bd3072)
# df.describe():
![image](https://github.com/chaitanya18c/ODD2023---Datascience---Ex-02/assets/119392724/8c180ebf-0048-43d0-9842-fd94d085a472)
# df.info():
![image](https://github.com/chaitanya18c/ODD2023---Datascience---Ex-02/assets/119392724/03d2c596-3bfc-4dba-b3f6-8e9daa848b2e)
# df.shape
![image](https://github.com/chaitanya18c/ODD2023---Datascience---Ex-02/assets/119392724/df97c96d-8724-4a8c-b39f-88a19dded9f8)
# BOXPLOT BEFORE REMOVING OUTLIERS
![image](https://github.com/chaitanya18c/ODD2023---Datascience---Ex-02/assets/119392724/42574795-e308-4df4-91f6-bc4abe450279)
# NEWDATA USING IQR
![image](https://github.com/chaitanya18c/ODD2023---Datascience---Ex-02/assets/119392724/aeca938f-ca96-4d7f-a415-1ea383d0dcee)
# OUTLIERS
![image](https://github.com/chaitanya18c/ODD2023---Datascience---Ex-02/assets/119392724/c5e6ad48-1f27-442c-b08a-3889bf21d8ec)
# newdata.shape
![image](https://github.com/chaitanya18c/ODD2023---Datascience---Ex-02/assets/119392724/220441c8-6cbd-4ea9-bd26-51cb61b5a220)
# BOXPLOT AFTER REMOVING OUTLIERS USING IQR
![image](https://github.com/chaitanya18c/ODD2023---Datascience---Ex-02/assets/119392724/31b688dd-6826-4957-a3da-574aa51e32dd)
# Zscore of 3
# NEWDATA USING Zscore
![image](https://github.com/chaitanya18c/ODD2023---Datascience---Ex-02/assets/119392724/cb6f0b25-417b-4e42-83a1-3bcdf8b91923)
# OUTLIERS
![image](https://github.com/chaitanya18c/ODD2023---Datascience---Ex-02/assets/119392724/fb70982f-a5e6-4923-b4b3-812680dffa3c)
# newdata2.shape
![image](https://github.com/chaitanya18c/ODD2023---Datascience---Ex-02/assets/119392724/8910987a-bbb9-4766-a97d-93ecfb340707)
# BOXPLOT AFTER REMOVING OUTLIERS USING Zscore
![image](https://github.com/chaitanya18c/ODD2023---Datascience---Ex-02/assets/119392724/392a6c67-45bd-4189-8388-c362a9175bbc)
# height_weight.csv
![image](https://github.com/chaitanya18c/ODD2023---Datascience---Ex-02/assets/119392724/64bfb706-69c0-4ef2-8d8d-a4bd4511f7ae)
# dataset.describe()
![image](https://github.com/chaitanya18c/ODD2023---Datascience---Ex-02/assets/119392724/9f6b6333-21ea-4f38-90fa-2cb54fb35cb1)
# dataset.info()
![image](https://github.com/chaitanya18c/ODD2023---Datascience---Ex-02/assets/119392724/f574b285-6a6f-487e-a1ec-e5f34032a881)
# BOXPLOT BEFORE REMOVING OUTLIERS
![image](https://github.com/chaitanya18c/ODD2023---Datascience---Ex-02/assets/119392724/f8658740-e9dc-43b8-9bf3-7c4954edf07f)
# HEIGHT OUTLIERS
![image](https://github.com/chaitanya18c/ODD2023---Datascience---Ex-02/assets/119392724/b7b83df5-4603-4a4c-8598-ca465f319e7c)
# DATASET AFTER REMOVING HEIGHT OUTLIERS
![image](https://github.com/chaitanya18c/ODD2023---Datascience---Ex-02/assets/119392724/2915f0ce-c637-48a3-9076-54f129d9f46d)
# BOXPLOT AFTER REMOVING HEIGHT OUTLIERS
![image](https://github.com/chaitanya18c/ODD2023---Datascience---Ex-02/assets/119392724/a18ff35c-11dc-4e34-bfe2-c5196d620e64)
# WEIGHT OUTLIERS
![image](https://github.com/chaitanya18c/ODD2023---Datascience---Ex-02/assets/119392724/2264812c-3fd1-4d99-8cc8-de8c8ee137fd)
# DATASET AFTER REMOVING WEIGHT OUTLIERS
![image](https://github.com/chaitanya18c/ODD2023---Datascience---Ex-02/assets/119392724/de9092f0-ee7c-4ad5-9fe9-f7c52834222d)
# BOXPLOT AFTER REMOVING WEIGHT OUTLIERS
![image](https://github.com/chaitanya18c/ODD2023---Datascience---Ex-02/assets/119392724/1be226c9-8b6f-498b-b2a4-aa7189e49fc8)
# RESULT:
The given datasets are read and outliers are detected and are removed using IQR and z-score methods.
