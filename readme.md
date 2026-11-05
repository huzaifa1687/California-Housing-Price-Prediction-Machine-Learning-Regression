# California Housing Price Prediction

A Machine Learning regression project that predicts median house values in California using housing and demographic data.

## 1. Project Overview

The objective of this project is to develop a Machine Learning model that predicts California house values based on different features such as median income, average rooms, population, housing age, and geographical location.

Three models were developed and evaluated:

- Dummy Regressor (Baseline)
- Linear Regression
- Random Forest Regression

The final Random Forest model achieved an R² score of **0.802** on the test dataset.

## 2. Dataset Information

**Dataset:** California Housing Dataset  
**Source:** Scikit-learn  
**Dataset Size:** 20,640 records  
**Original Input Features:** 8  
**Target Variable:** `MedHouseVal`

### Dataset Features

| Feature | Description |
|---|---|
| MedInc | Median income in the block group |
| HouseAge | Median house age |
| AveRooms | Average number of rooms |
| AveBedrms | Average number of bedrooms |
| Population | Block group population |
| AveOccup | Average household occupancy |
| Latitude | Geographical latitude |
| Longitude | Geographical longitude |
| MedHouseVal | Median house value (target) |

**Important:** The target variable is measured in units of $100,000 and is capped at 5.0 (approximately $500,000).

The dataset is based on 1990 US Census information, so it does not represent today's housing market.

## 3. Technologies and Libraries

The project was developed using Python and Jupyter Notebook.

Libraries used:

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Joblib

## 4. Project Structure

```text
House-Price-Prediction/
│
├── data/
│   └── california_housing.csv
│
├── models/
│   └── california_housing_model.pkl
│
├── notebooks/
│   └── House_Price_Prediction.ipynb
│
├── outputs/
│   └── Evaluation charts and visualizations
│
├── README.md
└── requirements.txt
```

## 5. Project Workflow

The project followed these steps:

1. Dataset collection and loading
2. Exploratory Data Analysis (EDA)
3. Data inspection and cleaning
4. Feature engineering
5. Train-test splitting
6. Feature scaling
7. Baseline model development
8. Linear Regression model training
9. Random Forest model training
10. Cross-validation
11. Model evaluation
12. Residual analysis
13. Feature importance analysis
14. Model saving and testing

## 6. Exploratory Data Analysis (EDA)

Exploratory Data Analysis was performed to understand the dataset and identify patterns.

The following visualizations were created:

- Feature distribution histograms
- Target variable distribution
- Correlation heatmap
- Median income versus median house value scatter plot
- Feature correlation analysis
- Boxplots for identifying potential outliers

The analysis helped identify relationships between housing features and median house values.

## 7. Data Preprocessing and Feature Engineering

The target variable `MedHouseVal` was separated from the input features.

### Feature Engineering

Two additional features were created:

**RoomsPerHousehold**

Average rooms divided by average occupancy.

**BedroomsPerRoom**

Average bedrooms divided by average rooms.

These features provide additional information that may help the model identify housing patterns.

### Train-Test Split

The dataset was divided into:

- 80% Training Data
- 20% Testing Data

A fixed random state of 42 was used for reproducibility.

### Feature Scaling

StandardScaler was used to standardize numerical features.

The final model uses a Scikit-learn Pipeline to perform feature engineering and scaling automatically.

No categorical encoding was necessary because all original input features are numerical.

## 8. Machine Learning Models

Three regression approaches were developed.

### 1. Dummy Regressor (Baseline)

The baseline model predicts the mean target value from the training dataset for every observation.

It provides a reference point for evaluating whether more complex models actually improve predictions.

### 2. Linear Regression

Linear Regression models the relationship between input features and the target variable using a linear equation.

It provides a simple and interpretable benchmark.

### 3. Random Forest Regression

Random Forest is an ensemble learning algorithm that combines multiple decision trees.

It can capture nonlinear relationships and interactions between housing features.

The final model was configured with:

- Number of estimators: 100
- Maximum depth: 15
- Random state: 42

## 9. Model Evaluation

The final Random Forest model was evaluated using the test dataset.

### Final Performance Results

| Metric | Result |
|---|---:|
| Mean Absolute Error (MAE) | 0.3334 |
| Root Mean Squared Error (RMSE) | 0.5094 |
| R² Score | 0.802 |

### Interpretation

**MAE: 0.3334**

The average absolute prediction error is approximately $33,340.

**RMSE: 0.5094**

The root mean squared prediction error is approximately $50,940. RMSE penalizes larger prediction errors more heavily.

**R² Score: 0.802**

The model explains approximately 80.2% of the variation in house values in the test dataset.

Overall, the Random Forest model demonstrates good predictive performance on this dataset. However, its predictions are not perfectly accurate.

## 10. Cross-Validation

Five-fold cross-validation was used to evaluate model performance across different training and validation folds.

The training dataset was divided into five folds. Each fold was used for validation once while the remaining folds were used for training.

The purpose was to assess model stability and reduce dependence on a single train-test split.

Cross-validation results should be reported separately from the final test-set results.

## 11. Visualizations and Analysis

The following charts were generated to evaluate the model:

- Actual vs Predicted Values
- Residual Distribution
- Residuals vs Predicted Values
- Random Forest Feature Importance
- Model RMSE Comparison
- Model R² Comparison
- Correlation Heatmap

These visualizations help assess prediction quality, error patterns, and feature contributions.

## 12. Saving the Trained Model

The final trained pipeline was saved using Joblib.

Model file:

`models/california_housing_model.pkl`

The saved pipeline includes:

- Feature engineering
- Feature scaling
- Random Forest Regression

It accepts the original eight input features and automatically creates the two engineered features.

The `FeatureEngineer` class definition must be available when loading the saved model.

## 13. How to Run the Project

### Step 1: Clone the Repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
```

### Step 2: Open the Project Folder

```bash
cd House-Price-Prediction
```

### Step 3: Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 4: Start Jupyter Notebook

```bash
jupyter notebook
```

### Step 5: Open the Notebook

Open `House_Price_Prediction.ipynb` and run the cells in order.

## 14. Project Limitations

Although the model achieved an R² score of 0.802, several limitations remain:

1. **Outdated Dataset:** The dataset is based on 1990 Census information and does not reflect current housing prices.

2. **Target Value Cap:** Median house values are capped at 5.0, which limits the model's ability to predict differences among higher-value districts.

3. **Geographical Aggregation:** The dataset represents block-group-level statistics rather than individual property details.

4. **Missing Features:** Factors such as property condition, building quality, current interest rates, and recent market trends are not fully represented.

5. **Prediction Errors:** The model can produce inaccurate predictions, especially for unusual districts or housing values.

6. **Feature Importance:** Random Forest feature importance indicates predictive contribution, not causation.

## 15. Future Improvements

Possible improvements include:

- Hyperparameter tuning using GridSearchCV or RandomizedSearchCV.
- Testing Gradient Boosting and other ensemble models.
- Using additional and more recent housing datasets.
- Comparing different feature engineering approaches.
- Performing more detailed error analysis.
- Developing a web application for interactive predictions.

## 16. Conclusion

This project demonstrates the application of Machine Learning regression techniques to a real-world housing prediction problem.

The baseline, Linear Regression, and Random Forest approaches provide different levels of predictive modeling.

The final Random Forest model achieved:

- MAE: 0.3334
- RMSE: 0.5094
- R² Score: 0.802

The project covers the complete workflow, from data exploration and preprocessing to model training, evaluation, visualization, and model saving.

---

**Project:** California Housing Price Prediction  
**Category:** Machine Learning / Regression  
**Environment:** Python and Jupyter Notebook