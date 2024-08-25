# Bike Sharing Demand Prediction
## Overview
This project involves building a multiple linear regression model to predict the demand for shared bikes based on various factors. The dataset used in this analysis is from a US bike-sharing provider, BoomBikes, and includes daily records of bike rentals along with associated meteorological and seasonal data. The goal is to identify the key variables that influence bike demand and build a predictive model that can help the company optimize its operations and meet customer needs effectively.

## Dataset Description
The dataset contains the following columns:

instant: Record index (Dropped from the analysis)
dteday: Date (Dropped from the analysis)
season: Season (1: Spring, 2: Summer, 3: Fall, 4: Winter)
yr: Year (0: 2018, 1: 2019)
mnth: Month (1 to 12)
holiday: Whether the day is a holiday (0: No, 1: Yes)
weekday: Day of the week
workingday: Whether the day is neither weekend nor holiday (0: No, 1: Yes)
weathersit: Weather situation (1: Clear, 2: Mist, 3: Light Snow/Rain, 4: Heavy Rain/Fog)
temp: Temperature in Celsius (Normalized)
atemp: Feeling temperature in Celsius (Normalized)
hum: Humidity (Normalized)
windspeed: Wind speed (Normalized)
casual: Count of casual users (Dropped from the analysis)
registered: Count of registered users (Dropped from the analysis)
cnt: Count of total rental bikes (Target variable)
Data Preparation and Feature Engineering
Dropping Unnecessary Columns: The columns instant, dteday, casual, and registered were dropped as they were either irrelevant or not required for predicting the total count of bike rentals.

## Handling Categorical Variables:
Created dummy variables for categorical features such as season and weathersit.
The holiday, workingday, and yr variables were retained as they are binary and already encoded.
Scaling:

Numerical features such as temp, atemp, hum, and windspeed were scaled using Min-Max scaling to normalize the data between 0 and 1.

## Model Building

### Splitting Data:
The dataset was split into training (70%) and testing (30%) sets.

### Initial Model:
An initial model was built using only temp as the predictor, which showed a strong relationship with the target variable cnt.

### Iterative Model Building:
Additional features such as atemp, hum, and windspeed were added iteratively.
The model’s performance was evaluated at each step using statistical metrics such as R-squared and p-values.

### Multicollinearity Check:
Variance Inflation Factor (VIF) was calculated to detect multicollinearity among the predictors.
Variables with high VIF, indicating multicollinearity, were dropped to improve the model's stability.

### Final Model:
The final model included temp and hum as the most significant predictors.
The final R-squared value on the test data was around 43%, indicating that the model could explain 43% of the variance in bike demand.

### Model Evaluation
Residual Analysis: The residuals were plotted to check for normality and homoscedasticity. The Q-Q plot and residual vs. fitted plot confirmed that the model assumptions were reasonably met.
Regularization: Ridge and Lasso regression were applied to prevent overfitting, with Lasso providing the best results after hyperparameter tuning.
Cross-Validation: Cross-validation was used to assess the model's generalizability, with the final model achieving an R-squared of approximately 38% on the test set after tuning the Lasso model's alpha parameter.

### Conclusion
The project successfully identified key factors influencing bike demand, such as temperature and humidity, and built a predictive model using multiple linear regression. While the model provides useful insights, further improvements could be made by exploring additional features, alternative algorithms, or more advanced feature engineering techniques.

## How to Run the Project
Ensure all required Python packages are installed: pandas, numpy, matplotlib, seaborn, statsmodels, scikit-learn.
Load the dataset day.csv.
Follow the steps outlined in the code, from data preparation to model building and evaluation.
Analyze the outputs, including statistical summaries, plots, and final model performance metrics.
