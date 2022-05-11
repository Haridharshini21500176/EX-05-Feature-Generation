# EX-05-Feature-Generation


## AIM
To read the given data and perform Feature Generation process and save the data to a file. 

# Explanation
Feature Generation (also known as feature construction, feature extraction or feature engineering) is the process of transforming features into new features that better relate to the target.
It includes two process:
Feature Encoding Feature Scaling

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
```
Program Developed: Haridharshini.S
Register number:212221230033
```
## Data.csv:
```
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
```
## Data.csv output:
![167535075-4bfd1901-3205-4443-a48f-25b591212309](https://user-images.githubusercontent.com/94168395/167890040-d8c22b8b-5c06-4ae2-97ce-a5999e157dbc.png)
![167535151-79710200-9ee9-4046-9236-10bd91b4abf1](https://user-images.githubusercontent.com/94168395/167890101-16b75e4f-1b84-44b0-b066-a87a0c20d7b1.png)
![167535212-2f97389b-44c6-4178-9b20-50e51cae1441](https://user-images.githubusercontent.com/94168395/167890151-e70877b8-64a4-426e-8501-8f89db36c213.png)
![167535250-769e47ab-8e88-4985-a3dc-23c36d6ea64f](https://user-images.githubusercontent.com/94168395/167890199-b14f33b8-342c-405b-857c-cc2addeb25fa.png)
![167535283-95949d9f-7fbd-45a0-b581-6ca5e1afea49](https://user-images.githubusercontent.com/94168395/167890237-0208202e-c2c6-40ae-8dd9-8b1e647f541f.png)
![167535541-20ea5766-2e18-4c84-8211-468e8e92fe86](https://user-images.githubusercontent.com/94168395/167890354-f1f4df5f-2290-46aa-bc3d-895bef1ad2a1.png)
![167535579-1fde21f6-ed58-493c-a399-cb6a612d5ba0](https://user-images.githubusercontent.com/94168395/167890397-411a3b0d-0d25-4f19-ae4a-3e675b267422.png)

## Encoding.csv code:
```
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
```
## Encoding.csv Output:
![167535752-06f9cdf1-7e81-4a56-90ff-1e4aba63797a](https://user-images.githubusercontent.com/94168395/167891050-081bf50a-73dc-45d3-b24a-ba0b327505bb.png)
![167535782-e587b16c-9fe3-429f-9388-a0c0df06de3c](https://user-images.githubusercontent.com/94168395/167891083-56e04fe9-8772-495c-9c54-948914d426d9.png)
![167535819-c8af8977-64b3-402c-8c92-538d30387180](https://user-images.githubusercontent.com/94168395/167891117-5beb27f9-f640-4362-a2db-2d7625e6890c.png)
![167535847-27bcc761-c846-4e9b-b8b5-ffe51552b3b7](https://user-images.githubusercontent.com/94168395/167891151-95d46499-fba0-4a1c-a272-0b594c8cc9e6.png)
![167535894-76fc3945-30ee-4f75-8a7f-7e12e192b364](https://user-images.githubusercontent.com/94168395/167891175-4a953995-92b2-4e42-a478-850c6c774c27.png)
![167535995-512feb0e-bf28-483d-a995-761f5b5a47f1](https://user-images.githubusercontent.com/94168395/167891262-03847809-f645-4052-9122-e2d53afaa94e.png)
![167536058-7c444df8-d262-435d-b946-0edd91313c90](https://user-images.githubusercontent.com/94168395/167891337-3c6df561-00b9-4f02-90a4-f527263e1137.png)

## Tiatanic.csv Code:
```
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
```
## Titanic.csv Output:
![167536194-5b47b956-e449-40ee-a02d-2565feeb4d51](https://user-images.githubusercontent.com/94168395/167891739-ed808499-af67-48b6-8a25-0fad759b8be4.png)
![167536225-abe4776c-87fb-4642-aa0b-6e690a1f2047](https://user-images.githubusercontent.com/94168395/167891815-c01e050c-5a60-4840-adae-ca06114cac87.png)
![167536245-aae9d19e-11a2-4e70-9e6c-0383591064d0](https://user-images.githubusercontent.com/94168395/167891848-b669ec6e-73cf-48b5-9190-d11a34c5ee1b.png)
![167536305-097a0fa2-8b24-4dc1-abc6-54ce2a2d0b75](https://user-images.githubusercontent.com/94168395/167891878-b0eec7ba-7f63-44fd-8fdf-f62bdc991a38.png)
![o23](https://user-images.githubusercontent.com/94168395/167891968-6ddc5803-cb6b-47ec-bff6-87a72f814e51.png)
![o24](https://user-images.githubusercontent.com/94168395/167891993-3d5c0104-3749-4d34-8790-c2e7b64f3aaa.png)
![167536485-746e1c58-fb1b-44be-8df8-831d73cae0ac](https://user-images.githubusercontent.com/94168395/167892108-5e1dd2f4-9e11-451e-b8c0-66373b67c372.png)
![o27](https://user-images.githubusercontent.com/94168395/167892221-a0c56297-dd9f-40b7-b92d-76035327e377.png)

# RESULT:
Hence Feature Generation process and Feature Scaling process is applied to the given data frames sucessfully.



































