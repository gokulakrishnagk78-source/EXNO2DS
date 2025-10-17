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

## CODING AND OUTPUT
```
        import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

df = pd.read_csv("C:\\Users\\krishna\\Downloads\\titanic_dataset (1).csv")

df["Age"] = df["Age"].fillna(df["Age"].median())
df["Fare"] = df["Fare"].fillna(df["Fare"].median())
df["Embarked"] = df["Embarked"].fillna(df["Embarked"].mode()[0])

plt.figure(figsize=(8, 6))
sns.boxplot(data=df, x="Age")
plt.title("Boxplot of Age")
plt.tight_layout()
plt.show()

plt.figure(figsize=(8, 6))
sns.boxplot(data=df, x="Fare")
plt.title("Boxplot of Fare")
plt.tight_layout()
plt.show()

def remove_outliers(df, column):
    Q1 = df[column].quantile(0.25)
    Q3 = df[column].quantile(0.75)
    IQR = Q3 - Q1
    lower = Q1 - 1.5 * IQR
    upper = Q3 + 1.5 * IQR
    return df[(df[column] >= lower) & (df[column] <= upper)]

df = remove_outliers(df, "Age")
df = remove_outliers(df, "Fare")

plt.figure(figsize=(8, 6))
sns.countplot(data=df, x="Sex", hue="Survived", palette="Set2")
plt.title("Survival Count by Gender")
plt.tight_layout()
plt.show()

plt.figure(figsize=(8, 6))
sns.displot(data=df, x="Age", kde=True, bins=30, color="skyblue")
plt.title("Age Distribution")
plt.tight_layout()
plt.show()

cross_tab = pd.crosstab(df["Pclass"], df["Survived"])
print(cross_tab)

plt.figure(figsize=(8, 6))
sns.heatmap(cross_tab, annot=True, fmt="d", cmap="YlGnBu")
plt.title("Survival by Class Heatmap")
plt.tight_layout()
plt.show()
```
#output:
![Screenshot_17-10-2025_141149_localhost](https://github.com/user-attachments/assets/4b1cff97-f787-4e50-8ee2-7f8d8d166c06)
![Screenshot_17-10-2025_141219_localhost](https://github.com/user-attachments/assets/650b19ec-c112-4c56-ab2f-b4fa997b1018)
![Screenshot_17-10-2025_141159_localhost](https://github.com/user-attachments/assets/c4034387-e09a-44c1-af48-0faa316db39c)
![Screenshot_17-10-2025_14128_localhost](https://github.com/user-attachments/assets/c4d8f009-b005-4481-a6ec-83df2db77775)
![Screenshot_17-10-2025_141230_localhost](https://github.com/user-attachments/assets/149c3c88-a86b-47b3-b698-acbbc8601f98)

# RESULT:
exploratory data analysis for the given sample dataset is completed successfully
