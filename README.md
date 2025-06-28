# END_TO_END_DATA_SCIENCE_PROJECT

COMPANY: CODTECH IT SOLUTIONS

NAME: PARTH CHANDWANI

INTERN ID: CT08DF409

DOMAIN: DATA SCIENCE

DURATION: 8 WEEKS

MENTOR: NEELA SANTOSH

DESCRIPTION OF THE TASK:

---

# 🏠 House Price Prediction Web App

This project is a full-stack machine learning application that predicts house prices using trained models on the Ames Housing dataset. It includes data preprocessing, model training, and deployment via a Flask web app.

---

## 📁 Project Structure

```
.
├── app.py                       # Flask application for serving predictions
├── data_processing.py          # Preprocessing and model training script
├── house_price_model.pkl       # Trained Random Forest model (log-scaled)
├── house_price_preprocessor.pkl# ColumnTransformer for preprocessing
├── numerical_features.pkl      # List of numerical features used
├── categorical_features.pkl    # List of categorical features used
├── train.csv / test.csv        # Ames Housing dataset files (to be added manually)
├── templates/
│   └── index.html              # Frontend for inputting data (not included here)
```

---

## 🔧 Features

* Trained on Ames Housing Dataset
* Handles both numerical and categorical features
* Preprocessing includes:

  * Imputation for missing values
  * Feature scaling (numerical)
  * One-hot encoding (categorical)
* Random Forest Regressor as the core model
* Log-transformation of the target (`SalePrice`) for better performance
* Flask API with `/predict` endpoint for integration

---

## 📦 Requirements

```bash
pip install pandas numpy scikit-learn matplotlib seaborn flask joblib
```

---

## 🚀 How to Run the Project

1. **Download the Data:**

   * Download `train.csv` and `test.csv` from the [Kaggle Ames Housing dataset](https://www.kaggle.com/c/house-prices-advanced-regression-techniques/data)
   * Place them in the project root folder

2. **Train the Model:**

   ```bash
   python data_processing.py
   ```

3. **Start the Web App:**

   ```bash
   python app.py
   ```

4. Open your browser and go to `http://localhost:5000`

---
Based on the attached images, which appear to be screenshots from a VS Code environment, here's a detailed summary of the "End To End Data Science Project" for a `README.md` file.

-----

# End-to-End Data Science Project

This repository contains an end-to-end data science project, likely focused on a regression problem given the presence of house price-related files and RMSE/R-squared metrics. The project covers data preprocessing, model training, and deployment using Flask.

## Key Components and Files

  * **`app.py`**: This is the main Flask application file responsible for serving the web interface. It uses `render_template('index.html')` to display the front-end, suggesting a web-based interaction for the trained model.
  * **`data_processing.py`**: This script likely handles the entire data preprocessing pipeline. The screenshots show output related to:
      * Loading `train.csv` and `test.csv`.
      * Displaying `train_data` and `test_data` shapes.
      * Showing `info()` details for both datasets, including column names, non-null counts, and data types.
      * Identifying and reporting missing values in both `Train data` and `Test data`.
      * Performing preprocessing steps that result in `X_train_processed` and `X_test_processed` with shapes `(1460, 287)` and `(1459, 287)` respectively, indicating a significant increase in features after transformations (e.g., one-hot encoding).
  * **`categorical_features.pkl`**: A pickled file likely containing a list or a transformer for the categorical features identified during data preprocessing.
  * **`numerical_features.pkl`**: A pickled file likely containing a list or a transformer for the numerical features identified during data preprocessing.
  * **`house_price_model.pkl`**: This is the serialized (pickled) machine learning model, presumably trained to predict house prices.
  * **`house_price_preprocessor.pkl`**: This is the serialized (pickled) preprocessing pipeline or transformer used to prepare new input data for the `house_price_model`.
  * **`requirements.txt`**: Lists all the Python dependencies required to run this project.
  * **`test.csv`**: The test dataset used for model evaluation.
  * **`train.csv`**: The training dataset used for model development and training.
  * **`templates/index.html`**: The HTML template file for the Flask web application's home page. This is crucial for the web interface.
  * **`Figure_1.png`**, **`Figure_2.png`**: These are likely image files representing visualizations or plots generated during the exploratory data analysis (EDA) or model evaluation phases of the project.

## Data Overview (from screenshots)

The project deals with a dataset containing house-related information. Key observations from the `Test Info` and `Train Info` sections include:

  * **Total Columns**: 80 columns.
  * **Target Variable**: Likely `SalePrice` (present in `train.csv`, inferred from the problem type).
  * **Data Types**: A mix of `int64`, `float64`, and `object` (categorical) data types.
  * **Missing Values**: Significant missing values are present in several columns, requiring imputation or handling during preprocessing. Some examples with high missing counts:
      * `PoolQC` (1453 in train, 1456 in test)
      * `MiscFeature` (1446 in train, 1448 in test)
      * `Alley` (1369 in train, 1352 in test)
      * `Fence` (1179 in train, 1169 in test)
      * `FireplaceQu` (690 in train, 730 in test)
      * `LotFrontage` (259 in train, 227 in test)
      * `GarageType`, `GarageYrBlt`, `GarageFinish`, `GarageQual`, `GarageCond`, `BsmtExposure`, `BsmtFinType1`, `BsmtFinType2`, `BsmtQual`, `BsmtCond`, `BsmtExposure`, `MasVnrArea`, `MasVnrType` also have missing values, though fewer.

## Preprocessing Details (from `data_processing.py` output)

  * The preprocessing step transforms the original features.
  * `X_train_processed` shape: `(1460, 287)`
  * `X_test_processed` shape: `(1459, 287)`
  * `y_log_shape`: `(1460,)` (suggests the target variable `SalePrice` was log-transformed, which is common for skewed distributions in regression problems).

## Model Performance

The model's performance on the validation set (log-transformed target) is reported as:

  * **RMSE**: 0.1448
  * **R-squared**: 0.8876

These metrics indicate a reasonably good fit, with an R-squared of 0.8876 suggesting that approximately 88.76% of the variance in the log-transformed house prices is explained by the model.

-----

## 🧠 Model Insights

* **Algorithm**: `RandomForestRegressor`
* **Performance**:

  * **Log-scale RMSE**: \~0.15–0.20
  * **R² Score**: \~0.85+
  * **Original-scale RMSE**: \~30,000–40,000 USD (approx.)

---

## 🧮 Example API Input (JSON)

```json
{
  "GrLivArea": 1710,
  "OverallQual": 7,
  "GarageCars": 2,
  "GarageArea": 548,
  "TotalBsmtSF": 856,
  "1stFlrSF": 856,
  "FullBath": 2,
  "TotRmsAbvGrd": 8,
  "YearBuilt": 2003,
  "MSSubClass": 60,
  "MSZoning": "RL",
  "LotFrontage": 65.0,
  "LotArea": 8450,
  "Street": "Pave",
  "LotShape": "Reg",
  "ExterQual": "Gd",
  "Foundation": "PConc",
  "BsmtQual": "Gd",
  "CentralAir": "Y",
  "KitchenQual": "Gd",
  "GarageType": "Attchd",
  "GarageFinish": "RFn",
  "PavedDrive": "Y",
  "SaleType": "WD",
  "SaleCondition": "Normal"
}
```

---

## 🔄 API Endpoint

**POST** `/predict`
**Request**: JSON payload of feature values
**Response**:

```json
{
  "predicted_house_price": 208497.52
}
```

---
![Image](https://github.com/user-attachments/assets/a9cfcaba-b448-42e9-a669-e42fc2c77ab8)
![Image](https://github.com/user-attachments/assets/f8435af6-26bd-43e1-b142-295a47b10cb5)
![Image](https://github.com/user-attachments/assets/d8834b21-f5d7-42a5-a807-2a37718f1643)
![Image](https://github.com/user-attachments/assets/fa243947-ee8e-4e00-b693-97be13b2ae7f)
![Image](https://github.com/user-attachments/assets/98f641cb-81d4-4fda-84d3-dca2ec3cda82)
![Image](https://github.com/user-attachments/assets/56f7d2e2-aaf3-4626-b029-7e38277800b2)
![Image](https://github.com/user-attachments/assets/2e0fc00b-e66f-4ae3-b677-725f4e6b4d31)
![Image](https://github.com/user-attachments/assets/57fbbfa4-8192-4b18-bb79-4731e06da825)
![Image](https://github.com/user-attachments/assets/204136ff-afd5-484d-865e-5fb9f1d2f001)
![Image](https://github.com/user-attachments/assets/6ece8dda-f999-4d7d-8b28-61c3f900a37b)
![Image](https://github.com/user-attachments/assets/4c2c4c9b-3a7e-4072-8a47-41d82595cd06)
![Image](https://github.com/user-attachments/assets/e0b77b0a-b864-4031-a159-29519097eaf2)
![Image](https://github.com/user-attachments/assets/1c910da8-c591-4ee4-842e-b04ba87f8499)
![Image](https://github.com/user-attachments/assets/9269445c-7a8d-4a58-8efe-8e4f953eb875)


## 📚 References

* [Kaggle - Ames Housing Dataset](https://www.kaggle.com/c/house-prices-advanced-regression-techniques)
* [scikit-learn](https://scikit-learn.org/)
* [Flask](https://flask.palletsprojects.com/)

---
