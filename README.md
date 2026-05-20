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

<img width="571" height="388" alt="image" src="https://github.com/user-attachments/assets/f2dd5ddd-bb0a-43e1-ba9a-5f929c4a5f15" />

```
be = BinaryEncoder()
nd = be.fit_transform(df['Ord_2'])
df
```

<img width="593" height="366" alt="image" src="https://github.com/user-attachments/assets/5d4f806a-6a90-4a67-956b-9b56a1449963" />

```
from category_encoders import TargetEncoder
te = TargetEncoder()
CC = df.copy()
new = te.fit_transform(CC["City"],y=CC["Target"])
CC = pd.concat([CC,new],axis = 1)
CC
```

<img width="595" height="383" alt="image" src="https://github.com/user-attachments/assets/21362509-67a5-4c9a-af1d-d1dedb8038d3" />

```
if 'City' in CC.columns:
    CC = CC.drop('City', axis=1)
new = te.fit_transform(X = df["City"],y=df["Target"])
CC = pd.concat([CC.reset_index(drop=True),new.reset_index(drop=True)],axis = 1)
CC
```

<img width="642" height="401" alt="image" src="https://github.com/user-attachments/assets/902ecf30-f841-45cc-81f7-83d9ce5c1ea7" />

```
df = pd.read_csv('Data_to_Transform.csv')
df
```

<img width="922" height="461" alt="image" src="https://github.com/user-attachments/assets/ddbd33aa-293a-404f-972e-84552cf614a5" />

```
df.skew()
```

<img width="396" height="130" alt="image" src="https://github.com/user-attachments/assets/a59d3cbf-ec2c-4f9f-8985-680b779e3195" />

```
np.log(df["Highly Positive Skew"])
```

<img width="612" height="276" alt="image" src="https://github.com/user-attachments/assets/f937ed45-26ed-4bd3-a10b-c53cc7414ed3" />

```
np.reciprocal(df["Moderate Positive Skew"])
```

<img width="746" height="287" alt="image" src="https://github.com/user-attachments/assets/b63d3130-b6b5-4600-9696-56217a67793b" />

```
np.sqrt(df["Highly Positive Skew"])
```

<img width="617" height="275" alt="image" src="https://github.com/user-attachments/assets/cf9bd5d7-8551-4f7b-8ed7-a8ae43cfe759" />

```
np.square(df["Highly Positive Skew"])
```

<img width="737" height="270" alt="image" src="https://github.com/user-attachments/assets/ab5a61e1-ff52-444d-8f5e-09707e8ce7c0" />

```
df["Highly Positive Skew_boxcox"], parameters = stats.boxcox(df["Highly Positive Skew"])
df
```

<img width="1048" height="458" alt="image" src="https://github.com/user-attachments/assets/c9ac6295-7010-4ca1-8fe9-7043fea4afaa" />

```
df["Moderate Negative Skew_yeojohnson"], parameters = stats.yeojohnson(df["Moderate Negative Skew"])
df
```

<img width="1272" height="457" alt="image" src="https://github.com/user-attachments/assets/a0b5743e-3652-4edd-a463-74d680e3e809" />

```
from sklearn.preprocessing import QuantileTransformer
qt = QuantileTransformer(output_distribution = 'normal')
df["Moderate Negative Skew_1"] = qt.fit_transform(df[["Moderate Negative Skew"]])
df
```

<img width="1247" height="470" alt="image" src="https://github.com/user-attachments/assets/ddea599c-8b2e-4ad1-81f6-0d924836821f" />

```
import matplotlib.pyplot as plt
import seaborn as sns
import statsmodels.api as sm
import scipy.stats as stats
sm.qqplot(df["Moderate Negative Skew"],line = '45')
plt.show()
```

<img width="855" height="556" alt="image" src="https://github.com/user-attachments/assets/4cd5b2ec-c080-4b9d-8709-6f256438ebc4" />

```
sm.qqplot(df["Moderate Negative Skew_1"],line = '45')
plt.show()
```

<img width="857" height="562" alt="image" src="https://github.com/user-attachments/assets/6a6533af-b97a-41d6-b36d-75b77c8b0015" />

```
df["Highly Negative Skew_1"] = qt.fit_transform(df[["Highly Negative Skew"]])
sm.qqplot(df["Highly Negative Skew"],line = '45')
plt.show()
```

<img width="891" height="522" alt="image" src="https://github.com/user-attachments/assets/9c6afaa8-6d87-445c-8682-93b4aa3f84e5" />

```
sm.qqplot(np.reciprocal(df["Moderate Negative Skew_1"]),line = '45')
plt.show()

```

<img width="888" height="552" alt="image" src="https://github.com/user-attachments/assets/d5391c49-00de-4f82-8aff-eec8a0b5d9c7" />

```
sm.qqplot(df["Highly Negative Skew_1"],line = '45')
plt.show()
```

<img width="862" height="561" alt="image" src="https://github.com/user-attachments/assets/063a617b-8fda-4ae3-af97-ca32ddeb77fb" />

```
sm.qqplot(np.abs(df["Highly Negative Skew_1"]),line = '45')
plt.show()
```

<img width="897" height="577" alt="image" src="https://github.com/user-attachments/assets/21cebfe5-c6b4-4bec-bb90-7f887f930318" />

```
sm.qqplot(np.log(df["Highly Negative Skew_1"]),line = '45')
plt.show()
```

<img width="792" height="537" alt="image" src="https://github.com/user-attachments/assets/aff79377-23d8-4efc-be35-8403a9a3d7a1" />

```
sm.qqplot(np.sqrt(df["Moderate Negative Skew_1"]),line='45')
plt.show()
```

<img width="848" height="540" alt="image" src="https://github.com/user-attachments/assets/7c238641-6948-401a-a8d5-b9e9985efbe8" />

```
pd.concat([CC,new],axis = 1)
```

<img width="613" height="395" alt="image" src="https://github.com/user-attachments/assets/1a4a6952-19d2-4497-91da-59a332c20d4b" />

# RESULT:
   Thus, we have successfully performed Feature Encoding and Transformation process and saved the data to a file.

       
