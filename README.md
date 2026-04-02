# Energy Demand Forecasting: High-Load Appliance Analysis (Sub_metering_3)

## 📌 Project Overview
This project focuses on predicting and forecasting energy demand for high-load household appliances, specifically represented by the **Sub_metering_3** (Electric Water-heater and Air-conditioner) attribute of the UCI Household Power Consumption dataset. 

By isolating this specific sub-meter, the project aims to:
1.  **Forecast Future Demand:** Use **ARIMA** to predict the next 24–72 hours of AC/Heater usage based on historical consumption trends.
2.  **Analyze Behavioral Drivers:** Use **Random Forest Regression** to understand how external factors—such as the hour of the day, the day of the week, and total household power load—directly influence the activation of these high-energy appliances.
3.  **Data Engineering for Scale:** Demonstrate the ability to process, clean, and feature-engineer a high-volume dataset (~2 million rows) into a format suitable for time-series and machine learning models.

## 📊 Dataset Information
The dataset used is the **Individual Household Electric Power Consumption** from the UCI Machine Learning Repository.
* **Size:** ~2,075,259 observations (Very Large).
* **Granularity:** 1-minute sampling over 47 months.
* **Download Link:** [UCI Household Power Consumption](https://archive.ics.uci.edu/ml/datasets/individual+household+electric+power+consumption)

> **Note:** Due to the large file size (~130MB raw), the dataset is not included in this repository. Please download the `.txt` file from the link above and place it in the project root folder before running the scripts.

## 🛠️ Data Engineering Pipeline
* **Data Cleaning:** Replaced missing values (`?`) with `NaN` and applied **Mean Imputation** to ensure a continuous timeline for ARIMA.
* **Type Conversion:** Converted "Object" columns to `float64` to allow for mathematical modeling.
* **Time Feature Extraction:** Combined `Date` and `Time` strings into a `DatetimeIndex`.
* **Feature Engineering:** Extracted `hour`, `day_of_week`, and `month` to identify human behavioral patterns and seasonal trends.

## 🤖 Modeling Approach
* **ARIMA (Time-Series):** Captures the internal "memory" of the data to forecast future trends based on statistical lags.
* **Random Forest Regressor (ML):** A non-linear ensemble model used to map the relationship between energy demand and behavioral features like the time of day.

## 📈 Key Metrics & Analysis
* **Stationarity:** Verified via the **Augmented Dickey-Fuller (ADF)** test to justify ARIMA differencing ($d$).
* **Correlation:** Analyzed using **ACF/PACF** plots to determine model lags ($p, q$).
* **Accuracy:** Evaluated using **R-Squared ($R^2$)** for the Machine Learning model and Mean Absolute Error (MAE) for the forecast.

## 🚀 How to Run
1. Download the dataset from the UCI link provided above.
2. Ensure Python environments have `pandas`, `numpy`, `matplotlib`, `seaborn`, `statsmodels`, and `scikit-learn` installed.
3. Run the preprocessing script to clean the data and extract time features.
4. Execute the visualization and modeling cells to generate insights and forecasts.
