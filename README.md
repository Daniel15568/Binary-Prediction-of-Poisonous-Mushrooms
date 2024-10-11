# 🍄 Kaggle Competition: Mushroom Classification

This project is a submission for a Kaggle competition where the goal was to predict whether a mushroom is edible (`e`) or poisonous (`p`). The dataset provided features related to the physical characteristics of mushrooms, and the task was to build a model to classify them into one of the two categories.

## 📊 Process Overview

### 1. Data Preprocessing

To prepare the data for the model, I performed the following steps:

- **Handling Missing Data:**  
  Before proceeding with any modelling, I examined the dataset for missing values. To ensure data quality, I applied a rule where any column with **less than 50% of the total data** was dropped. This helped remove columns with too many missing values, leaving only useful features for training.

- **Handling Categorical Data:**  
  The dataset contained several categorical features, such as cap shape, cap colour, and habitat. Since machine learning models require numeric input, I used **one-hot encoding** to convert these categorical features into a format suitable for the model. This step created new binary columns for each category, turning the categorical variables into numeric ones.

- **Scaling Features:**  
  After encoding, the dataset had a mix of values at different scales, which could affect model performance. I applied **standard scaling** to standardise the features, ensuring that all of them were on a similar scale. This is important for models like PCA and gradient boosting to perform effectively.

### 2. Dimensionality Reduction

Given the high number of features after one-hot encoding, I used **Principal Component Analysis (PCA)** to reduce the dimensionality of the data. PCA helps by retaining the most important information while reducing the number of features, which:
  - Prevents overfitting,
  - Improves training time, and
  - Simplifies the model without losing much predictive power.

### 3. Model Selection and Training

For this competition, I experimented with several machine learning models to find the best one for the task. The models I used were:

- **LightGBM (LGBM):** A gradient boosting algorithm that is fast and efficient, especially for large datasets.
- **XGBoost (XGB):** Another gradient boosting algorithm known for its performance in many machine learning tasks. XGBoost is robust and capable of handling complex classification problems.
- **Random Forest (RF):** An ensemble learning method that operates by constructing multiple decision trees and outputting the class that is the mode of the predictions of the individual trees.

After training all three models, **XGBoost (XGB)** performed the best, achieving an impressive **98% accuracy** on the test data.

### 4. Hyperparameter Tuning

To further optimise the models, I used **RandomizedSearchCV** to find the best hyperparameters for both LightGBM and XGBoost. Some of the key parameters I tuned include:

- `num_leaves` (controls the complexity of the trees),
- `max_depth` (limits tree depth),
- `learning_rate` (affects how quickly the model learns),
- `n_estimators` (number of boosting rounds).

For Random Forest, I focused on tuning parameters like `n_estimators` (number of trees) and `max_depth` (maximum depth of each tree).  
I used 5-fold cross-validation to ensure each model generalised well to unseen data.

### 5. Predictions and Submission

After tuning and selecting the best-performing model (XGBoost), I applied it to the test data. The model predicted whether each mushroom was edible (`e`) or poisonous (`p`). These predictions were saved in a CSV file with two columns:
  - `id`: the unique identifier for each mushroom,
  - `class`: the predicted class (`e` or `p`).

This file was then submitted to Kaggle for evaluation.

## 🏆 Results

After experimenting with different models, **XGBoost** was the best-performing model, achieving an impressive **98% accuracy** on the test data. This high level of accuracy reflects the model's ability to correctly classify mushrooms as either edible or poisonous. The combination of proper data preprocessing, dimensionality reduction, and extensive hyperparameter tuning contributed to this excellent result. 🎉

---



You can find the competition here: https://www.kaggle.com/competitions/playground-series-s4e8/overview
