# A web-based Deep Learning prediction model for rideshare demand based on weather conditions

Major rideshare platforms such as Uber and Lyft implement pricing schemes such as surge pricing and prime time, where passengers pay a higher rate for the ride during times of high demand; this higher pricing scheme incentivizes the drivers to provide service in inclement conditions in order to meet the ride request demand. Here, I propose to develop a web-based Deep Learning prediction model that uses real-time weather condition data and weather forecast to predict the change in rideshare demand in different locations of the city. The model will be trained based on non-weather-related variables affecting the demand such as day of the weak, hour of day, public events, city hotspots, and will project the changes in demand based on changes in weather conditions compare to normal baseline demand. The model can be used to calculate the price surges based on projected demand, ahead of time, and inform the rideshare platform and drivers of increased profit opportunities in certain times/locations.

For the purpose of preliminary data exploration, a sample data of 693000 Uber and Lyft rides and associated weather data for Boston, MA is analyzed here. However, for the capstone project, I propose to use a larger dataset obtained from Uber and Lyft for multiple major US cities, as well as weather data from NOAA, to develop the proposed prediction model. For real-time weather data, I’ll use the hourly data from ClimaCell’s weather API (www.climacell.co/weather-api/). The free tier subscription allows access to 1000 calls per day (100/hour limit), which is enough for the purpose of this project. I will develop a web-based model to obtain location-based real-time weather data and hourly forecasts ClimaCell’s weather API and use the information as inputs to the predictive model to forecast the ride demand over the coming hours.


### Exploratory Analysis:

For initial exploratory purposes, I use Uber and Lyft rideshare dataset for Boston, MA From 11-26-2018 to 12-18-2018. The dataset contains 693000 data points and contains ride information such as ride time, ride source and destination, ride type (shared, regular X, luxury, SUV, etc), and price surge multiplier. The dataset also includes weather information at the time of ride request. The weather features include: temperature, precipitation intensity, humidity, cloud cover, descriptive weather conditions (rainy, sunny, overcast, drizzle, ect), as well as the coordinates (latitude-longitude) of the ride’s source.

The preliminary exploratory analysis shows that the number of rides during the cloudy and overcast weather conditions is the highest, compared to clear weather conditions. Price surge multipliers are also highest during the cloudy conditions, which shows that the rideshare platforms are met with higher demand and hence increase the ride fares. The temperature histogram also shows that there’s a clear peak in the number of rides associated with certain temperature intervals. However, in order to correlate temperature and ride numbers, we would need a broader data samples that cover all months of the year, since the current dataset only covers November and December rides.

![Alt text](https://raw.githubusercontent.com/behzadasd/TDI/master/Figs/TDI_Rides_WeatherCondition.png)

![Alt text](https://raw.githubusercontent.com/behzadasd/TDI/master/Figs/TDI_Surges_WeatherCondition.png)

![Alt text](https://raw.githubusercontent.com/behzadasd/TDI/master/Figs/TDI_Histograms_1.png)


The data in current format is associated for each individual ride. In order to create a time series dataset for the exploration and correlation analysis, I created a new dataset, where all the ride and weather information are aggregated for each one-hour periods, so the change in patterns of different features can be tracked. For each 1-hour timeframe, number of rides during the period is counted. The price and surge multipliers are averaged during each period to calculate the average price per hour. Numerical weather information such as temperature, precipitation intensity, humidity, dew point, wind speed, cloud coverage, UV index, ect. are also averaged per each period. For categorical features such as descriptive weather conditions, the weather conditions with the highest number of occurrences during each period is selected as the dominant weather condition of that period. 

The new aggregated data shows that number of rides per hour has the highest correlation with wind speed and air pressure. Precipitation intensity and cloud cover have also high correlation with the number of rides. However, changes in wind speed and air pressures can be explained by changes in precipitation, since the rainy weather is normally associate with higher wind speeds and low air pressure.

I will perform a broader exploratory analysis to identify the weather features that have the highest correlation with the ride demand and price surges. I will obtain a larger ride dataset from Uber and Lyft platforms to be used for training the predictive model. Hourly weather information is also publicly available through NOAA website, which can be obtained and paired with the associated ride information for each time period. In the next step, I’ll develop and train a Deep Learning Neural Network model using Keras to predict the ride demand based on the selected weather inputs. After developing the predictive model, I will develop a web-based model to obtain location-based real-time weather data and hourly forecasts ClimaCell’s weather API and use the information as inputs to the predictive model to forecast the ride demand over the next hours.

![Alt text](https://raw.githubusercontent.com/behzadasd/TDI/master/Figs/TDI_Rides_Count_Corr.png)


![Alt text](https://raw.githubusercontent.com/behzadasd/TDI/master/Figs/TDI_Corr_all.png)




