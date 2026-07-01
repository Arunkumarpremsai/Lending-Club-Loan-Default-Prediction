# Lending Club Loan Default Prediction

## Overview
This repository contains a comprehensive data science and deep learning project that aims to predict whether a borrower will default on a loan. Using historical data from Lending Club, the project walks through data preprocessing, exploratory data analysis (EDA), feature engineering, and the training of a Deep Neural Network (DNN) using TensorFlow and Keras.

## Dataset
The project utilizes the `loan_data.csv` dataset, which contains **9,578** loans issued between 2007 and 2015. 
* **Target Variable:** `not.fully.paid` (Binary class: 0 for Fully Paid, 1 for Defaulted)
* The dataset typically features a severe class imbalance, where defaults make up a minority of the observations.

## Project Workflow

### 1. Data Preprocessing
* **Loading and Inspecting Data:** Checked for missing values and general dataset statistics.
* **Categorical Encoding:** Applied one-hot encoding to the `purpose` column (dropping the first category to avoid dummy variable trap) to convert qualitative text data into machine-readable numeric features.

### 2. Exploratory Data Analysis (EDA)
Comprehensive visualizations were built using `matplotlib` and `seaborn` to understand the data landscape:
* **Target Distribution:** Analyzed the class imbalance between fully paid and defaulted loans.
* **FICO Scores vs. Default Status:** Investigated how credit scores impact the likelihood of defaulting.
* **Interest Rates, DTI, & Annual Income:** Visualized continuous features using histograms and boxplots separated by default status.
* **Credit Inquiries:** Analyzed the impact of recent credit inquiries on loan repayment.

### 3. Feature Engineering
* **Correlation Analysis:** Generated a correlation matrix and heatmap for all numeric features.
* **Dimensionality Reduction:** Identified and dropped highly correlated feature pairs (`|r| > 0.75`) to reduce multicollinearity.

### 4. Deep Learning Model (TensorFlow / Keras)
* **Data Preparation:** Standardized features using `StandardScaler` and split the data into training, validation, and hold-out test sets. 
* **Architecture:** Designed a 3-hidden-layer Feed-Forward Neural Network (e.g., 128 → 64 → 32 neurons).
* **Regularization:** Incorporated Batch Normalization (for training stability) and Dropout layers to prevent overfitting.
* **Training Enhancements:**  `EarlyStopping`: Halts training when validation AUC stops improving.
  * `ReduceLROnPlateau`: Dynamically reduces the learning rate when metric improvements plateau.

### 5. Evaluation & Insights
* **Metric Optimization:** Tuned decision thresholds to maximize the F1-score for the minority class.
* **Model Performance:** Evaluated using Confusion Matrix, Classification Report, Accuracy, and ROC-AUC.
* **Feature Importance:** Employed a permutation-based approach to determine which features contributed most to the model's predictive power.

## Tech Stack
* **Python 3.x**
* **Data Manipulation:** `pandas`, `numpy`
* **Machine Learning:** `scikit-learn`
* **Deep Learning:** `tensorflow`, `keras`
* **Visualization:** `matplotlib`, `seaborn`
