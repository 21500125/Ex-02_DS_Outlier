# Ex-02_DS_Outlier
## AIM:
To read the given data and detect outliers and remove them.

## EXPLANATION:
An outlier is an observation that lies an abnormal distance from other values in a random sample from a population.These outliers can be removed using Z-score method and IQR-score method.Some outliers can be useful too, like detecting the rare disease in the population.

## ALGORITHM:
STEP 1:
Read the given data.

STEP 2:
Apply boxplot to analyze the outliers of given data.

STEP 3:
Use Z-score method to remove outliers.

STEP 4:
Use IQR score method to remove outliers that lies below or above the range

## CODE:
```
import pandas as pd
df=pd.read_csv("weight.csv")
df
df.drop("Gender",axis=1,inplace=True)
df.boxplot()
from scipy import stats
import numpy as np
z=np.abs(stats.zscore(df))
z
df1=df.copy()
df1=df1[(z<3).all(axis=1)]
df1
df1.boxplot()
df2=df.copy()
q1=df2.quantile(0.25)
q3=df2.quantile(0.75)
IQR=q3-q1
df2_new=df2[((df2>=q1-1.5*IQR)&(df2<=q3+1.5*IQR)).all(axis=1)]
df2_new.boxplot()
df2_new
```
# OUTPUT:
## READING THE DATA
![C1](https://user-images.githubusercontent.com/94219582/161584321-fd825f82-6171-4a26-a928-76477aeb5a32.PNG)
## BOXPLOT METHOD TO REPRESENT OUTLIERS
![C2](https://user-images.githubusercontent.com/94219582/161584602-d45d51bd-39a2-4a2b-91fb-22a5a489d290.PNG)
## REMOVING OUTLIERS USING Z-SCORE METHOD
![C3](https://user-images.githubusercontent.com/94219582/161584855-83cbf031-b70b-4934-8aec-204ed0707674.PNG)
![C4](https://user-images.githubusercontent.com/94219582/161585059-01cf6d4b-1296-4583-8f0d-2cc293314eb5.PNG)
![image](https://user-images.githubusercontent.com/94219582/161585849-7533f023-0d39-41ed-beee-eaa2faf24519.png)
## REMOVING OUTLIERS USING IQR METHOD
![C6](https://user-images.githubusercontent.com/94219582/161586331-6ea91be7-b1aa-4d6f-bde6-712eea20c9a7.PNG)
![image](https://user-images.githubusercontent.com/94219582/161586597-55dc24ed-1b50-4875-ae73-02bf57f50efe.png)
# RESULT:
Hence the given data is read and the outliers are removed.






