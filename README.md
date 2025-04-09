## NAME: SUJITHRA .K
## REGISTER NUMBER :212223040212
## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation

# 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:

import pandas as pd
import numpy as np
from scipy import stats

df=pd.read_csv("C:\\Users\\admin\Downloads\\data.csv")
df

<img width="576" alt="426145488-14f9d2fc-e4fa-43ab-9dd7-4456ea9cf500" src="https://github.com/user-attachments/assets/f802919b-9690-4807-abe0-c0c99ca42f73" />

from sklearn.preprocessing import LabelEncoder, OrdinalEncoder
climate=['Cold','Warm','Hot','Very Hot']
ele=OrdinalEncoder(categories=[climate])
ele.fit_transform(df[['Ord_1']])


<img width="576" alt="426145427-e0b1cdda-ca28-472e-bd09-4d0f676be59b" src="https://github.com/user-attachments/assets/eb2668d7-3d8c-4c10-b195-9300dbb4e5fb" />

df['bo2']=ele.fit_transform(df[['Ord_1']])
df

<img width="576" alt="426145365-40b1b90c-d045-4563-a574-954da6c0c757" src="https://github.com/user-attachments/assets/41be00f0-8fe3-4b53-90e9-c6eff88220bf" />

le=LabelEncoder()
df2=df.copy()
df2['Ord_2']=le.fit_transform(df2['Ord_2'])
df2


<img width="576" alt="426145312-ee0f6874-ce17-4c18-b968-b177b4a7a40e" src="https://github.com/user-attachments/assets/45965669-6e30-4f11-81ae-1c740d0f4ce8" />

from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder()
df3=df.copy()
enc=pd.DataFrame(ohe.fit_transform(df[['City']]))
df2=pd.concat([enc,df3],axis=1)
df2


<img width="690" alt="426145268-222e9931-614b-4b75-90b6-8c7d634af398" src="https://github.com/user-attachments/assets/16a8bb57-94e6-4dc3-ba1e-32158956c225" />

pd.get_dummies(df,columns=['City'])

<img width="794" alt="426145224-ce3174c3-540b-450d-9a1e-c38c6ce459e7" src="https://github.com/user-attachments/assets/31ea6393-bfce-4579-bcd2-c51ca9c4b717" />

!pip install category_encoders
from category_encoders import BinaryEncoder
dfd=pd.read_csv("/content/data.csv")
dfd

<img width="576" alt="426145172-3a7aff40-fa76-4ce5-a1dc-b7077be314d8" src="https://github.com/user-attachments/assets/59744d66-1eee-4b3e-9f42-7308b071d7c2" />

be=BinaryEncoder()
nd=be.fit_transform(dfd['Ord_2'])
df=pd.concat([dfd,nd],axis=1)
df

<img width="576" alt="426145131-ef1dfd0a-2766-4a99-82ab-e89e53dbf42f" src="https://github.com/user-attachments/assets/9cfe4173-0398-4920-9163-a484615c7c45" />

from category_encoders import TargetEncoder
te=TargetEncoder()
cc=df.copy()
new=te.fit_transform(X=cc['City'],y=cc['Target'])
pd.concat([cc,new],axis=1)

<img width="687" alt="426145100-80dfbdb3-653d-4aed-82a3-91b59f4b47ac" src="https://github.com/user-attachments/assets/494c8a91-ca34-4af2-a415-0443b3a8991a" />

vf=pd.read_csv("/content/Data_to_Transform.csv")
vf

<img width="711" alt="426145034-3e9ae0a7-4343-40bf-a397-625ed0a82b9e" src="https://github.com/user-attachments/assets/aba12f88-29f2-432a-8968-74d13be84f45" />

vf.skew()


<img width="576" alt="426144997-66b98a01-377a-4a1c-bedf-b3816d967604" src="https://github.com/user-attachments/assets/4c6a0af5-e098-46ce-899b-b4c07b528da9" />

np.log(vf["Highly Positive Skew"])


<img width="576" alt="426144927-7029bd4f-0363-447b-8d61-6549b912bd16" src="https://github.com/user-attachments/assets/37bc52e1-746e-4ed8-94fd-ee5946823921" />

np.reciprocal(vf["Highly Positive Skew"])

<img width="576" alt="426144890-527c808d-13fc-4002-84b9-85fef4ecb09d" src="https://github.com/user-attachments/assets/334c81be-d77a-418e-966c-f17899136a73" />

np.reciprocal(vf["Moderate Positive Skew"])

<img width="576" alt="426144838-c9c2ce92-8ecd-409b-bb1a-445e10d21652" src="https://github.com/user-attachments/assets/e57331a0-88b5-474a-8f64-0f1f65d36615" />

np.square(vf["Highly Positive Skew"])

<img width="576" alt="426144784-80586186-973c-4409-8d6d-988de121cd23" src="https://github.com/user-attachments/assets/00c0a6d6-e532-4410-a346-68e7faa48ecd" />

vf["Highly Positive Skew"],parameters=stats.boxcox(vf["Highly Positive Skew"])
vf

<img width="808" alt="426144742-b8ce5a76-03bc-48fe-9896-697541f9c0b7" src="https://github.com/user-attachments/assets/db8f6fbc-e8a5-446a-80d0-b8e32edf7c9e" />

vf["Moderate Negative Skew_teojohnson"],parameters=stats.yeojohnson(vf["Moderate Negative Skew"])
vf

<img width="618" alt="426144662-53776c9a-691c-4918-ab37-53baa8d2aa5b" src="https://github.com/user-attachments/assets/e326c57d-36e6-42ce-be45-213804330edd" />

from sklearn.preprocessing import QuantileTransformer
Qt=QuantileTransformer(output_distribution='normal')
vf["Moderate Negative Skew_1"]=Qt.fit_transform(vf[["Moderate Negative Skew"]])
vf

<img width="933" alt="426144578-f685f7b0-23c9-4d8e-bf1a-379e3dc72b1b" src="https://github.com/user-attachments/assets/0ebfe824-1abe-4136-b13a-a6fcaf8fa70d" />

import matplotlib.pyplot as plt
import seaborn as sna 
import statsmodels.api as sm
import scipy.stats as stats

sm.qqplot(vf["Moderate Negative Skew"],line='45')
plt.show()

<img width="576" alt="426144540-39139240-ce23-4b4a-beb4-8eefb3aeeda9" src="https://github.com/user-attachments/assets/69d66074-6b12-42cf-8155-c1cd892cd492" />

sm.qqplot(vf["Moderate Negative Skew_1"],line='45')
plt.show()

<img width="576" alt="426144429-c5a58485-a10f-4833-9f94-0bd9ed494f0d" src="https://github.com/user-attachments/assets/819e9a46-dc7f-4583-b79c-59a10601103e" />

vf["Highly Negative Skew_1"]=Qt.fit_transform(vf[["Highly Negative Skew"]])
sm.qqplot(vf["Highly Negative Skew"],line='45')
plt.show()

<img width="576" alt="426144396-39d2f3bf-7c2d-435a-bc9e-c831f16e7f87" src="https://github.com/user-attachments/assets/4daa8ddb-32f2-4dd3-88b3-818b1907141f" />

sm.qqplot(vf["Highly Negative Skew_1"],line='45')
plt.show()


<img width="576" alt="426131363-52e3fb2d-2df6-4d9a-9b95-ca954333c770" src="https://github.com/user-attachments/assets/3f01b3cd-7874-47b8-b5ca-bebc3c8b91fe" />

sm.qqplot(np.reciprocal(vf["Moderate Negative Skew_1"]),line='45')
plt.show()

<img width="576" alt="426130986-303d5376-27bd-4657-8371-3270deac285a" src="https://github.com/user-attachments/assets/6e2ca1eb-de59-4fc0-8e99-6769abeeb900" />

sm.qqplot(np.abs(vf["Highly Negative Skew_1"]),line='45')
plt.show()


<img width="576" alt="426152941-3523f1a9-46bf-43fd-aeaa-0ab004c6f239" src="https://github.com/user-attachments/assets/14ac3282-f458-4e9a-84a2-d396872b29d8" />

sm.qqplot(np.log(vf["Highly Negative Skew_1"]),line='45')
plt.show()

<img width="628" alt="426130920-3f72ce95-4772-4b4e-9d76-970cccc2f45e" src="https://github.com/user-attachments/assets/8233092a-ce35-44d9-a83e-e4fe4c9e5301" />

sm.qqplot(np.sqrt(vf["Highly Negative Skew_1"]),line='45')
plt.show()


<img width="576" alt="426152851-605aea61-644d-4c72-9be8-5094b08ef02d" src="https://github.com/user-attachments/assets/a2910553-5e07-4ad4-a93a-6e5d57d352ac" />

pd.concat([cc,new],axis=1)

<img width="576" alt="426130711-23442958-7834-4b2e-aa24-193a96448ace" src="https://github.com/user-attachments/assets/a8e4ae0b-f0c6-41e9-b1f1-5699e6237382" />

       
# RESULT:
Thus the given data, Feature Encoding, Transformation process and save the data to a file was successfully executed.


       
