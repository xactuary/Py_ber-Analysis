# PY_BER RIDE SHARING APP ANALYSIS
## SUMMARY
Using Py_ber ride sharing data, 
#### Background
The CEO of PyBer, which runs a ride sharing app, has asked the data analysts to create visualizations of ride share data in order to be able to see where the company can improve access to ride-sharing services and determine affordability for undersrerved neighborhoods.  This project creates a summary showing ride-sharing data by city type.  In addition, a graphical depiction of the data is also created.  The company is interested in seeing how the data differs by city type and how these differences can be used by decision makers at the company.  

#### DATA PROVIDED
Pyber provided 2 data files in csv format:
city_data.csv
ride_data.csv
The city data includes the number of drivers per city and type of city, broken down between Rural, Urban and Suburban all associated with the name of the city.  The ride data includes the city name and all the rides provided by date with a time stamp, and the fare paid.
  
## ANALYSIS
The two data files are first combined into one dataframe with the merge variable being the city.  This allows us to count the number of rides per city and driver counts per city, and total fares collecter per city as well as divide them into the city type.  When we have the total fare and the number of drivers in each city, we can then calculate the average are per driver by city and then overall by city type.  After dividing the data into three separate dataframes for the type of city, we can use them to do calculations separately for each type. + For example, to calcualte the average fare per driver in the urban areas we use the following script:
  
`urban_avg_fare_per_driver = urban_cities_df.groupby(["city"]).sum()["fare"]/urban_cities_df.groupby(["city"]).sum()["driver_count"]`
  
  Once these calculations have been completed by type of city, we can then combine all the statistics back into one dataframe to show the summary to the PyBer executives.  The final result is as follows:
  
![](https://github.com/xactuary/Py_ber-Analysis/blob/main/Resources/Summary%20DF.PNG)
  
This table shows that there are significantly fewer rides and drivers in the Rural areas bu thte average fare per ride and fare per Driver is significantly higher than in the Suburban and Urban settings.  However, the urban area has much higher revenue due to these significantly higher number of rides provided.  We can examine the monthly revenue stream broken down by the city types in the following graph:

