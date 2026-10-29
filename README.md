# A Hands-on Project: Generative AI for Querying Databases
Processed data can be retrieved from database tables using queries. Writing efficient queries is an essential skill for data professionals. 

Source: [Learning from Coursera](https://www.coursera.org/learn/generative-ai-elevate-your-data-science-career/ungradedLti/0w6yM/hands-on-lab-generative-ai-for-querying-databases)

## Objective

Prompt a Generative AI model to create efficient queries for the given data set.
## The data set

For the purpose of this project, we are making use of the [**Heart Disease Data set**](https://archive.ics.uci.edu/dataset/45/heart+disease "Heart Disease Dataset") from the UCI ML library, available publically under the [**CCA 4.0 International**](https://creativecommons.org/licenses/by/4.0/legalcode "CCA 4.0 International") license.

We can download the data set and run the queries generated in this project using any SQL querying system.
However, for the SQL practice prompts I am listing below, I will use SQLite with Python in Google Colab.  We can write and execute SQL queries directly in Google Colab or Jupyter Notebook without installing a separate database server.

# Giving the context


If we provide the model with the description of our data, we can generate efficient and readily usable queries for fetching the data based on your requirements.

 Prompt the following instruction to give the model the appropriate context for the data.


###  Prompt
We have a Heart Disease prediction dataset with a single table which has the following attributes.
1. age - age in years
2. gender- gender (1 = male; 0 = female)
3. cp - chest pain type
        -- Value 1: typical angina
        -- Value 2: atypical angina
        -- Value 3: non-anginal pain
        -- Value 4: asymptomatic
4. trestbps - resting blood pressure (in mm Hg on admission to the hospital)
5. chol - serum cholestoral in mg/dl
6. fbs - (fasting blood sugar > 120 mg/dl)  (1 = true; 0 = false)
7. restecg - resting electrocardiographic results
        -- Value 0: normal
        -- Value 1: having ST-T wave abnormality (T wave inversions and/or ST elevation or depression of > 0.05 mV)
        -- Value 2: showing probable or definite left ventricular hypertrophy by Estes' criteria
8. thalach - maximum heart rate achieved
9. exang - exercise induced angina (1 = yes; 0 = no)
10. oldpeak - ST depression induced by exercise relative to rest
11. slope - the slope of the peak exercise ST segment
        -- Value 1: upsloping
        -- Value 2: flat
        -- Value 3: downsloping
12. ca - number of major vessels (0-3) colored by flourosopy
13. thal - 3 = normal; 6 = fixed defect; 7 = reversable defect
14. num (the predicted attribute) - diagnosis of heart disease (angiographic disease status)
        -- Value 0: < 50% diameter narrowing
        -- Value 1: > 50% diameter narrowing


The model (I used GPT-6) will now have enough context to generate SQL queries for our prompts.



# Prompts for Data Querying

Use these practice prompts to develop and test SQL queries, explore the dataset, and gain insights into the characteristics of patients with and without heart disease.

### 1. Age Distribution


Write an SQL query to find the minimum, maximum, and average age of patients in the dataset.



### 2. Gender Analysis


Write and SQL query to count the number of male and female patients in the dataset.

### 3. Chest Pain Type Frequency

Write an SQL query to determine the frequency of each type of chest pain (typical angina, atypical angina, non-anginal pain, asymptomatic) among patients.

### 4. Age Group Analysis and Target Variable

Write an SQL query to investigate the distribution of the target variable (presence or absence of heart disease) within different age groups (e.g., 20-30, 30-40, etc.).


### 5. Cholesterol Range

Find the minimum and maximum cholesterol levels among patients.

### 6. Age Range and Gender Analysis

Determine the youngest and oldest ages for male and female patients separately.

### 7. Age Group Analysis and Target Variable

Investigate the distribution of the target variable (presence or absence of heart disease) across different age groups (e.g., 20–30, 30–40, etc.).

### 8. Maximum Heart Rate by Age Group

Find the maximum heart rate achieved during exercise for different age groups (e.g., 30–40, 40–50, etc.).

### 9. Percentage of Patients with High Blood Sugar

Calculate the percentage of patients with fasting blood sugar greater than 120 mg/dL.

### 10. Ratio of Patients with Resting Electrocardiographic Abnormalities

Find the ratio of patients with abnormal resting electrocardiographic results to those with normal results.

### 11. Number of Patients with Reversible Thalassemia

Count the number of patients with reversible thalassemia detected through thallium stress testing.

### 12. Average Age of Patients with Chest Pain

Calculate the average age of patients who experienced chest pain during diagnosis.

### 13. Distribution of Patients by Number of Major Vessels

Investigate the distribution of patients based on the number of major blood vessels colored by fluoroscopy (0–3).


