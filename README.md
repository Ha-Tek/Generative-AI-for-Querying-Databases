# A Hands-on Project: Generative AI for Querying Databases
Processed data can be retrieved from database tables using queries. Writing efficient queries is an essential skill for data professionals. 

## Objective

Prompt a Generative AI model to create efficient queries for the given data set.
## The data set

For the purpose of this project, we are making use of the [**Heart Disease Data set**](https://archive.ics.uci.edu/dataset/45/heart+disease "Heart Disease Dataset") from the UCI ML library, available publically under the [**CCA 4.0 International**](https://creativecommons.org/licenses/by/4.0/legalcode "CCA 4.0 International") license.

We can download the data set and run the queries generated in this project using any SQL querying system.

# Giving the context


If we provide the model with the description of our data, we can generate efficient and readily usable queries for fetching the data based on your requirements.

 Prompt the following instruction to give the model the appropriate context for the data.

**html**

```html
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
```

The model will now have enough context to generate SQL queries for our prompts.



# Prompts for Data Querying

## Age Distribution

Consider the following prompt.

**Prompt (HTML)**

```html
Write an SQL query to find the minimum, maximum, and average age of patients in the dataset.
```

You can expect to the see the following query in response.

**SQL Query**

```sql
SELECT 
    MIN(age) AS min_age,
    MAX(age) AS max_age,
    AVG(age) AS avg_age
FROM heart_disease_prediction_dataset;
```

## Gender Analysis

Consider the following prompt.

**Prompt (HTML)**

```html
Write and SQL query to count the number of male and female patients in the dataset.
```

You can expect to the see the following query in response.

**SQL Query**

```sql
SELECT
  SUM(CASE WHEN gender = 1 THEN 1 ELSE 0 END) AS male_count,
  SUM(CASE WHEN gender = 0 THEN 1 ELSE 0 END) AS female_count
FROM heart_disease_prediction_dataset;
```

## Chest Pain Type Frequency

Consider the following prompt.

**Prompt (HTML)**

```html
Write an SQL query to determine the frequency of each type of chest pain (typical angina, atypical angina, non-anginal pain, asymptomatic) among patients.
```

You can expect the following query to be generated.

**SQL Query**

```sql
SELECT
  CASE cp
    WHEN 1 THEN 'typical_angina'
    WHEN 2 THEN 'atypical_angina'
    WHEN 3 THEN 'non_anginal_pain'
    WHEN 4 THEN 'asymptomatic'
    ELSE 'unknown'
  END AS chest_pain_type,
  COUNT(*) AS frequency
FROM your_table_name
GROUP BY
  CASE cp
    WHEN 1 THEN 'typical_angina'
    WHEN 2 THEN 'atypical_angina'
    WHEN 3 THEN 'non_anginal_pain'
    WHEN 4 THEN 'asymptomatic'
    ELSE 'unknown'
  END
ORDER BY frequency DESC;
```

## Age Group Analysis and Target Variable

Consider the following prompt.

**Prompt (HTML)**

```html
Write an SQL query to investigate the distribution of the target variable (presence or absence of heart disease) within different age groups (e.g., 20-30, 30-40, etc.).
```

You can expect the following output.

**SQL Query**

```sql
SELECT
  CASE
    WHEN age IS NULL THEN 'Unknown'
    WHEN age >= 20 AND age < 30 THEN '20-29'
    WHEN age >= 30 AND age < 40 THEN '30-39'
    WHEN age >= 40 AND age < 50 THEN '40-49'
    WHEN age >= 50 AND age < 60 THEN '50-59'
    WHEN age >= 60 AND age < 70 THEN '60-69'
    WHEN age >= 70 AND age < 80 THEN '70-79'
    ELSE '80+'
  END AS age_group,
  num AS heart_disease_status,
  COUNT(*) AS count
FROM your_table_name
GROUP BY
  CASE
    WHEN age IS NULL THEN 'Unknown'
    WHEN age >= 20 AND age < 30 THEN '20-29'
    WHEN age >= 30 AND age < 40 THEN '30-39'
    WHEN age >= 40 AND age < 50 THEN '40-49'
    WHEN age >= 50 AND age < 60 THEN '50-59'
    WHEN age >= 60 AND age < 70 THEN '60-69'
    WHEN age >= 70 AND age < 80 THEN '70-79'
    ELSE '80+'
  END,
  num
ORDER BY age_group, heart_disease_status;
```

