## Project Overview

Using the COVID-19 nursing home data, we built a machine learning model to predict the risk level in the next two weeks for each individual nursing home and the model has a weighted average area under ROC of 82.6%. Tableau was used to visualize the map of county level and nursing home level COVID-19 historical data and predicted data with multiple ways to filter and view the data.

## Team members
Yilin Cao
Runbai Wan
Yumei Wang
Xinrui Yuan
He Sun

### Approaches

• Summarize risk factors reported from multiple literatures
• Gather and Integrate data from CMS government, LTCfocus.org and NYTimes for model consumption
• Build a Machine Learning (ML) based model (LightGBM) to predict short term nursing home COVID-19 risk level using Google Colab
• Create final visualization input data with model prediction result and historical COVID trend, build interactive Tableau Dashboard map and publish to Tableau public server

### Data

How to get it:
• Download nursing home COVID-19 data from CMS government (https://data.cms.gov/covid-19/covid-19-nursing-home-data), LTCfocus.org and NYTimes(https://github.com/nytimes/covid-19-data)
• Convert nursing home locations to latitude and longitude for map visualization by Google geocoding API
• Combine datasets from different data sources

### Data pre-processing

Python and Pandas, NumPy, Scikit-learn libraries are used for data processing.

• Convert nursing home locations to latitude and longitude for map visualization:
To visualize each nursing home on map, latitude and longitude for each nursing home were retrieved by Google geocoding API using the full address of each nursing home.
• Combine datasets from different data sources:
Latitude and longitude of each nursing home are combined with Nursing home COVID-19 data, and then merged with nursing home characteristics data. Nursing homes with no characteristics data (possibly due to shutdown) were removed. Then combine with county level COVID-19 data (aggregated weekly from daily data).
• Deal with missing data:
For fixed values, forward fill them using the latest value available, then backward fill if still missing.
For values which are not expected to move drastically in a short period of time, forward fill only.
Skipping backward fill to avoid peeking into the future.
• Feature engineering
1) One-hot encoding categorical variables; 
2) Logarithm transformation of right skewed numeric features1; 
3) Lagging selected features to allow the model to see more historical data.

### Model training

Data is splitted into train set and test set. We used data after 2022-8-30 as the test data along with 5% nursing homes from random selection. As discussed above, we allow the model to see 4 weeks data of confirmed cases and 1 week data of other features to forecast the risk level of the following 2 weeks. We trained the model using gbdt booster and log loss for multi-class classification with 200 boost rounds.

### Model evaluation

To better measure model performance we plotted its Receiver Operating Characteristic as presented below. The plot indicated that the model is good at identifying Risk level 0 (the least risky) nursing homes as well as Risk level 2 (the most risky) while performing less accurately for Risk level 1. The model has a weighted average area under ROC of 82.6%.

### Code

• code/0a_county_level_COVID-19_daily_data.ipynb combines US county level COVID-19 daily data of year 2020, 2021 and 2022.
• code/0b_county_level_COVID-19_weekly_data_2020-2022.ipynb aggregates daily data into weekly data in accordance with the nursing home COVID-19 data weekly update.
• code/0c_get_nursing_home_latitude_and_longitude.ipynb converts the address of each nursing home into latitude and longitude by Google Geocoding API.
• code/1_read_input_data.ipynb combines data from different data source and performs preliminary data cleaning
• code/2_LightGBM_classification.ipynb performs feature engineering, treat missing variables and build LightGBM model
• code/3_prediction_LightGBM_classification.ipynb make predicts using LightGBM model 

