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
```
import pandas as pd
import numpy as np
from scipy import stats
df = pd.read_csv("C:\\Users\\admin\\Downloads\\data (1).csv")
print(df)
```
<img width="701" height="285" alt="image" src="https://github.com/user-attachments/assets/77cc9f4c-e4ca-4ab0-8434-6c8e4b01ad58" />
```
from sklearn.preprocessing import OrdinalEncoder,LabelEncoder
climate = ['Cold','Warm','Hot','Very Hot']
ele = OrdinalEncoder(categories=[climate])
ele.fit_transform(df[["Ord_1"]])
```
<img width="470" height="236" alt="image" src="https://github.com/user-attachments/assets/cd560414-b1db-4062-9c2a-cce14b5aff85" />
```
df['bo2'] = ele.fit_transform(df[["Ord_1"]])
df
```
<img width="718" height="398" alt="image" src="https://github.com/user-attachments/assets/27d34a9c-a0ec-4421-8e47-c55b38a03f3d" />
```
le = LabelEncoder()
df2 = df.copy()
df2['Ord_2'] = le.fit_transform(df2['Ord_2'])
df2
```
<img width="581" height="371" alt="image" src="https://github.com/user-attachments/assets/ea055ca8-fd50-4fc0-bdfa-434e0dd253ce" />
```
df2['Ord_2'] = le.fit_transform(df2['Ord_2'])
df2
```
<img width="597" height="387" alt="image" src="https://github.com/user-attachments/assets/3853aedb-51a6-4cb9-a7ab-b0c7d6423f9d" />

```
from sklearn.preprocessing import OneHotEncoder
ohe = OneHotEncoder()
df3 = df.copy()
enc = pd.DataFrame(ohe.fit_transform(df2[["City"]]))
df2 = pd.concat([enc,df3],axis = 1)
df2
```
<img width="652" height="372" alt="image" src="https://github.com/user-attachments/assets/75f2a067-9615-4915-bdf3-90b06b2c2100" />
```
pd.get_dummies(df,columns=['City'])
```
<img width="951" height="396" alt="image" src="https://github.com/user-attachments/assets/054c6da6-1d7d-4d56-ab47-41acb921e522" />
```
from category_encoders import BinaryEncoder
df = pd.read_csv('data.csv')
df
```

# RESULT:
       # INCLUDE YOUR RESULT HERE

       
