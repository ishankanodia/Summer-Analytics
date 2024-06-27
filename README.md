# Vaccine Uptake Prediction Project

## Project Overview

The goal of this project is to predict the likelihood of individuals receiving two types of vaccines: the xyz vaccine and the seasonal flu vaccine. This is a multilabel classification problem, where we aim to predict two probabilities for each respondent: one for the xyz vaccine and one for the seasonal flu vaccine. The predictions are binary (0 or 1), but the model outputs should be probabilities ranging from 0.0 to 1.0.

## Data Description

The dataset provided includes 36 columns, with `respondent_id` as a unique identifier and 35 features describing various attributes of the respondents. The features include demographic information, health status, behavioral factors, opinions on vaccine effectiveness and risks, among others.

### Target Variables
- `xyz_vaccine`: Whether the respondent received the xyz flu vaccine (0 = No, 1 = Yes).
- `seasonal_vaccine`: Whether the respondent received the seasonal flu vaccine (0 = No, 1 = Yes).

### Features
1. **Concern and Knowledge about XYZ Flu**
   - `xyz_concern`: Level of concern about the xyz flu (0 to 3).
   - `xyz_knowledge`: Level of knowledge about the xyz flu (0 to 2).
   
2. **Behavioral Factors**
   - `behavioral_antiviral_meds`: Taken antiviral medications (binary).
   - `behavioral_avoidance`: Avoided close contact with others with flu-like symptoms (binary).
   - `behavioral_face_mask`: Bought a face mask (binary).
   - `behavioral_wash_hands`: Frequently washed hands or used hand sanitizer (binary).
   - `behavioral_large_gatherings`: Reduced time at large gatherings (binary).
   - `behavioral_outside_home`: Reduced contact with people outside of own household (binary).
   - `behavioral_touch_face`: Avoided touching eyes, nose, or mouth (binary).

3. **Doctor Recommendations**
   - `doctor_recc_xyz`: XYZ flu vaccine was recommended by doctor (binary).
   - `doctor_recc_seasonal`: Seasonal flu vaccine was recommended by doctor (binary).

4. **Health and Demographic Factors**
   - `chronic_med_condition`: Has chronic medical conditions (binary).
   - `child_under_6_months`: Has regular close contact with a child under six months (binary).
   - `health_worker`: Is a healthcare worker (binary).
   - `health_insurance`: Has health insurance (binary).
   
5. **Opinions on Vaccine Effectiveness and Risks**
   - `opinion_xyz_vacc_effective`: Opinion about xyz vaccine effectiveness (1 to 5).
   - `opinion_xyz_risk`: Opinion about risk of getting sick with xyz flu without vaccine (1 to 5).
   - `opinion_xyz_sick_from_vacc`: Worry of getting sick from taking xyz vaccine (1 to 5).
   - `opinion_seas_vacc_effective`: Opinion about seasonal flu vaccine effectiveness (1 to 5).
   - `opinion_seas_risk`: Opinion about risk of getting sick with seasonal flu without vaccine (1 to 5).
   - `opinion_seas_sick_from_vacc`: Worry of getting sick from taking seasonal flu vaccine (1 to 5).

6. **Demographics**
   - `age_group`: Age group of respondent.
   - `education`: Self-reported education level.
   - `race`: Race of respondent.
   - `sex`: Sex of respondent.
   - `income_poverty`: Household annual income with respect to 2008 Census poverty thresholds.
   - `marital_status`: Marital status of respondent.
   - `rent_or_own`: Housing situation of respondent.
   - `employment_status`: Employment status of respondent.
   - `hhs_geo_region`: Residence region (U.S. Dept. of Health and Human Services classification).
   - `census_msa`: Residence within metropolitan statistical areas.
   - `household_adults`: Number of other adults in household (top-coded to 3).
   - `household_children`: Number of children in household (top-coded to 3).
   - `employment_industry`: Type of industry respondent is employed in.
   - `employment_occupation`: Type of occupation of respondent.

## Data Preprocessing

1. **Load Data**: Load training and test datasets.
2. **Drop Irrelevant Columns**: Remove `respondent_id`, `health_insurance`, `employment_industry`, and `employment_occupation` columns.
3. **Encode Categorical Variables**: Use ordinal encoding for categorical features.
4. **Handle Missing Values**: Fill missing values with median for numerical features.
5. **Standardize Data**: Standardize numerical features for model training.

## Modeling

Several models were trained and evaluated:

1. **Logistic Regression**:
   - Fit two logistic regression models separately for `xyz_vaccine` and `seasonal_vaccine`.
   - Compute ROC AUC scores for each model.
   
2. **Random Forest Classifier**:
   - Fit random forest classifier and evaluate using cross-validation with ROC AUC scoring.
   
3. **Gradient Boosting Classifier**:
   - Fit gradient boosting classifier and evaluate using cross-validation with ROC AUC scoring.

## Evaluation

Performance was evaluated using the area under the receiver operating characteristic curve (ROC AUC) for each of the two target variables. The mean of these two scores provides the overall evaluation metric. This ensures that the model's probability predictions are accurately reflecting the likelihood of vaccine uptake.

## Results and Submission

Predictions were made on the test dataset using the trained models. The submission file includes:
- `respondent_id`
- `xyz_vaccine`: Predicted probability of receiving the xyz vaccine.
- `seasonal_vaccine`: Predicted probability of receiving the seasonal flu vaccine.

The final output was saved in a CSV file for submission.

## Conclusion

This project demonstrated the use of various machine learning models to predict vaccine uptake based on a range of features. By preprocessing the data effectively and evaluating multiple models, we aimed to achieve high predictive performance as measured by the ROC AUC metric.
