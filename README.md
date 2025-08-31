# Countries_Ratings

**Countries Credit Ratings Predictor Tool**

**Author:** Iulian Costea

---

## 📌 Executive Summary
The **Countries Ratings** project is designed to predict **Country Credit Ratings** and **Country Outlook** for the **current year** and the **next year** for **any country worldwide**.

This information is critical for companies, institutional investors, and individual investors seeking new investment opportunities and assessing different countries' investment attractiveness and associated risk levels.

Predictions follow the rating scales provided by agencies like **Moody’s**, **Fitch**, and **S&P**. Historical credit rating data from **S&P**, **Moody’s**, and **DBRS** has been used for model training. Additional macroeconomic and demographic data has been collected from **World Bank** and **IMF**.

---

## 🎯 Rationale
- Not all countries have official credit ratings.
- Even when available, ratings are often updated infrequently.
- This tool provides **timely predictions** of ratings and outlooks for **current and near-future years**.

This makes the tool valuable for investors who require **up-to-date insights** into a country’s investment profile.

---

## ❓ Research Question
Can we predict a country’s **Credit Rating** and **Outlook** for the current and next year using macroeconomic and demographic indicators?

---

## 📊 Data Sources
| Dataset                        | Source                                                                 |
|--------------------------------|------------------------------------------------------------------------|
| Countries Credit Ratings       | [Wikipedia](https://en.wikipedia.org/wiki/List_of_countries_by_credit_rating) |
| CPI (Inflation)                | [IMF WEO](https://www.imf.org/en/Publications/WEO/weo-database/2025/april) |
| Government Debt                | [IMF WEO](https://www.imf.org/en/Publications/WEO/weo-database/2025/april) |
| Macroeconomic Indicators       | [World Bank](https://databank.worldbank.org/source/world-development-indicators) |

- Initial data coverage: **1960–2023**
- Training period after cleaning: **1980–2023**

---

## 🛠️ Methodology

1. **Data Preparation**
   - Extract, aggregate, normalize historical country ratings.
   - Map ratings to numerical values (**ratingn**).
   - Merge with macroeconomic and demographic data.
   - Clean consolidated DataFrame.

2. **Feature Engineering**
   - Correlation analysis + removal of multicollinear features.
   - Target imputation (`ffill`, `bfill`).
   - Feature imputation with multiple strategies: `polynomial_fill`, `mean_fill`, `rolling_average`, `ARIMA`, `global fallback`.
   - PCA for dimensionality reduction (first principal components).
   - Creation of lagging features *(work in progress).*

3. **Modeling**
   - Baseline: **DecisionTreeClassifier** for **ratingn** (multiclass) and **outlook**.
   - Hyperparameter optimization using **RandomizedSearchCV**.
   - Tested models: **RandomForest**, **XGBoost**, **LightGBM**, **CatBoost**.
   - Evaluations with **Confusion Matrix**, **AUC/ROC Curves**.

---

## 📈 Results

### Overall Technical Findings
- Feature imputation strategies improved data coverage significantly.
- PCA reduced dimensionality without major performance losses.
- **Class imbalance** in outlook prediction remains a key challenge.

---

## 🚀 Next Steps

- [ ] Address class imbalance in *outlook* prediction (e.g., SMOTE, class weights).
- [ ] Refine lagging features from *outlook*.
- [ ] Improve imputation techniques.
- [ ] Finalize regression models for feature predictions (current + next year).
- [ ] Add interpretability layer (e.g., SHAP values).

---

## 📂 Project Outline
- [Notebook: Countries Ratings Preparation](/blob/main/Countries_ratings.ipynb)

---

## 📜 License
MIT License (or specify)

---

## 📝 Notes
This README is a work in progress. Future updates will include detailed evaluation metrics, methodology diagrams, and reproducibility instructions (environment setup, run commands).

