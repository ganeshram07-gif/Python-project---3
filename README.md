# Weather Data Analysis and Seasonal Trend Visualization Using Python

## Project Overview

This project analyzes historical global weather data using Python libraries Pandas and Matplotlib. It applies Exploratory Data Analysis (EDA) to clean, process, and visualize data for identifying seasonal patterns in temperature, precipitation, humidity, and more. 

The analysis transforms raw multi-location weather records into insights on trends and relationships between variables like temperature_celsius, humidity, precip_mm, and wind_kph. 

## Problem Statement

Raw weather datasets require cleaning and visualization to reveal patterns. This project addresses: temperature changes over time, seasonal rainfall/humidity trends, temperature-humidity correlations, seasonal distributions, and missing data handling. 
## Technologies Used

- Python
- Pandas
- Matplotlib
- NumPy
- Google Colab / Jupyter Notebook 
## Dataset Description

The GlobalWeatherRepository.csv contains observations from multiple locations with columns like: country, location_name, temperature_celsius, humidity, precip_mm, wind_kph, last_updated, and more (41 columns total, 131,758 rows). 
## Implementation Details

### 1. Importing Libraries

```python
import pandas as pd
import matplotlib.pyplot as plt
from google.colab import drive
drive.mount('/content/drive')
```


### 2. Loading the Dataset

```python
df = pd.read_csv('/content/drive/MyDrive/Python Project 1/GlobalWeatherRepository.csv')
```


### 3. Data Inspection

Displays shape (131758, 41), columns, head, and null sums (all zero post-cleaning).
### 4. Handling Missing Data

```python
df.fillna(df.mean(numeric_only=True), inplace=True)
```


### 5. Date and Time Processing

```python
df['last_updated'] = pd.to_datetime(df['last_updated'])
df['Month'] = df['last_updated'].dt.month
```


### 6. Creating Seasonal Categories

```python
def get_season(month):
    if month in [12,1,2]: return "Winter"
    elif month in [3,4,5]: return "Summer"
    elif month in [6,7,8]: return "Monsoon"
    else: return "Autumn"
df['Season'] = df['Month'].apply(get_season)
```


### 7. Temperature Trend Visualization

Daily average temperature line plot over dates. 
```python
df['Date'] = df['last_updated'].dt.date
daily_temp = df.groupby('Date')['temperature_celsius'].mean()
plt.plot(daily_temp.index, daily_temp.values)
```


### 8. Seasonal Rainfall Comparison

Bar chart of average precip_mm by season. 
### 9. Temperature Distribution

Histogram of temperature_celsius (20 bins). 
### 10. Temperature vs Humidity Relationship

Scatter plot of temperature_celsius vs humidity. 
### 11. Seasonal Data Distribution

Pie chart of season counts with percentages. 
## Project Objectives Achieved

- Loaded and inspected GlobalWeatherRepository.csv.
- Handled missing values with means.
- Added Month/Season columns and date processing.
- Created line plot for temperature trends, bar for seasonal rain, histogram for temp distribution, scatter for temp-humidity, pie for seasons. 
## Key Learning Outcomes

- EDA on multi-location weather data.
- Datetime handling and seasonal categorization.
- Matplotlib visualizations (line, bar, hist, scatter, pie).
- Pandas grouping, filling, and applying functions.
## Conclusion

This project uses Pandas and Matplotlib to reveal climate trends from global weather data, confirming seasonal patterns via visualizations.
## Author

**Ganesh Ram S**
