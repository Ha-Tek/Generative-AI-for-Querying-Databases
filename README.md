# Generative-AI-for-Querying-Databases
Processed data can be retrieved from database tables using queries. Writing efficient queries is an essential skill for data professionals. In this hands-on lab, Generative AI platforms are used to create optimized queries by providing the model with sufficient context.

## Objective(s)

By the end of this lab, you'll be able to prompt a Generative AI model to create efficient queries for your data set.
## The data set

For the purpose of this lab, you are making use of the [**Heart Disease Data set**](https://archive.ics.uci.edu/dataset/45/heart+disease "Heart Disease Dataset") from the UCI ML library, available publically under the [**CCA 4.0 International**](https://creativecommons.org/licenses/by/4.0/legalcode "CCA 4.0 International") license.

You can download the data set and run the queries generated in this lab using any SQL querying system.

# Giving the context

You might note that there is a section named **`Prompt Instructions`** on the Generative AI interface.

If you provide the model with the description of your data, you can generate efficient and readily usable queries for fetching the data based on your requirements.

Paste the following text in the prompt instructions to give the model the appropriate context for the data.

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

The model will now have enough context to generate SQL queries for your prompts.
