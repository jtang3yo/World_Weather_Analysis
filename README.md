# World_Weather_Analysis
## Overview and Background 
1. Overview 
  * Deliverable 1: Retrieve Weather Data
  * Deliverable 2: Create a Customer Travel Destinations Map
  * Deliverable 3: Create a Travel Itinerary Map
2. Background
  Jack loves the PlanMyTrip app. Beta testers love it too. And, as with any new product, they’ve recommended a few changes to take the app to the next level. Specifically, they recommend adding the weather description to the weather data you’ve already retrieved in this module. Then, you'll have the beta testers use input statements to filter the data for their weather preferences, which will be used to identify potential travel destinations and nearby hotels. From the list of potential travel destinations, the beta tester will choose four cities to create a travel itinerary. Finally, using the Google Maps Directions API, you will create a travel route between the four cities as well as a marker layer map.

## Analysis 
1. Deliverable 1: Retrieve Weather Data 
  * Create a new set of 2,000 random latitudes and longitudes and get the nearest cities. 
    Coordinates![image](https://user-images.githubusercontent.com/82353749/119246794-73d54080-bb52-11eb-8536-ae5ac9a222c5.png)
  * Make OpenWeatherMap API Call. 
    OpenweatherAPIcall![image](https://user-images.githubusercontent.com/82353749/119246818-af700a80-bb52-11eb-9a9a-4fa69221e048.png)
  * Retrieve the following information from the API call:
    (1) Latitude and longitude
    (2) Maximum temperature
    (3) Percent humidity
    (4) Percent cloudiness
    (5) Wind speed
    (6) Weather description (for example, clouds, fog, light rain, clear sky)
    Retrieve data from Openweather_1![image](https://user-images.githubusercontent.com/82353749/119246888-2c02e900-bb53-11eb-98a3-e29507797ce5.png)
  * Add data into DataFrame and save it into Weather_Database/WeatherPy_Database.csv 
    WeatherPy_dataframe![image](https://user-images.githubusercontent.com/82353749/119246912-71bfb180-bb53-11eb-85f0-d23b66cc604e.png)

2. Deliverable 2: Create a Customer Travel Destination Map 
  * Import WeatherPy_Database.csv file and create input box statements for Min and Max Temperatures as 70 and 90 degrees. 
    Min and Max Temp ![image](https://user-images.githubusercontent.com/82353749/119247010-4c7f7300-bb54-11eb-9fe5-56ab6e7d4a93.png)
  * Use the loc method to filter the city_data_df DataFrame for temperature criteria collected in Step 2, then create a new DataFrame called preferred_city_data.
    preferred_city_data![image](https://user-images.githubusercontent.com/82353749/119247050-a7b16580-bb54-11eb-8464-a64b754615d3.png)
  * Create DataFrame called hotel_df to store hotel names along with city, country, max temp, and coordinates.
    Hotel_df![image](https://user-images.githubusercontent.com/82353749/119247088-f3640f00-bb54-11eb-81b2-14b6bb902e0a.png)
  * Set parameters to search for hotels with 5000 meters, iterate through the hotel DataFrame and store the data retrieved in a dataframe. 
    params![image](https://user-images.githubusercontent.com/82353749/119247662-9454c900-bb59-11eb-88c4-306af99efb8b.png)
  * Drop the rows where there is no Hotel Name, replace the empty strings with np=nan before dropna(). 
    Drop null![image](https://user-images.githubusercontent.com/82353749/119247748-57d59d00-bb5a-11eb-9b26-776678c1e769.png)
  * Export the dataframe and save in output WeatherPy_Vacation.csv file. 
    clean_hotel_df![image](https://user-images.githubusercontent.com/82353749/119247851-12659f80-bb5b-11eb-8a61-0914b5c4ef9e.png)
  * Use info_box_template and retrieve city name, the country code, the weather description, and the maximum temperature for the city into hotel_info list
    hotel_info fig![image](https://user-images.githubusercontent.com/82353749/119248135-30cc9a80-bb5d-11eb-9523-f7be4891d733.png)

3. Deliverable 3: Create a Travel Itinerary Map 
  Use the Google Directions API to create a travel itinerary that shows the route between four cities chosen from the customer’s possible travel destinations. Then, create a marker layer map with a pop-up marker for each city on the itinerary.
  * Read the WeatherPy_vacation.csv into a DataFrame.
    read csv file![image](https://user-images.githubusercontent.com/82353749/119248309-4d1d0700-bb5e-11eb-9ab3-8b31fa6c389a.png)
  * Using the template add the city name, the country code, the weather description and maximum temperature for the city, and show the fig. 
    vacation_df  with marker and heatmap layer![image](https://user-images.githubusercontent.com/82353749/119248373-b735ac00-bb5e-11eb-8fdf-73d152e019e3.png)
    WeatherPy_travel_map.png![image](https://user-images.githubusercontent.com/82353749/119248381-c7e62200-bb5e-11eb-9081-127af46e4acb.png)
  * I was going to visit Mexico for the Day of the Dead, because of covid, everything seized, so I choose Topolobampo, Las Choapas, Ixtapa, La Cruz, Topolobampo for a roundtrip. Create DataFrames for each city by filtering the 'vacation_df' using the loc method. 
    picked start_end_stops![image](https://user-images.githubusercontent.com/82353749/119248463-4ba00e80-bb5f-11eb-9446-6db4c2d48095.png)
  * Get the latitude-longitude pairs as tuples from each city DataFrame using the to_numpy function and list index. 
    get lats and lngs of start_end_stops![image](https://user-images.githubusercontent.com/82353749/119248493-8013ca80-bb5f-11eb-9d83-b688c7c2a9de.png)
  * reate a direction layer map using the start and end latitude-longitude pairs, and stop1, stop2, and stop3 as the waypoints. The travel_mode should be "DRIVING", "BICYCLING", or "WALKING". I chose "Bicycling" as travel_mode, which might be a little bit unrealistic. 
    Route![image](https://user-images.githubusercontent.com/82353749/119248531-bf421b80-bb5f-11eb-974b-659048b05c00.png)
  * Combine the four city DataFrames into one DataFrame using the concat() function.
    Vacation itineary![image](https://user-images.githubusercontent.com/82353749/119248552-eb5d9c80-bb5f-11eb-89f0-b87fc594a8c9.png)
  * Get the data from each row and add it to the formatting template and store the data in a list, and add a marker layer for each city to the map.
    vacation_itinerary_markers![image](https://user-images.githubusercontent.com/82353749/119248582-1a740e00-bb60-11eb-8427-6931f6f0b9ca.png)
    WeatherPy_travel_map_markers.png![image](https://user-images.githubusercontent.com/82353749/119248704-e9480d80-bb60-11eb-9f77-a35034ddc114.png)



