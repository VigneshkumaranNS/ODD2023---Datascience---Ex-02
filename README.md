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
![image](https://github.com/VigneshkumaranNS/ODD2023---Datascience---Ex-02/assets/119484483/66d877b0-07fd-46e4-948a-4932c7755cbd)
# df.describe():
![image]![img2](https://github.com/VigneshkumaranNS/ODD2023---Datascience---Ex-02/assets/119484483/17710447-9ca1-447a-b83f-d8d4638728db)
# df.info():
![img3](https://github.com/VigneshkumaranNS/ODD2023---Datascience---Ex-02/assets/119484483/12f76ddc-1e03-4f47-b8cd-2d9e231358e8)

# df.shape
![img4](https://github.com/VigneshkumaranNS/ODD2023---Datascience---Ex-02/assets/119484483/c58aa1e6-6e7d-4de4-8ba9-ae74413f68e4)

# BOXPLOT BEFORE REMOVING OUTLIERS
![img5](https://github.com/VigneshkumaranNS/ODD2023---Datascience---Ex-02/assets/119484483/60f8a070-6917-41ea-89eb-70a2eba74eed)

# NEWDATA USING IQR
![img6](https://github.com/VigneshkumaranNS/ODD2023---Datascience---Ex-02/assets/119484483/3d0a9508-2b2f-47de-92e3-fd17a2926017)

# OUTLIERS
![img7](https://github.com/VigneshkumaranNS/ODD2023---Datascience---Ex-02/assets/119484483/c300b3cc-3bc7-46c6-8162-90f91985a389)

# newdata.shape
![img8](https://github.com/VigneshkumaranNS/ODD2023---Datascience---Ex-02/assets/119484483/0852fce1-852e-4ff0-ac40-0a5a128b7e0f)
# BOXPLOT AFTER REMOVING OUTLIERS USING IQR
![img9](https://github.com/VigneshkumaranNS/ODD2023---Datascience---Ex-02/assets/119484483/0c04cc9a-3222-4435-bff4-b3b8dfc05d9c)
# Zscore of 3
# NEWDATA USING Zscore
![img10](https://github.com/VigneshkumaranNS/ODD2023---Datascience---Ex-02/assets/119484483/54af52b9-95f0-49bc-9107-c4190455d146)

# OUTLIERS
![img11](https://github.com/VigneshkumaranNS/ODD2023---Datascience---Ex-02/assets/119484483/7d654a17-de36-4d3e-86a1-ca95cf6ec36d)
# newdata2.shape
![img12](https://github.com/VigneshkumaranNS/ODD2023---Datascience---Ex-02/assets/119484483/52af869b-69d9-48b1-b76b-3ecf44958e73)
# BOXPLOT AFTER REMOVING OUTLIERS USING Zscore
![img13](https://github.com/VigneshkumaranNS/ODD2023---Datascience---Ex-02/assets/119484483/566eebbe-bedd-49ab-ba4c-b2c95fc7efbc)
# height_weight.csv
![img14](https://github.com/VigneshkumaranNS/ODD2023---Datascience---Ex-02/assets/119484483/ab20e8c6-2347-4bd1-b1bb-11434233d1fe)
# dataset.describe()
![img15](https://github.com/VigneshkumaranNS/ODD2023---Datascience---Ex-02/assets/119484483/d824665a-b755-42d2-92c7-47c836161a98)
# dataset.info()
![img16](https://github.com/VigneshkumaranNS/ODD2023---Datascience---Ex-02/assets/119484483/23b5384e-6ac6-47a5-9038-0bedd64a6b9e)
# BOXPLOT BEFORE REMOVING OUTLIERS
![img17](https://github.com/VigneshkumaranNS/ODD2023---Datascience---Ex-02/assets/119484483/582fc63c-a46f-4450-9ce7-b7d3f07681a3)
# HEIGHT OUTLIERS
![img18](https://github.com/VigneshkumaranNS/ODD2023---Datascience---Ex-02/assets/119484483/e2a85896-1ffd-43f9-9d93-fe4530012be0)
# DATASET AFTER REMOVING HEIGHT OUTLIERS
![img19](https://github.com/VigneshkumaranNS/ODD2023---Datascience---Ex-02/assets/119484483/cc2bbf53-bd97-4e40-b709-e91e38db3d12)
# BOXPLOT AFTER REMOVING HEIGHT OUTLIERS
![img20](https://github.com/VigneshkumaranNS/ODD2023---Datascience---Ex-02/assets/119484483/1cba984c-414b-47f7-bb88-bc9643b60802)
# WEIGHT OUTLIERS
![img21](https://github.com/VigneshkumaranNS/ODD2023---Datascience---Ex-02/assets/119484483/7526a8c7-edf3-4b5d-a600-2da57bc3f652)
# DATASET AFTER REMOVING WEIGHT OUTLIERS
![img22](https://github.com/VigneshkumaranNS/ODD2023---Datascience---Ex-02/assets/119484483/d1bd6b2d-9832-4381-b7fc-9160b3554976)
# BOXPLOT AFTER REMOVING WEIGHT OUTLIERS
![img23](https://github.com/VigneshkumaranNS/ODD2023---Datascience---Ex-02/assets/119484483/eb1beb07-e875-4853-9e60-4a7f3c43a723)
# RESULT:
The given datasets are read and outliers are detected and are removed using IQR and z-score methods.
