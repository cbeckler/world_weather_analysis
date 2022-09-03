# WeatherPy with Python APIs

## Overview of Project

### Purpose

The analyst used Python APIs combined with the `pandas`, `citipy`, and `gmaps` libraries to build an app to help users plan a vacation based on their ideal temperature range. 

### Methods

A database of cities worldwide was generated using `np.random` to get a list of 2000 random coordinate pairs. `citipy` was then used to get the name of the nearest city to the coordinates, if one existed. 749 cities were found based off the randomized coordinates. A JSON of the information for each city was then extracted using the OpenWeatherMap API, skipping cities not present in the API's data. Following these exclusions, a dataframe was created for the 691 remaining cities and their weather information, and exported as a csv.

The final dataset was arranged like so:

![city data dataframe](https://github.com/cbeckler/world_weather_analysis/blob/main/Resources/city_data%20df.png)

The code for these steps may be found [here](https://github.com/cbeckler/world_weather_analysis/blob/main/Weather_Database/Weather_Database.ipynb).

Narrowing down the cities for user's vacation preferences was done by asking users to input their desired high and low temperatures, and then creating a new preferred_cities dataframe with cities whose max temperatures fell within that range. For testing purposes, a temperature range of 75-85 F was set. 

Data for a suggested hotel to stay in for each city in this preferred_cities data was extracted using Google's place `nearbysearch` API. The extracted hotel name was added to the preferred_cities data, and cities with no hotel suggestions were dropped. The data was then exported as a csv.

The final preferred_cities dataset was arranged like so:

![hotel data dataframe](https://github.com/cbeckler/world_weather_analysis/blob/main/Resources/hotel_df.png)

The code for these steps may be found [here](https://github.com/cbeckler/world_weather_analysis/blob/main/Vacation_Search/Vacation_Search.ipynb).

Finally, a vacation itinerary was planned. Using a `gmap` of the preferred_cities data, four cities within the same country that was roughly near each other were manually selected as destinations. The coordinates for each city were extracted as a tuple, which were then used to create a `gmap` directions layer. Finally, a dataframe with just the four suggested cities was created and the information from it was used to extract information and create a labeled map.

The code for these steps may be found [here](https://github.com/cbeckler/world_weather_analysis/blob/main/Vacation_Itinerary/Vacation_Itinerary.ipynb).

## Deliverables

This program returned a travel itinerary map:

![itinerary map](https://github.com/cbeckler/world_weather_analysis/blob/main/Vacation_Itinerary/WeatherPy_travel_map.png)

and a map with interactive markers to give addtional information about the cities selected:

![city map](https://github.com/cbeckler/world_weather_analysis/blob/main/Resources/less_ugly_map.png)
