# NAME:KISHORE.G
# REG.NO: 212223040099

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
df = pd.read_csv("SAMPLEIDS (1).csv")
df
```
<img width="884" height="678" alt="image" src="https://github.com/user-attachments/assets/5f61b015-fbd9-4465-9868-c9f00760c5c4" />

```
df.isnull().sum()
```

<img width="292" height="272" alt="image" src="https://github.com/user-attachments/assets/f0e874e8-71fc-464a-97ee-26cd9b789d58" />

```
df.isnull().any()
```

<img width="513" height="297" alt="image" src="https://github.com/user-attachments/assets/03100619-135f-4daf-96e2-4cd8bd6ce643" />

```
df.dropna()
```
<img width="1100" height="500" alt="image" src="https://github.com/user-attachments/assets/4ba8f882-ea09-4ead-a82e-6b9e520a3b59" />

```
df.fillna()
```
<img width="962" height="376" alt="image" src="https://github.com/user-attachments/assets/352c599d-a97e-4143-9224-b45e8da14793" />

```
df.fillna(method = 'ffill')
```
<img width="820" height="670" alt="image" src="https://github.com/user-attachments/assets/0599d9ad-726e-47d1-90d1-aef91e0a0122" />

```
df.fillna(method = 'bfill')
```
<img width="829" height="663" alt="image" src="https://github.com/user-attachments/assets/bf6fc9c5-d776-45b9-bd31-9e5475f1f9c7" />

# InterQuartile range:

```
import pandas as pd
ris = pd.read_csv("iris.csv")
ris
```

<img width="994" height="681" alt="image" src="https://github.com/user-attachments/assets/b0646f2e-06bf-4a46-b4b0-1c1f185c9137" />

```
ris.describe()
```

<img width="579" height="289" alt="image" src="https://github.com/user-attachments/assets/156125aa-0415-494e-8386-be8044aa09b0" />

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ris)
```
<img width="748" height="530" alt="image" src="https://github.com/user-attachments/assets/5bb0d03c-e75b-491c-9b77-cb7cf3dbc20e" />

```
c1=ris.sepal_width.quantile(0.25)
c3=ris.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
<img width="593" height="131" alt="image" src="https://github.com/user-attachments/assets/ac85b217-efce-4bef-b0b5-eb01ba97987b" />

```
rid=ris[((ris.sepal_width<(c1-1.5*iq))|(ris.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```

<img width="473" height="121" alt="image" src="https://github.com/user-attachments/assets/e4931632-d0f0-48a7-b267-28a56828bda7" />

```
 delid=ris[~((ris.sepal_width<(c1-1.5*iq))|(ris.sepal_width>(c3+1.5*iq)))]
 delid
 ```
<img width="724" height="394" alt="image" src="https://github.com/user-attachments/assets/3c259a05-55ff-4add-b143-28ea6e71a472" />

```
sns.boxplot(x='sepal_width',data=delid)
```

<img width="697" height="543" alt="image" src="https://github.com/user-attachments/assets/3ad7db22-41c9-48fd-9c06-ba1b7e48f661" />

```
import matplotlib.pyplot as plt 
import pandas as pd
import numpy as np
import scipy.stats as stats
ds = pd.read_csv("heights.csv")
ds
```
<img width="231" height="471" alt="image" src="https://github.com/user-attachments/assets/fb136ca8-6c6c-4865-a449-0feb68154c47" />

```
q1 = ds['height'].quantile(0.25)
q2 = ds['height'].quantile(0.5)
q3 = ds['height'].quantile(0.75)
iqr =q3 - q1
iqr
```

<img width="713" height="168" alt="image" src="https://github.com/user-attachments/assets/5fdfce06-12ad-483d-9f4e-3b257b1a4b77" />

```
low = q1- 1.5*iqr
low
high = q3+ 1.5*iqr
high
```
<img width="544" height="136" alt="image" src="https://github.com/user-attachments/assets/40e2750a-f73c-4028-abc3-485145252f91" />

```
 ds1 = ds[((ds['height'] >=low)& (ds['height'] <=high))]
 ds1
```

<img width="664" height="424" alt="image" src="https://github.com/user-attachments/assets/fdc6a7cc-ca80-4899-b2c4-2522b28ae8ef" />



```
import numpy as np
import scipy.stats as stats
z = np.abs(stats.zscore(ds['height']))
z
```
<img width="533" height="306" alt="image" src="https://github.com/user-attachments/assets/c962e0d4-3b3e-448f-90a2-e09599a316bc" />

```
ds1 = ds[z<3]
ds1
```

<img width="558" height="495" alt="image" src="https://github.com/user-attachments/assets/18ade4f7-0d9c-4221-8ba9-366bec0e4a2f" />



# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z -score method.
