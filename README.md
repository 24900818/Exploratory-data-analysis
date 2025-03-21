# Exploratory-data-analysis

# EXNO2DS

# AIM:


  To perform Exploratory Data Analysis on the given data set.
EXPLANATION:
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

# CODING AND OUTPUT
     import pandas as pd
     import numpy as np
     import matplotlib.pyplot as plt
     import seaborn as sns
     file_path = '/content/drive/MyDrive/Colab Notebooks/titanic_dataset.csv' 
     dt = pd.read_csv(file_path)
     dt
  ![image](https://github.com/user-attachments/assets/6f4a7e75-6e2e-49c4-8906-ab3b90476587)
  
     dt.info()
  ![image](https://github.com/user-attachments/assets/68e5eea7-490c-465f-8d6b-c00a9bad712e)
  
      num_rows, num_columns = dt.shape
      print(f"Number of rows: {num_rows}")
      print(f"Number of columns: {num_columns}")
  ![image](https://github.com/user-attachments/assets/2ca0414f-c6d7-4bc2-abbd-55a2991e3454)
  
     dt.set_index("PassengerId", inplace=True)
     dt.head()
  ![image](https://github.com/user-attachments/assets/f555f387-d7e4-4a5e-a1e7-8ac57870ad6b)
  
     dt.describe()
  ![image](https://github.com/user-attachments/assets/4fdab13c-d9f8-42e6-8287-78c81eb200f1)
  
     survived_counts = dt['Survived'].value_counts()
     survived_percentages = dt['Survived'].value_counts(normalize=True) * 100
     print("Survived Counts:")
     print(survived_counts)
     print("\nSurvived Percentages:")
     print(survived_percentages)
  ![image](https://github.com/user-attachments/assets/3d891de6-2745-4f9f-9fa4-3c46d79ad00d)

    sex_counts = dt['Sex'].value_counts()
    sex_percentages = dt['Sex'].value_counts(normalize=True) * 100
    print("Sex Counts:")
    print(sex_counts)
    print("\nSex Percentages:")
    print(sex_percentages)
  ![image](https://github.com/user-attachments/assets/761bd8f9-79af-47a1-aff7-2795c8593937)

    pclass_counts = dt['Pclass'].value_counts()
    pclass_percentages = dt['Pclass'].value_counts(normalize=True) * 100
    print("Pclass Counts:")
    print(pclass_counts)
    print("\nPclass Percentages:")
    print(pclass_percentages)
  ![image](https://github.com/user-attachments/assets/f9e680d6-e114-4075-8740-6bb27c1588c8)

  
    embarked_counts = dt['Embarked'].value_counts()
    embarked_percentages = dt['Embarked'].value_counts(normalize=True) * 100
    print("Embarked Counts:")
    print(embarked_counts)
    print("\nEmbarked Percentages:")
    print(embarked_percentages)
  ![image](https://github.com/user-attachments/assets/e6d2074f-e839-43ab-a791-06cf9c196274)

    import matplotlib.pyplot as plt
    import seaborn as sns
    sns.set(style="whitegrid")
    sns.countplot(x='Survived', data=dt)
    plt.title('Survival Distribution')
    plt.show()
  ![image](https://github.com/user-attachments/assets/fea8152f-2eb1-4e21-a554-4bd02ab00a5b)

     sns.countplot(x='Pclass', data=dt)
     plt.title('Passenger Class Distribution')
     plt.show()
  ![image](https://github.com/user-attachments/assets/8e542d43-9cce-4523-82ed-406abfab33ed)

     import seaborn as sns
     import matplotlib.pyplot as plt
     sns.set(style="whitegrid")
     sns.countplot(x='Survived', data=dt)
     plt.title('Survival Distribution (Univariate Analysis)')
     plt.xlabel('Survived (0 = No, 1 = Yes)')
     plt.ylabel('Count')
     plt.show()
  ![image](https://github.com/user-attachments/assets/5d74dc81-8e8c-452b-886c-2b8f54071a25)

     unique_pclass = dt['Pclass'].unique()
     print("Unique values in 'Pclass':", unique_pclass)
  ![image](https://github.com/user-attachments/assets/a862cbde-fd7d-4cb8-ba37-b175572cf5b3)

      dt.rename(columns={'Sex': 'Gender'}, inplace=True)
      print(dt.columns)
  ![image](https://github.com/user-attachments/assets/f935e308-262f-4254-a644-a9bae52fe5de)

      import seaborn as sns
      import matplotlib.pyplot as plt
      sns.catplot(x='Pclass', hue='Survived', data=dt, kind='count', height=5, aspect=1.5)
      plt.title('Survival Count by Passenger Class')
      plt.xlabel('Passenger Class (Pclass)')
      plt.ylabel('Count')
      plt.show()
  ![image](https://github.com/user-attachments/assets/b467b7d0-8b8b-467c-b3e3-f9135d95775e)

     fig, ax1 = plt.subplots(figsize=(8, 5))
     graph = sns.countplot(x='Pclass', hue='Survived', data=dt, ax=ax1)
     for p in graph.patches:
     height = p.get_height()
     graph.text(p.get_x() + p.get_width() / 2, height + 20.8, height, ha="center")
     plt.title('Survival Count by Passenger Class')
     plt.xlabel('Passenger Class (Pclass)')
     plt.ylabel('Count')
     plt.legend(title='Survived', loc='upper right')
     plt.show()
  ![image](https://github.com/user-attachments/assets/b4a6be08-eb31-473c-bb6d-f35f0c88b200)

     plt.figure(figsize=(8, 5))
     sns.boxplot(x='Survived', y='Age', data=dt)
     plt.title('Age Distribution by Survival Status')
     plt.xlabel('Survived (0 = No, 1 = Yes)')
     plt.ylabel('Age')
     plt.show()
  ![image](https://github.com/user-attachments/assets/db84eff4-2fb8-4b56-bcb4-98bc5f666123)

     import seaborn as sns
     import matplotlib.pyplot as plt
     plt.figure(figsize=(10, 6))
     sns.boxplot(x='Pclass', y='Age', hue='Gender', data=dt)
     plt.title('Age Distribution by Passenger Class and Gender')
     plt.xlabel('Passenger Class (Pclass)')
     plt.ylabel('Age')
     plt.legend(title='Gender')
     plt.show()
  ![image](https://github.com/user-attachments/assets/b6190711-3831-4efe-955c-b708f7b90cb0)

      sns.catplot(x='Pclass', hue='Survived', col='Gender', data=dt, kind='count', height=5, aspect=1)
      plt.suptitle('Survival Count by Passenger Class and Gender', y=1.02)
      plt.show()
  ![image](https://github.com/user-attachments/assets/649b9721-eda3-4226-bb1e-bcac75ba0ff1)

      corr = dt.select_dtypes(include=np.number).corr()
      plt.figure(figsize=(10, 6))
      sns.heatmap(corr, annot=True, cmap='coolwarm', fmt='.2f')
      plt.title('Correlation Heatmap')
      plt.show()
  ![image](https://github.com/user-attachments/assets/a95e1dea-4296-4a24-a1c1-110a567c8504)

      sns.pairplot(dt, hue='Survived', height=2.5)
      plt.suptitle('Pairplot of Numerical Columns Colored by Survival Status', y=1.02)
      plt.show()
  ![image](https://github.com/user-attachments/assets/39afcbed-ddd6-48b9-88e7-9836215aeeaa)

 # RESULT
    Thus, the Exploratory Data Analysis on the given data set was performed successfully
