# EDA-and-Visualization-of-a-Real-World-Dataset
Perform exploratory data analysis (EDA) on a dataset such as the Titanic Dataset or Airbnb Listings Dataset.

Exploratory Data Analysis (EDA) on Titanic Dataset

>Project Overview:

This project involves performing Exploratory Data Analysis (EDA) on a dataset using Python. The key steps include:

>Loading the dataset:

Checking for missing and duplicate values

Removing outliers using the Interquartile Range (IQR) method

Visualizing numeric distributions using histograms

Creating a correlation heatmap for feature relationships

Summarizing statistics for insights

>How to Run the Script:

Ensure you have the following libraries installed in your Python environment:

pip install pandas numpy matplotlib seaborn

>Importing Necessary Libraries:

import pandas as pd

import numpy as np

import matplotlib.pyplot as plt

import seaborn as sns

pandas: For data manipulation

numpy: For numerical operations

matplotlib & seaborn: For visualizations

>Loading the Dataset:

df = pd.read_csv('tested.csv')

Reads the dataset into a pandas DataFrame.

>Checking for Missing and Duplicate Values

df.isnull().sum()

df.duplicated().sum()

Identifies missing and duplicate values.

>Removing Outliers using IQR Method:

def remove_outliers(data, column):
  Q1 = data[column].quantile(0.25)
    
  Q3 = data[column].quantile(0.75)
    
  IQR = Q3 - Q1

  lower_bound = Q1 - 1.5 * IQR
  
  upper_bound = Q3 + 1.5 * IQR

  return data[(data[column] >= lower_bound) & (data[column] <= upper_bound)]

df_cleaned = remove_outliers(df, "Fare")

df_cleaned = remove_outliers(df_cleaned, "Age")

Identifies outliers using the IQR method.

Removes data points outside the calculated threshold.

>Visualization of Outliers Removed:

plt.figure(figsize=(10, 5))

sns.boxplot(data=df_cleaned[["Fare", "Age"]])

plt.show()

Shows boxplots for Fare and Age after outlier removal.

>Observation:

Outliers in Fare and Age have been removed.

>Visualizing Numeric Data Distributions:

numeric_columns = df.select_dtypes(include=["number"]).columns

df[numeric_columns].hist(figsize=(10, 10), bins=20, edgecolor="black")

plt.suptitle("Histograms of Numeric Columns", fontsize=16)

plt.show()

Plots histograms for all numeric features.

>Observation:

Some features are right-skewed, such as Fare.

Age follows a normal-like distribution.

>Creating a Correlation Heatmap:

numeric_df = df.select_dtypes(include=["number"])
correlation_matrix = numeric_df.corr()

plt.figure(figsize=(10, 10))

sns.heatmap(correlation_matrix, annot=True, cmap="coolwarm", fmt=".2f", linewidths=0.5)

plt.title("Correlation Heatmap")

plt.show()

Displays a correlation heatmap.

>Observation:

Pclass negatively correlates with Fare.

Age shows weak correlations with other features.

>Summary Statistics:

summary = df.describe()

summary

Generates summary statistics for numeric features.

>Observation:

The Fare column has a large range (0 to 512).

The average age is around 30 years.

>Conclusion:

The dataset had missing values, which should be addressed.

Outliers were removed to clean the data.

Data visualization revealed important insights into feature distributions.

The correlation heatmap helped identify relationships between features.
