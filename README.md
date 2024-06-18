# DataHAck hackathon - Vaccine prediction  

## Project Description
This project aims to predict whether individuals received two types of vaccines: the XYZ flu vaccine and the seasonal flu vaccine. Specifically, we'll be predicting probabilities. The dataset includes various features related to the respondents' demographics, behaviors, and knowledge about the flu. The primary goal is to build machine learning models that can accurately predict the likelihood of vaccine uptake based on these features.

## Dataset
The project uses two datasets:
- `training_set_features.csv`: Contains the features for each respondent.
- `training_set_labels.csv`: Contains the labels indicating whether each respondent received the XYZ flu vaccine and the seasonal flu vaccine.

### Features
- **Numerical Features**: Various numerical indicators related to respondent behaviors and concerns.
- **Categorical Features**: Demographic information such as age group, education, race, sex, income level, marital status, housing status, employment status, and geographic region.

### Targets
- `xyz_vaccine`: Binary indicator of whether the respondent received the XYZ flu vaccine.
- `seasonal_vaccine`: Binary indicator of whether the respondent received the seasonal flu vaccine.

## Approach

### Data Preparation
1. **Loading Data**: The features and labels are loaded and merged on `respondent_id`.
2. **Feature Separation**: Numerical and categorical features are separated for preprocessing.

### Preprocessing
- **Numerical Features**:
  - Imputation of missing values using the median.
  - Standardization using `StandardScaler`.
- **Categorical Features**:
  - Imputation of missing values using the most frequent value.
  - One-hot encoding of categorical variables.

The preprocessing steps are combined into a `ColumnTransformer`.

### Model Training and Evaluation
Three different models were evaluated:
1. **Logistic Regression**
2. **Random Forest**
3. **XGBoost**

Each model was incorporated into a pipeline with the preprocessor and evaluated using the ROC AUC score for both target variables.

### Model Evaluation
The models were evaluated on a hold-out test set using the mean ROC AUC score across both target variables:
- **Logistic Regression**: 0.8459
- **Random Forest**: 0.8410
- **XGBoost**: 0.8387

Logistic Regression was found to be the best performing model.

### Submission
The best model (Logistic Regression) was retrained on the entire dataset. Predictions for the XYZ flu vaccine and seasonal flu vaccine were made and saved in a submission file.

## Results
The best model, Logistic Regression, achieved a mean ROC AUC score of 0.8459, indicating a strong performance in predicting vaccine uptake.

## Usage
To reproduce the results, follow these steps:
