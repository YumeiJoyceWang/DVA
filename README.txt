##################
# DESCRIPTION:
##################
Python code for DATA and MODEL:
code/0a_county_level_COVID-19_daily_data.ipynb combines US county level COVID-19 daily data of year 2020, 2021 and 2022 which were downloaded from this link: https://github.com/nytimes/covid-19-data.
code/0b_county_level_COVID-19_weekly_data_2020-2022.ipynb aggregates daily data into weekly data in accordance with the nursing home COVID-19 data weekly update.
code/0c_get_nursing_home_latitude_and_longitude.ipynb converts the address of each nursing home into latitude and longitude by Google Geocoding API.
code/1_read_input_data.ipynb combines data from different data source and performs preliminary data cleaning
code/2_LightGBM_classification.ipynb performs feature engineering, treat missing variables and build LightGBM model
code/3_prediction_LightGBM_classification.ipynb make predicts using LightGBM model 

VISUALIZATION:
1. Tableau generates tableau extract with visual dataset produced from model post-data processing (code/3_prediction_LightGBM_classification.ipynb: final_visual.csv).
2. Create Tableau MAP sheet, Top 10 Sheet, Trend plot-facility sheet and dashboard1, dashboard1 is final visual product(all of these could be found in tableau workbook submitted). 
3. Tableau visual dashboard and data extract published on Tableau public server (https://public.tableau.com/app/profile/ruby1883/viz/team88-final-project/Dashboard1?publish=yes), tableau workbook and data could be downloaded from site, and also saved in Doc/TableauWorkbook folder (team88-final-project.twbx, final_visual.csv)


##################
# INSTALLATION
##################
Tableau Dashboard is available at https://public.tableau.com/app/profile/ruby1883/viz/team88-final-project/Dashboard1?publish=yes

Running the DATA and MODEL code would need python installation and relevant packages. We recommend Google Colab for package version consistency.
Note: all data needed for Tableau Dashboard is uploaded to Tableau public server, there's no need to run DATA and MODEL code for viewing/interacting with Tableau Dashboard.

##################
# EXECUTION
##################
Tableau Dashboard is available at https://public.tableau.com/app/profile/ruby1883/viz/team88-final-project/Dashboard1?publish=yes

##################
# DEMO VIDEO
##################
https://youtu.be/WPDeCED8ZNE