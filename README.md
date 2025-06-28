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

## 📚 References

* [Kaggle - Ames Housing Dataset](https://www.kaggle.com/c/house-prices-advanced-regression-techniques)
* [scikit-learn](https://scikit-learn.org/)
* [Flask](https://flask.palletsprojects.com/)

---
