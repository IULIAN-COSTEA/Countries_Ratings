## Countries_Ratings
Countries Credit Ratings Predictor Tool

**Author**
Iulian Costea

#### Executive summary
The project **Countries Ratings** is designed to predict **Country Credit Ratings** and **Country outlook** for the **current year** and **next year** for **any country in the world**.
This information is important for companies, insitutional investors and individual investors that are looking for new investment opportunities and are continously assessing different countries' investment attractivity and their associated risks level.
The countries credit ratings provided by the models in this project are following the ratig scale provided by agencies like Moody’s, Fitch or S&P. For model training historical credit ratings information from **S&P**, **Moody's** and **DBRS** has been used. 
Additional information related to macroeconomic indications and demographics has been collected from **Worldbank** and **IMF**.

#### Rationale
Access to countries credit ratings although are released as public information, are not available for all countries and also are not alway updated. That's because credit rating agencies do not provide credit ratings for all countries. 
Moreover, for the countries that are covered by the credit ratings the update period are sometime long and the most updated credit rating is not available for the present or near future. This project is a useful tool for the investors becuase provides insights into any country investment profile at any given time in the near future. (current and next year).

#### Research Question
The tool is predicting the **Country Credit Rating** and **Country Outlook** for the **current year** and **near future (next year)**.


#### Data Sources
The project uses the following data sources and datasets:

- **Countries credit Ratings** - Information collected from the following source: [Wikipedia](https://en.wikipedia.org/wiki/List_of_countries_by_credit_rating) 
  
- **Countries CPI** - Source: [FMI](https://www.imf.org/en/Publications/WEO/weo-database/2025/april)

- **Countries Government Debt** - Source:[FMI](https://www.imf.org/en/Publications/WEO/weo-database/2025/april)

- **Countries Macroeconomic Indicators** - Source: [WorldBank](https://databank.worldbank.org/source/world-development-indicators)

- Initial historical data covers period 1960-2023. However, due to missing data the period used for training is **training period 1980-2023**.

#### Methodology
Below a summary of the used methodology:

- Country Credit Ratings extraction, agregation and normalization - Historical Country Credit Ratings and Country Outlook have been collected from different creding Agencies. Data has been cleaned, agregated, normalized and mapped to a new numerical column **ratingn**.

- All datasets have been transformed, cleaned and merged into a single Dataframe for proper processing

- Conducted **data cleaning** on the new consolidated dataframe

- Conducted **correlation analysis** and **multi-colinearity** processing (by removing all multi-colinear features)

- Conducted **data processing and some imputation** (using .ffill() and .bfill()) on target columns **ratingn** and **outlook**.

- Conducted data imputation on features columns using following techniques: polynomial_fill, .ffill(), .bfill(), mean_fill, rolling_average, arima and Global Fallback for any remaining NaNs

- Conducted **PCA Analysis** and selected **First Principal Components**

- Create **lagging features** (work in progess)

- Build **Regression Models** for next 2 years predictions (work in progess)

- Build **Classification Baseline model** for *multiclass classification* using **DecisionTreeClassifier** for **two targets** Country Ratings (*ratingn*) and Country Outlook (*outlook*)

- Experimentation using **RandomSearchCV**(tried also SearchCV) and different classification models(*Randomforest*, *XGBoost*, *LightGBM* and *CatBoost* )

- Selected the best model and calculated Confusion matrix and AUC/ROC curves for both targets 

#### Results
What did your research find?

### **Overall technical findings**
<div align="justify">

</div>

#### Next steps

1. Address unbalanced multiclass dataset challenges for *outlook* target to improve its F1-score

2. Create lagging features using *outlook* features

3. Improve imputation techniques for a better imputation

4. Finalize Regression models to be able to predict all features for the current and next year

#### Outline of project

- [Link to notebook 1]()
- [Link to notebook 2]()
- [Link to notebook 3]()


<Br>

## **Overall technical findings**
<div align="justify">

</div>


 
- The **best model from Experiment-A and also overall** is: **LogisticRegression Model** with below results:

<br>
<div align="center">
  <img src="data/Experiment-A_res.png" alt="Experiment-A Results">
</div>
<br>

  - The best models for Experiment-B is: **Support Vector Machine (SVM)** with below results. However these rezults are below the results obtained in Experiment-A:

<br>
<div align="center">
  <img src="data/Experiment-B_res.png" alt="Experiment-B Results">
</div>
<br>


<br>
<div align="center">
  <img src="data/ROCs_Plot.jpg" alt="ROCs Results">
</div>
<br>



## **Business related findings and recommendations:**

