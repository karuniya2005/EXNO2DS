# EXNO2DS
# AIM: To perform Exploratory Data Analysis on the given data set.
### NAME : KARUNIYA M
### REG NO : 212223240068
### DATE : 09/09/2024
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

data = pd.read_csv('/content/titanic_dataset.csv')

print(data.isnull().sum())

data['Fare'].fillna(data['Fare'].median(), inplace=True)
data['Embarked'].fillna(data['Embarked'].mode()[0], inplace=True)
```
![image](https://github.com/user-attachments/assets/a386e145-7fba-45eb-80a0-15cb8a048a93)

```
sns.boxplot(data=data, x='Fare')
plt.title('Boxplot of Fare')
plt.show()
```
![download](https://github.com/user-attachments/assets/fa40bc66-3f11-4643-b1f8-01fb046d6bc1)

```
def remove_outliers_iqr(df, column):
    Q1 = df[column].quantile(0.25)
    Q3 = df[column].quantile(0.75)
    IQR = Q3 - Q1
    lower_bound = Q1 - 1.5 * IQR
    upper_bound = Q3 + 1.5 * IQR
    return df[(df[column] >= lower_bound) & (df[column] <= upper_bound)]

data_no_outliers = remove_outliers_iqr(data, 'Fare')

sns.countplot(data=data_no_outliers, x='Fare')
plt.title('Countplot of Fare')
plt.show()
```
![download](https://github.com/user-attachments/assets/8aa90350-889d-4f9f-b160-c1dd3746280b)

```
sns.displot(data_no_outliers['Age'], kde=True)
plt.title('Distplot of Age')
plt.show()
```
![download](https://github.com/user-attachments/assets/251e7666-c19b-4870-90be-a79c5d76303a)

```
cross_tab = pd.crosstab(data_no_outliers['Pclass'], data_no_outliers['Survived'])
print(cross_tab)
```
![image](https://github.com/user-attachments/assets/2214d0dd-d1dd-4220-8f25-bd779e99387f)

```
sns.heatmap(cross_tab, annot=True)
plt.title('Heatmap of Pclass vs Survived')
plt.show()
```
![download](https://github.com/user-attachments/assets/b22d839f-167a-496c-b644-eddd696ab6b2)

# RESULT
Thus the program to Perform Exploratory data analysis for the given data set is successfully performed

