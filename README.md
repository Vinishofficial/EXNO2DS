# EXNO2DS
# AIM:

To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT:
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from google.colab import files
uploaded = files.upload()
df = pd.read_csv(next(iter(uploaded)))
df.head()
```
<img width="987" height="162" alt="image" src="https://github.com/user-attachments/assets/e23a83d8-127d-4e70-9f0a-de83da95a8e3" />

df

<img width="1017" height="345" alt="image" src="https://github.com/user-attachments/assets/92b9bfe9-ce1b-49bc-8dab-ecb58daf3b14" />


```python
df.info()
```
<img width="311" height="280" alt="image" src="https://github.com/user-attachments/assets/2120307d-da97-40b9-830d-efc180179f9a" />


DISPLAY NO OF ROWS AND COLUMNS
```python
df.shape
```

<img width="218" height="72" alt="image" src="https://github.com/user-attachments/assets/480bc8ed-40cd-40e8-878e-20ea9a32bc5c" />


SET PASSENGER ID AS INDEX COLUMN

```python
df.set_index('PassengerId', inplace=True)
df.describe()
```

<img width="530" height="237" alt="image" src="https://github.com/user-attachments/assets/22303021-148f-4678-91c6-c84a9d2e45c3" />


CATEGORICAL DATA ANALYSIS
USE VALUE COUNT FUNCTION AND PERFROM CATEGORICAL ANALYSIS

```python
df['Pclass'].value_counts()
```

<img width="148" height="166" alt="image" src="https://github.com/user-attachments/assets/92969583-1fcf-4a7b-afb2-f19f44320b96" />

USE COUNTPLOT AND PERFORM UNIVARIATE ANALYSIS FOR THE "SURVIVED" COLUMN IN TITANIC DATASET
Countplot for Survived column
```python
sns.countplot(x='Survived', data=df)
plt.title('Survival Distribution')
plt.xlabel('Survived')
plt.ylabel('Count')
plt.show()

```
<img width="512" height="387" alt="image" src="https://github.com/user-attachments/assets/2dacd06b-c271-489a-abe3-10d1a8126ce2" />



<img width="317" height="80" alt="image" src="https://github.com/user-attachments/assets/3b5d607f-12fb-4f53-8adf-0089e3e0d101" />

RENAMING COLUMN
```python
df.rename(columns = {'Sex':'Gender'}, inplace = True)
df
```

<img width="971" height="376" alt="image" src="https://github.com/user-attachments/assets/12e99464-3952-48c5-8565-66eea0898408" />

Catplot for bivariate analysis
```python
sns.catplot(x='Pclass', y='Survived', data=df, kind='bar')
plt.title('Survival Rate by Passenger Class')
plt.xlabel('Passenger Class')
plt.ylabel('Survival Rate')
plt.show()
```

<img width="487" height="422" alt="image" src="https://github.com/user-attachments/assets/122050cf-d1e0-470e-a8a0-42e9d55e757c" />

```python
fig, ax1 = plt.subplots(figsize=(8,5))
graph = sns.countplot(x='Survived', data=df, ax=ax1)
graph.set_xticklabels(graph.get_xticklabels())
for p in graph.patches:
    height = p.get_height()
    graph.text(p.get_x() + p.get_width()/2, height + 20.8,
               height, ha="left")
```
<img width="1091" height="417" alt="image" src="https://github.com/user-attachments/assets/6377471e-80b8-4aea-a1b3-29bb50ee5176" />


Boxplot for Age and Survived
```python
sns.boxplot(x='Survived', y='Gender', data=df)
plt.title('Age Distribution by Survival')
plt.xlabel('Survived')
plt.ylabel('Age')
plt.show()
```

<img width="582" height="377" alt="image" src="https://github.com/user-attachments/assets/b94125fe-3b1e-443f-bca2-820a763efb44" />


Boxplot: Age by Passenger Class and Gender
```python
sns.boxplot(x='Pclass', y='Age', hue='Gender', data=df)
plt.title('Age Distribution by Passenger Class and Gender')
plt.xlabel('Passenger Class')
plt.ylabel('Age')
plt.show()
```

<img width="568" height="387" alt="image" src="https://github.com/user-attachments/assets/a0e8fba7-cc00-4113-9ab6-0f34050c3b5b" />


USE CATPLOT METHOD AND ANALYZE THREE COLUMNS(PCLASS,SURVIVED,GENDER)

```python
sns.catplot(x='Pclass', y='Survived', hue='Gender', data=df, kind='bar')
plt.title('Survival by Passenger Class and Gender')
plt.xlabel('Passenger Class')
plt.ylabel('Survival Rate')
plt.show()
```

<img width="506" height="423" alt="image" src="https://github.com/user-attachments/assets/8545f85e-e9e5-4bce-896a-e91d78cd4193" />



IMPLEMENT HEATMAP AND PAIRPLOT FOR THE DATASET
Heatmap for numerical columns

```python
plt.figure(figsize=(10, 6))
sns.heatmap(df.corr(numeric_only=True), annot=True, cmap='coolwarm')
plt.title('Correlation Heatmap')
plt.show()
```

<img width="683" height="432" alt="image" src="https://github.com/user-attachments/assets/dc6cdaff-1080-4ca5-9e42-74798dbff345" />

```python
sns.pairplot(df[['Pclass', 'Survived']].assign(PassengerId=df.index))
plt.show()
```

<img width="646" height="621" alt="image" src="https://github.com/user-attachments/assets/8d61aeae-14a7-44fd-843c-19d3234e70c4" />


# RESULT
 We have performed Exploratory Data Analysis on the given data set successfully.
