# Hospital Patient Survival Analysis (SQL)

## Project Overview

This project employs advanced SQL queries to analyze hospital patient data to understand mortality rates and the influence of demographic and clinical factors on patient survival. The goal is to deliver actionable insights that can support healthcare providers in improving patient outcomes.

## Problem Statement

Hospital mortality is influenced by many factors including patient demographics, comorbidities, and ICU admission characteristics. This project aims to analyze these factors via SQL queries to identify high-risk groups and critical predictors of hospital death.

## Data Description

- Dataset: Hospital patient records from `patient_survival.ps_data`.
- Features include: ethnicity, gender, age, ICU types and admission sources, physiological metrics (weight, BMI, heartrate), comorbidities (e.g., diabetes, leukemia), and hospital death status.
- Data cleaning steps include handling missing values such as updating ethnicity where missing.

## Methodology

The analysis includes:

- Data cleaning and imputation for missing ethnicity.
- Calculating mortality rates overall and stratified by ethnicity, gender, and age.
- Assessing impact of comorbid conditions on mortality.
- Investigating ICU admission sources and types in relation to mortality.
- Distribution analysis of BMI and physiological factors among survivors and deceased.
- Evaluating elective surgery statistics and ICU length of stay differences by survival status.

## Key Findings

- Mortality rates vary significantly by age, ethnicity, and comorbidity presence.
- Certain ICU admission sources and types are associated with higher death probabilities.
- Comorbidities such as diabetes and cirrhosis have notable prevalence among deceased patients.
- BMI and physiological metrics differ between survivors and non-survivors, indicating potential risk factors.

## How to Run

1. Set up access to the database containing the `patient_survival.ps_data` table.
2. Run the SQL scripts in the `/sql/` directory sequentially using your SQL client.
3. Examine the query outputs for patient survival insights and risk stratification.
4. Optionally export data for further visualization and reporting.

## Technologies

- SQL (PostgreSQL/MySQL/Other)
- SQL client tools (e.g., DBeaver, pgAdmin, MySQL Workbench)

## Contact

For questions or collaborations, reach out:

- Email: shahbaz.b.sharif@gmail.com
- LinkedIn: [linkedin.com/in/shahbaz-sharif](https://www.linkedin.com/in/shahbaz-sharif)

---

