# Chicago Crime & Weather Analysis

Predicting daily crime counts in Chicago using weather, day of week and seasonality. 
Built for UHI Data Analytics Assignments

## Files in this repo

- `1_Explore_Clean.ipynb`: Step 1, explore + clean both datasets, build BigQuery views, export combined (chicago_crime_weather_2017_2024) and individual CSVs (chicago_crime_by_location, chicago_crime_by_type) for further analysis
- `2_R_Analysis.ipynb`: Step 2, R analysis, correlations and regression models
- `3_Linear_Regression.ipynb`: Step 3, linear regression in TensorFlow
- `4_DNN.ipynb`: Step 4, DNN models (1, 2, and 3 hidden layers), comparison with linear baseline
- `chicago_crime_weather_2017_2024.csv`: combined daily dataset, 2920 rows x 38 columns
- `chicago_crime_by_location.csv`: long format, daily counts per (date, location_description)
- `chicago_crime_by_type.csv`: long format, daily counts per (date, primary_type)

## Data sources

Chicago crime data from `bigquery-public-data.chicago_crime.crime`. Weather from `bigquery-public-data.noaa_gsod.gsod*`, O'Hare station (USAF 725300). Window 2017-01-01 to 2024-12-31

## How to run

All notebooks load the CSVs directly from this repo.

1. Open any notebook in Google Colab (click "Open in Colab" badge)
2. Notebooks 1, 3, 4 use Python runtime 
3. Notebook 2 uses R runtime

## How to test the model with predefined data

Both notebooks 3 and 4 have a final cell that runs the model on hand-crafted test scenarios. Two sample inputs are predefined: a warm summer Friday (80F, no rain, July) and a cold rainy Sunday (20F, 0.5in rain, January)

To test own scenario, need to edit the values at the top of cell:

```python
row1['mean_temp_f']      = <temperature in F>
row1['precipitation_in'] = <precipitation in inches>
row1['wind_speed_knots'] = <wind speed in knots>
row1['visibility_miles'] = <visibility in miles>
row1['dow_X']            = 1   # 1=Sunday, 2=Mon, ... 7=Saturday
row1['month_Y']          = 1   # 1=January, ... 12=December
