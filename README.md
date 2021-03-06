# PY_BER RIDE SHARING APP ANALYSIS
## SUMMARY
Using Py_ber ride sharing data, this project examines the difference in fares per ride and driver between different types of cities. 
#### Background
The CEO of PyBer, which runs a ride sharing app, has asked the data analysts to create visualizations of ride share data in order to be able to see where the company can improve access to ride-sharing services and determine affordability for underserved neighborhoods.  This project creates a summary showing ride-sharing data by city type.  In addition, a graphical depiction of the data is also created.  The company is interested in seeing how the data differs by city type and how these differences can be used by decision makers at the company.  

#### DATA PROVIDED
Pyber provided 2 data files in csv format:
  
1.  city_data.csv
2.  ride_data.csv
  
The city data includes the number of drivers per city and type of city, broken down between Rural, Urban and Suburban all associated with the name of the city.  The ride data includes the city name and all the rides provided by date with a time stamp, and the fare paid.
  
## ANALYSIS
The two data files are first combined into one dataframe with the merge variable being the city.  This allows us to count the number of rides per city and driver counts per city, and total fares collected per city as well as divide them into the city type.  When we have the total fare and the number of drivers in each city, we can then calculate the average fare per driver by city and then overall by city type.  After dividing the data into three separate dataframes for the type of city, we can use them to do calculations separately for each type. For example, to calcualte the average fare per driver in the urban areas we use the following script:
  
>`urban_avg_fare_per_driver = urban_cities_df.groupby(["city"]).sum()["fare"]/urban_cities_df.groupby(["city"]).sum()["driver_count"]`
  
  Once these calculations have been completed by type of city, we can then combine all the statistics back into one dataframe to show the summary to the PyBer executives.  The final result is as follows:
  
![](https://github.com/xactuary/Py_ber-Analysis/blob/main/Resources/Summary%20DF.PNG)
  
This table shows that there are significantly fewer rides and drivers in the Rural areas but the average fare per ride and fare per driver is significantly higher than in the Suburban and Urban settings.  However, the Urban area has much higher revenue due to these significantly higher number of rides provided.  We can examine the monthly revenue stream broken down by the city types in the following graph:

![](https://github.com/xactuary/Py_ber-Analysis/blob/main/analysis/Fig11.png)
  
The code used to create the graph includes some adjustments to the default style legend in order to fit it on the graph.  In addition, the graph is stretched out so it is easier to see the trends.  The following is the code used to create this depiction.

>'ax = Week_fare_df.plot(figsize=(15,5))
>ax.set_title("Total Fare by City Type")
>ax.set_ylabel('Fare($USD)')
>ax.set_xlabel('Date')
>ax.legend(loc='center',fontsize='small')`  

The graph shows that the rural fares per month are fairly steady throughout the time period whereas the Urban fares have more peaks and troughs.  The suburban fares are somewhere in the middle. 

##  SUMMARY

Based on the above information, the following are three recommendations that PyBer might consider.

>1.  As noted above, for the rural areas, the average fare per ride is much higher than for Suburban and Urban cities. This discrepancy may be due to the longer distances traveled in rural areas.  PyBer should gather the data on miles driven and cost per mile to compare between the types of cities.  They should also look at the statistics of total rides per population in the areas to see if there is less use just due to population density issues or whether it is an affordability issue.  
  
>2. At the same time, the average fare per driver in rural areas is much higher.  This implies that there are many fewer drivers in the Rural areas so individual drivers are taking on more fares than in the urban area where each driver earns significantly less.  PyBer should consider recruiting more drivers in the rural areas which might increase the number of riders and provide more service to what may be an underserviced area.
  
>3.  For Urban areas, the average fare per driver is fairly low at less than half that of Suburban drivers.  The average fare per ride, however, is more than half that for Suburban drivers.  So it appears that there may be too many drivers in the Urban areas which is leading to the drivers not making as much money.  So it looks like the supply of drivers is out of balance between the different areas.  Moving some drivers from urban to suburban and rural areas may even out the supply.





