# PyBer_Analysis
Python using matplotlib and Pandas in Jupyter Notebook

## PyBer Launch - Introduction
This analysis for ride sharing platform, Pyber, writes Python using Pandas Library and Matplotlib in Jupyter Notebook to visualize how weekly fares across city types (Urban, Suburban and Rural) differ. This code and the visualtizations can be refactored to view differences of rides by city type, number of riders by city type, and number of drivers by city allowing PyBer to improve access to ride sharing services and determine affordability by city type.

The entire project consisted of two analyses Pyber and Pyber_Challenge broken down below.

## Development
### if you fail to plan, you plan to fail
There's _alot_ of data! A quick data scan followed by writing out goals of the project helps stay organized. 

### Analysis 1
In the first analysis [Pyber.ipyng](http://localhost:8888/notebooks/PyBer_Analysis/Pyber.ipynb) an exploratory analysis ran through some very large csv data files.

Then, DataFrames were merged alongside groupby(), .count(), .sum(), .mean, to understand average fares, total rides, and total drivers by city type

```
#Sum of fares for each city type
sum_fares_by_type = pyber_data_df.groupby(["type"]).sum()["fare"]

# Ride Count for Urban Cities
urban_ride_count = urban_cities_df.groupby(["city"]).count()["ride_id"]

#Average Fare in Urban Cities
urban_avg_fare = urban_cities_df.groupby(["city"]).mean()["fare"]

```

Finally, Charts including scatter, pie and box & whiskers help visualize the story expressing outliers, city type with most activity, percentages, etc. Charts showcase relationshps between the type of city and number of drivers and riders as well as percentage of total fares of riders and drivers by type of city.


![charts](https://user-images.githubusercontent.com/79612565/115090829-c32caf00-9eca-11eb-95ba-50adc3868ac8.png)

### Analysis 2
1. In the second analysis, code was refactored from the Pyber Analysis to create a summary DataFrame for total rides, total drivers, total fares, and averages

```
# Get total rides by city type
total_rides = pyber_data_df.groupby(["type"]).count()["ride_id"]

#Get total drivers by city type
total_drivers =  city_data_df.groupby(["type"]).sum()["driver_count"]

```

**Caution!** 
- Using count() vs sum() to get totals for riders, fares and drivers will differ
- Using city_data_df vs pyber_data_df: in order to get the accurate count of drivers by city type, the city_data_df is used over merged pyber_data_df so counts aren't doubled.

**Refactored Code Ahead!** Code from School_District_Analysis was refactored to clean up the DataFrame

```
#  8. Format the columns.
pyber_summary_df["Total Rides"] = pyber_summary_df["Total Rides"].map("{:,}".format)
pyber_summary_df["Total Drivers"] = pyber_summary_df["Total Drivers"].map("{:,}".format)
pyber_summary_df["Total Fares"] = pyber_summary_df["Total Fares"].map("${:,.2f}".format)
pyber_summary_df["Average Fare per Ride"] = pyber_summary_df["Average Fare per Ride"].map("${:,.2f}".format)
pyber_summary_df["Average Fare per Driver"] = pyber_summary_df["Average Fare per Driver"].map("${:,.2f}".format)
pyber_summary_df
```

- ![Clean_DF](https://user-images.githubusercontent.com/79612565/115090845-d2136180-9eca-11eb-977d-ad78abf04781.png)

2. Next, using groupby() pivot(), resample(), and loc() a  DataFrame was created to be used for a multi line graph showing total fares for each week by city type 

** The index must be reset to a datetime datatype in order to resample() the DataFrame into weekly bins**

![Graph](https://user-images.githubusercontent.com/79612565/115090792-a8f2d100-9eca-11eb-8fcf-21565c52af1a.png)


## Wrap It Up
We can analyze these results across a 5 month multi-line graph. To start, the graph makes it easy to see that fares across rural areas are low, however the average fare per rider is the highest. Most likely this is due to rural city type having the fewest drivers, perhaps PyBer should focus on expansion across suburban and urban over the rural cities or create incentive programs to increase rider participation and drivers within the Rural areas.

Secondly, Suburban rides might be increased by building brand awareness from focusing on certain demographics such as age. By pulling rider data and formatting, we could understand what kinds of riders are most active on the app and create campaigns to capture other audiences. PyBer might also look to understand peak times such as the end of Februrary or March. If no outliers skew the total fares, we should look to understand what caused these spikes and mimic behavior.  

Finally, we can see from the DataFrame that drivers outweigh riders, creating the lowest average fare per ride, which might disincentivize drivers. PyBer might limit drivers in urban areas during certain times.

PyBer can use this code to run montly, yearly, even daily analyses and can refactor the code to be used with number  of drivers, riders and/or fares as they determine which markets to penetrate and focus.
