# Project

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from google.colab import files

try:
    df = pd.read_csv("OCD Patient Dataset_ Demographics & Clinical Data.csv")
except FileNotFoundError:
    print("File not found. Please upload the 'OCD Patient Dataset_ Demographics & Clinical Data.csv' file.")
    uploaded = files.upload()
    if uploaded:
        # Assuming the user uploads the correct file
        for fn in uploaded.keys():
            print(f'User uploaded file "{fn}" with length {len(uploaded[fn])} bytes')
            df = pd.read_csv(fn)
    else:
        print("No file was uploaded. Please upload the file to proceed.")
        df = None

if df is not None:
    print("Dataset loaded successfully.")

 df.head()
df.info()
df.describe()

Missing_values = df.isnull().sum()
print(Missing_values)




df['Previous Diagnoses'].fillna('Unknown', inplace=True)
df['Medications'].fillna('Unknown', inplace=True)


plt.figure(figsize=(10, 6))
plt.hist(df['Age'], bins=20)
plt.xlabel('Age')
plt.ylabel('Count')
plt.title('Age Distribution of OCD Patients')
plt.show() 


sns.countplot(x='Gender', data=df)
plt.title('Gender Distribution')
plt.show()


sns.histplot(df['Y-BOCS Score (Obsessions)'], bins=20, kde=True)
plt.title('Obsession Severity Distribution')
plt.show()


sns.scatterplot(
    x='Y-BOCS Score (Obsessions)',
    y='Y-BOCS Score (Compulsions)',
    data=df
)
plt.title('Obsession vs Compulsion Severity')
plt.show()


sns.countplot(x='Depression Diagnosis', data=df)
plt.title('Depression in OCD Patients')
plt.show()

sns.countplot(x='Anxiety Diagnosis', data=df)
plt.title('Anxiety in OCD Patients')
plt.show()





plt.figure(figsize=(10,6))
sns.heatmap(df[['Age',
            'Duration of Symptoms (months)',
                'Y-BOCS Score (Obsessions)',
                'Y-BOCS Score (Compulsions)']].corr(),
            annot=True, cmap='coolwarm')
plt.title('Correlation Matrix')
plt.show()




data = pd.read_csv('OCD Patient Dataset_ Demographics & Clinical Data.csv')
data.head()


data.describe()

data['Previous Diagnoses'] = data['Previous Diagnoses'].fillna('Unknown')
data['Medications'] = data['Medications'].fillna('Unknown')

plt.hist(data.Age, bins=20)
plt.xlabel('Age')
plt.ylabel('Count')
plt.title('Age Distribution of OCD Patients')
plt.show()


sns.countplot(x='Gender', data=data)
plt.title('Gender Distribution')
plt.show()

sns.histplot(data['Y-BOCS Score (Obsessions)'], bins=20, kde=True)
plt.xlabel('Y-BOCS Obsession Score')
plt.ylabel('Count')
plt.title('Obsession Severity')
plt.show()


plt.scatter(data['Y-BOCS Score (Obsessions)'], data['Y-BOCS Score (Compulsions)'])
plt.xlabel('Obsessions Score')
plt.ylabel('Compulsions Score')
plt.title('Obsessions vs Compulsions')
plt.show()

plt.figure(figsize=(10,6))
sns.heatmap(data[['Age',
                'Duration of Symptoms (months)',
                'Y-BOCS Score (Obsessions)',
                'Y-BOCS Score (Compulsions)']].corr(),
            annot=True, cmap='coolwarm')
plt.title('Correlation Heatmap')
plt.show()


data.describe()
















































