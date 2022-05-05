# EX-05-Feature-Generation


## AIM
To read the given data and perform Feature Generation process and save the data to a file. 

# Explanation
Feature Generation (also known as feature construction, feature extraction or feature engineering) is the process of transforming features into new features that better relate to the target.
 

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature Generation techniques to all the feature of the data set
### STEP 4
Save the data to the file


# CODE
Program Developed: Yashaswi.Mitta
Register number:212221230062
# Data.csv :
import pandas as pd
df=pd.read_csv("data.csv")
df

#feature generation
import category_encoders as ce
be=ce.BinaryEncoder()
ndf=be.fit_transform(df["bin_1"])
df["bin_1"] = be.fit_transform(df["bin_1"])
ndf

ndf2=be.fit_transform(df["bin_2"])
df["bin_2"] = be.fit_transform(df["bin_2"])
ndf2

df1=df.copy()
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder,OneHotEncoder
import category_encoders as ce
be=ce.BinaryEncoder()
ohe=OneHotEncoder(sparse=False)
le=LabelEncoder()
oe=OrdinalEncoder()


df1["City"] = ohe.fit_transform(df1[["City"]])

temp=['Cold','Warm','Hot','Very Hot']
oe1=OrdinalEncoder(categories=[temp])
df1['Ord_1'] = oe1.fit_transform(df1[["Ord_1"]])

edu=['High School','Diploma','Bachelors','Masters','PhD']
oe2=OrdinalEncoder(categories=[edu])
df1['Ord_2']= oe2.fit_transform(df1[["Ord_2"]])
df1

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df2=pd.DataFrame(sc.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df2

from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df3=pd.DataFrame(sc1.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df3

from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df4=pd.DataFrame(sc2.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df4

from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df5=pd.DataFrame(sc3.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df5
# Encoding.csv :
import pandas as pd
df=pd.read_csv("Encoding Data.csv")
df

#feature generation
import category_encoders as ce
be=ce.BinaryEncoder()
ndf=be.fit_transform(df["bin_1"])
df["bin_1"] = be.fit_transform(df["bin_1"])
ndf

ndf2=be.fit_transform(df["bin_2"])
df["bin_2"] = be.fit_transform(df["bin_2"])
ndf2

df1=df.copy()
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
le=LabelEncoder()
oe=OrdinalEncoder()

df1["nom_0"] = oe.fit_transform(df1[["nom_0"]])
temp=['Cold','Warm','Hot']
oe2=OrdinalEncoder(categories=[temp])
df1['ord_2'] = oe2.fit_transform(df1[['ord_2']])

df1

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df0=pd.DataFrame(sc.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df0

from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df2=pd.DataFrame(sc1.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df2

from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df3=pd.DataFrame(sc2.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df3

from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df4=pd.DataFrame(sc3.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df4
# Titanic.csv :
import pandas as pd
df=pd.read_csv("titanic_dataset.csv")
df

#removing unwanted data
df.drop("Name",axis=1,inplace=True)
df.drop("Ticket",axis=1,inplace=True)
df.drop("Cabin",axis=1,inplace=True)

#data cleaning
df.isnull().sum()

df["Age"]=df["Age"].fillna(df["Age"].median())
df["Embarked"]=df["Embarked"].fillna(df["Embarked"].mode()[0])

df.isnull().sum()

df

#feature encoding
from category_encoders import BinaryEncoder
be=BinaryEncoder()
df["Sex"]=be.fit_transform(df[["Sex"]])
ndf=be.fit_transform(df["Sex"])
ndf

df1=df.copy()
from sklearn.preprocessing import LabelEncoder, OrdinalEncoder
embark=['S','C','Q']
e1=OrdinalEncoder(categories=[embark])
df1['Embarked'] = e1.fit_transform(df[['Embarked']])
df1

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df2=pd.DataFrame(sc.fit_transform(df1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df2

from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df3=pd.DataFrame(sc1.fit_transform(df1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df3

from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df4=pd.DataFrame(sc2.fit_transform(df1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df4

from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df5=pd.DataFrame(sc3.fit_transform(df1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df5


# OUPUT
# Data.csv :
![image](https://user-images.githubusercontent.com/94619247/166960042-b88ac4ed-529e-4130-bedd-94088cf1f44a.png)
![image](https://user-images.githubusercontent.com/94619247/166960089-c5dd6495-16cd-46d3-b59e-526767decfe7.png)
![image](https://user-images.githubusercontent.com/94619247/166960115-41ecebad-fa43-45dd-8cf7-27c999560cf1.png)
![image](https://user-images.githubusercontent.com/94619247/166960146-23292023-0b35-4383-9d56-e0283557a455.png)
![image](https://user-images.githubusercontent.com/94619247/166960167-6985fd14-b494-470b-aa49-f727c916345e.png)
![image](https://user-images.githubusercontent.com/94619247/166960201-58f65e3a-16ab-4ab8-bfbe-55b2f478db53.png)
![image](https://user-images.githubusercontent.com/94619247/166960246-e8f23e59-f899-4ee7-8611-140d34cea413.png)
![image](https://user-images.githubusercontent.com/94619247/166960291-dc360c40-7541-4397-8edf-ab305bf19d5c.png)
# Encoding.csv :
![image](https://user-images.githubusercontent.com/94619247/166960378-b34e7bd0-c554-4ac5-9cfc-d75f6f281672.png)
![image](https://user-images.githubusercontent.com/94619247/166960411-eae667f8-3329-4148-9c31-b77229406dab.png)
![image](https://user-images.githubusercontent.com/94619247/166960440-4dabb22e-9c52-48f6-9610-cc066a129324.png)
![image](https://user-images.githubusercontent.com/94619247/166960481-31d47a57-917c-4c46-a883-95bf53efd127.png)
![image](https://user-images.githubusercontent.com/94619247/166960510-a15ba0a4-c1a1-4438-a492-bd426eb8a744.png)
![image](https://user-images.githubusercontent.com/94619247/166960551-ba105279-ad59-4140-854a-e957a13fa533.png)
![image](https://user-images.githubusercontent.com/94619247/166960597-f912bcbb-b045-48e0-8d90-1fe89b9f6cee.png)
![image](https://user-images.githubusercontent.com/94619247/166960773-9b8485db-3d4f-49bb-b149-2de8ea51146a.png)
# Titanic.csv :
![image](https://user-images.githubusercontent.com/94619247/166960864-3b394974-b6d0-4ae2-b399-fe50ec099b38.png)
![image](https://user-images.githubusercontent.com/94619247/166960913-c8649297-cbb4-4bf8-8823-312f9cebd2a3.png)
![image](https://user-images.githubusercontent.com/94619247/166960933-e65f91de-47c8-4a8e-9763-d2a15d376f04.png)
![image](https://user-images.githubusercontent.com/94619247/166960979-9dfe1044-c3c2-490a-966f-d4c6e7ae66de.png)
![image](https://user-images.githubusercontent.com/94619247/166961024-f8e248c9-6c12-4280-a41d-16c637fdf4fc.png)
![image](https://user-images.githubusercontent.com/94619247/166961065-b9519462-8008-498d-a052-c27cdcfa7bff.png)
![image](https://user-images.githubusercontent.com/94619247/166961158-5f16adb0-d46d-4662-b4a3-b436d737e3a3.png)
![image](https://user-images.githubusercontent.com/94619247/166961198-17652048-c5be-4eeb-8456-19eb6210beaf.png)
![image](https://user-images.githubusercontent.com/94619247/166961291-324175c6-120d-4ef5-8fa6-7541ed5c8f5f.png)
![image](https://user-images.githubusercontent.com/94619247/166961312-65c35358-e5ce-41ae-9912-005c72bf786d.png)
![image](https://user-images.githubusercontent.com/94619247/166961359-0467981b-ee5d-4235-a9db-aec84dfcdd71.png)
# RESULT:
Feature Generation process and Feature Scaling process is applied to the given data frames sucessfully.

