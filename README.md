# PyBer_Analysis
Python using matplotlib and Pandas in Jupyter Notebook
## PyBer Launch - Introduction
This analysis for ride sharing platform, Pyber, writes Python using Pandas Library and Matplotlib in Jupyter Notebook to visualize how weekly fares across city types (Urban, Suburban and Rural) differ. This code and the visualtizations can be refactored to view differences of rides by city type, number of riders by city type, and number of drivers by city allowing PyBer to improve access to ride sharing services and determine affordability by city type.

First analysis shown by the PyBer code showcase the relationshp btw type of city and number of drivers and riders and percentage of total fares by rider, driver and type of city

charts showcase relationshp between the type of city and number of drivers and riders as well as percentage of total fares of riders and drivers by type of city
## Devlopment
### if you fail to plan, you plan to fail
In the first analysis [Pyber.ipyng](http://localhost:8888/notebooks/PyBer_Analysis/Pyber.ipynb) an exploratory analysis ran through some very large csv data files
DataFrames were merged alongside groupby(), .count(), .sum(), .mean, to understand average fares, total rides, and total drivers by city type

```
#Sum of fares for each city type
sum_fares_by_type = pyber_data_df.groupby(["type"]).sum()["fare"]

# Ride Count for Urban Cities
urban_ride_count = urban_cities_df.groupby(["city"]).count()["ride_id"]

#Average Fare in Urban Cities
urban_avg_fare = urban_cities_df.groupby(["city"]).mean()["fare"]

```


Charts including scatter, pie and box & whiskers help visualize the story expressing outliers, city type with most activity, and more:


You come up with the following list of steps and deliverables:

Import your data into a Pandas DataFrame.
Merge your DataFrames.
Create a bubble chart that showcases the average fare versus the total number of rides with bubble size based on the total number of drivers for each city type, including urban, suburban, and rural.
Determine the mean, median, and mode for the following:
The total number of rides for each city type.
The average fares for each city type.
The total number of drivers for each city type.
Create box-and-whisker plots that visualize each of the following to determine if there are any outliers:
The number of rides for each city type.
The fares for each city type.
The number of drivers for each city type.
Create a pie chart that visualizes each of the following data for each city type:
The percent of total fares.
The percent of total rides.
The percent of total drivers.

In the second analysis, first code was refactored the code from Pyber to create a summary DataFrame for total rides, total drivers, total fares, and averages

```
# Get total rides by city type
total_rides = pyber_data_df.groupby(["type"]).count()["ride_id"]

#Get total drivers by city type
total_drivers =  city_data_df.groupby(["type"]).sum()["driver_count"]

```

** Refactored Code Alert!** Code from School_District_Analysis was refactored to clean up the DataFrame

Caution! knowing when to use count() vs sum()
using city_data_df vs pyber_data

Next, using groupby() pivot(), resample(), and loc() a  DataFrame was created to be used for a multi line graph showing total fares for each week by city type

** The index must be reset to a datetime datatype in order to resample() the DataFrame into weekly bins**

Results: Using images from the summary DataFrame and multiple-line chart, describe the differences in ride-sharing data among the different city types.
Summary: Based on the results, provide three business recommendations to the CEO for addressing any disparities among the city types.
