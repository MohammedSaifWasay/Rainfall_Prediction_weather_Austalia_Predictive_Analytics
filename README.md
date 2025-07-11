# 🌧️ Rain Prediction in Australia using Machine Learning

## 📌 Project Overview
This project focuses on predicting whether it will rain tomorrow in various locations across Australia using historical weather data from 2007 to 2017. Leveraging a range of machine learning models, the goal is to build an accurate predictive system that minimizes false negatives—days when rain occurs but is not forecasted.

## 🎯 Objectives
- Build an accurate machine learning model to predict rainfall.
- Identify key meteorological features influencing rain.
- Compare multiple classification algorithms using metrics like recall, precision, F1-score, and ROC-AUC.
- Apply SMOTEENN to address class imbalance and improve prediction of rain events.

## 🧪 Dataset
- **Source**: [Rain in Australia - Kaggle](https://www.kaggle.com/datasets/jsphyg/weather-dataset-rattle-package)
- **Size**: 145,460 rows × 23 columns
- **Target Variable**: `RainTomorrow` (Yes/No)
- **Date Range**: 2007 to 2017

### Key Features:
- Temperature: `MinTemp`, `MaxTemp`, `Temp9am`, `Temp3pm`
- Atmospheric: `Rainfall`, `Evaporation`, `Sunshine`
- Wind: `WindGustSpeed`, `WindSpeed9am`, `WindSpeed3pm`, `WindDir9am`, `WindDir3pm`
- Humidity & Pressure: `Humidity9am`, `Humidity3pm`, `Pressure9am`, `Pressure3pm`
- Cloud Cover: `Cloud9am`, `Cloud3pm`
- Binary indicators: `RainToday`, `RainTomorrow`

## ⚙️ Data Preprocessing
- **DateTime parsing** and feature extraction (year, month, day of year).
- **Missing values** imputed:
  - Numerical: KNN Imputer
  - Categorical: Mode Imputation
- **Outliers** removed and log-transformed for features like `Evaporation`, `WindSpeed9am`.
- **Feature Engineering**:
  - Categorical wind directions converted to angles.
  - Created cyclical features using sine and cosine transforms (e.g., `MonthSin`, `DayOfYearCos`).
- **Data Scaling**: StandardScaler
- **Train-Test Split**: Time-based (train data before 2015; test data from 2015 onwards)

## 📈 Exploratory Data Analysis (EDA)
- KDE plots show different distributions between rainy and non-rainy days.
- Rainy days tend to have:
  - Higher humidity and cloud cover
  - Lower sunshine and pressure
  - Higher wind gusts
- **Temporal trends**: Rain is more common in Feb–March (wet season in north), less in winter months (May–Oct).
- **Geographical patterns**:
  - Highest rainfall: Queensland, Northern Territory
  - Lowest rainfall: South Australia

## 🧠 Machine Learning Models
| Model               | Accuracy | Recall (Rain) | Precision (Rain) | F1 Score | ROC-AUC |
|--------------------|----------|----------------|------------------|----------|----------|
| **Random Forest**     | 0.7814   | 0.76           | 0.50             | **0.60** | **0.8542** |
| Gradient Boosting  | 0.7462   | **0.80**       | 0.45             | 0.58     | 0.8501   |
| Logistic Regression | 0.7191   | **0.83**       | 0.42             | 0.56     | 0.8479   |
| Decision Tree       | 0.7179   | 0.74           | 0.41             | 0.53     | 0.7873   |
| SVM (unbalanced)    | **0.8388**| 0.41           | **0.73**         | 0.52     | 0.8475   |

✅ **SMOTEENN** used for balancing—boosted recall and F1 score.

## 🧪 Key Findings
- **Most important features** (via Random Forest importance):
  - `Humidity3pm`, `Sunshine`, `Cloud3pm`, `Pressure3pm`, `Rainfall`, `WindGustSpeed`
- **Best Model Overall**: Random Forest (highest F1 and ROC-AUC)
- **Best Model for High Recall**: Logistic Regression (minimizes false negatives)
- **Afternoon features (3pm)** play a major role in rainfall prediction.

## 📚 References
- Rain in Australia Dataset: [Kaggle](https://www.kaggle.com/datasets/jsphyg/weather-dataset-rattle-package)
- Iqbal et al., 2022. *Rainfall Prediction using ML Fusion*, Future Internet.
- Tao et al., 2021. *ML methods for Tropical Rainfall*, J. Hydrometeorology.
- Kaya & Yıldız, 2023. *Rainfall Prediction with K-Stars*, Sustainability.

## 🚀 Future Work
- Experiment with deep learning models (LSTM, Bi-LSTM).
- Deploy model as an interactive web app.
- Integrate real-time data for live predictions.
- Hyperparameter optimization using Optuna or Bayesian search.

---

## 🧠 Author
**Mohammed Saif Wasay**  
*Data Analytics Graduate — Northeastern University*  
*Machine Learning Enthusiast | Passionate about turning data into insights*

🔗 [Connect with me on LinkedIn](https://www.linkedin.com/in/mohammed-saif-wasay-4b3b64199/)
