# Logistic Regression for Income Prediction

## Project Overview
This project involves using the **Adult Income** dataset to predict whether an individual's income exceeds $50K based on various demographic features. The model uses **Logistic Regression** for classification after performing necessary preprocessing and encoding on both training and testing datasets.

## Dataset Description
The dataset includes features such as:
- Age
- Workclass
- Education
- Marital Status
- Occupation
- Relationship
- Race
- Sex
- Capital Gain and Loss
- Hours per week
- Native Country
- Income (target variable)

There are two datasets:
1. **Training Set** (`Adult Train.csv`)
2. **Testing Set** (`Adult Test.csv`)

## Preprocessing Steps

### 1. Reading and Initial Data Cleaning
- The CSV files are read using pandas, and the columns are split and assigned appropriate names.
- Null values are checked, but there are no missing values in the dataset.

### 2. Dropping Irrelevant Features
- Features such as `fnlwgt`, `race`, `capital-gain`, and `capital-loss` are removed as they are considered irrelevant for the prediction task.
- The `education-num` feature is dropped because it represents the same information as `education`.

### 3. Feature Engineering
- **Age Groups:** Based on the `age` feature, a new column `Seniority` is created with categories:
  - Young (< 25 years)
  - Middle Age (25–60 years)
  - Senior (> 60 years)
- **Work Hours Groups:** Based on `hours-per-week`, a new column `Work_type` is created:
  - Part Time (≤ 20 hours)
  - Full Time (21–30 hours)
  - Over Time (> 30 hours)
- **Marital Status and Relationship:** A combined feature `marital_relation_sex` is created by merging `marital-status`, `relationship`, and `sex` to reduce dimensionality.

### 4. Encoding Categorical Variables
- Label Encoding is performed on categorical columns such as `workclass`, `education`, `occupation`, `native-country`, `Seniority`, `Work_type`, and the newly created `marital_relation_sex`.

### 5. Target Variable
- The target variable (`income`) is encoded as a binary class (0: ≤50K, 1: >50K).

## Model Training

### 1. Logistic Regression Model
- A **Logistic Regression** model is used for training.
- The model is trained on the preprocessed training data, using the encoded features and the target variable.

## Testing

### 1. Preprocessing Test Data
- The same preprocessing steps applied to the training data are also applied to the testing dataset:
  - Dropping irrelevant features
  - Creating new features (`Seniority`, `Work_type`, `marital_relation_sex`)
  - Label Encoding the categorical columns

### 2. Prediction
- The model makes predictions on the preprocessed test data.

### 1. Confusion Matrix
- A confusion matrix is generated to visualize the model's performance on the test data, showing the relationship between predicted and actual values.

### 2. Accuracy Score
- The accuracy of the model on the test dataset is **75.09%**.

## Conclusion
The project successfully predicts income levels using demographic data. Although the accuracy score is reasonable, further improvements can be made through techniques such as feature selection, hyperparameter tuning, or trying different classification models.

