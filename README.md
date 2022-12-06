# NYC-Parking-Violations-Exploratory-Analysis

## Description
This is an exploratory analysis on NYC Parking Violations dataset using Pandas and Numpy


## Project Context
The NYC Department of Finance collects data on every parking ticket issued in NYC (~10M per year!). This data is made publicly available to aid in ticket resolution and to guide policymakers. For this project we will use a dataset of 50,000 parking violations issued in New York City during the 2021 fiscal year. The dataset was created in January 2021 and contains data from April 1 to November 30, 2020 sourced from [NYC Open Data](https://data.cityofnewyork.us/City-Government/Parking-Violations-Issued-Fiscal-Year-2023/pvqr-7yc4).

I installed pandas, numpy and matplotlib libraries.

## Data Analysis Questions
1. Read the CSV file containing the NYC parking violation data.  Then print out the number of rows imported.
2. Perform exploratory data analysis on the imported dataset to identify invalid data.
3. Show a simple plot that shows the number of parking violations issued for each vehicle year.
4. Which year had the most vehicles issued with ticket violations?
5. Which are the top 5 car brands with the highest violation tickets issued in New York State?
6. Which day has most tickets issued?

## Code Explanation
Q1. **Read the CSV file containing the NYC parking violation data.  Then print out the number of rows imported.**
>#Import libraries
>
>`import pandas as pd`
>
>`import numpy as np`
>
>`import matplotlib.pyplot as plt`
>
>`import seaborn as sb`
>
>#Read the file and import rows
>
>`df = pd.read_csv('violations.csv', usecols=['Summons Number', 'Plate ID', 'Registration State', 'Plate Type', 'Issue Date' , 'Violation Code', 'Vehicle Make', 'Vehicle Body Type', 'Vehicle Expiration Date', 'Street Name', 'Vehicle Year','Vehicle Color'])`
>
>`df`
>
>


Q2. **Perform exploratory data analysis on the imported dataset to identify invalid data.**

The following data is considered to be invalid:

-Issue Date: dates not within the fiscal year (use 2020–11–30 as the end of the fiscal year)

-Violation Code: codes other than those between 1 and 99 (Violation Codes)

>#Changing Issue Date into a Datetime data type
>
>`df['Issue Date'] = pd.to_datetime((df['Issue Date']), infer_datetime_format=True)`
>
>#Removing rows containing invalid violation codes
>
>`df = df[df['Plate Type'] != '999']`
>
>`df.reset_index()`


Q3. **Show a simple plot that shows the number of parking violations issued for each vehicle year.**

>#Isolate the data to be used in the plot.
>
>`df_vehicle_year = df.groupby('Vehicle Year')`
>
>`['Summons Number'].count()`
>
>#Create a plot that shows the number of parking violations for each vehicle year.
>
>`plt.plot(df_vehicle_year)
plt.show()`


Q4. **Which year had the most vehicles issued with ticket violations?**

>`plt.figure(figsize=(25, 5))`
>
>`sb.countplot(data=df, x='Vehicle Year',` 
>
>`color=base_color);`
>
>`plt.title('Vehicle Year');`


Q5. **Which are the top 5 car brands with the highest violation tickets issued in New York State?**




## Author
Shirley Serem
