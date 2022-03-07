# Create a Weather App

Create a two screen weather app which shows current location weather details and next 7 days forecast. 

Use open weather public API to get current weather and next 7 days forecast details. Use the attached API key to call  “4cd569ffb3ecc3bffe9c0587ff02109f”, you can also sign up to create a new free API key. 

# Example API Call:

Current weather using device coordinates:

**API**: 
https://api.openweathermap.org/data/2.5/weather?lat=35&lon=139&appid=4cd569ffb3ecc3bffe9c0587ff02109f


**Response**: 
```
{
  "coord": {
    "lon": -122.08,
    "lat": 37.39
  },
  "weather": [
    {
      "id": 800,
      "main": "Clear",
      "description": "clear sky",
      "icon": "01d"
    }
  ],
  "base": "stations",
  "main": {
    "temp": 282.55,
    "feels_like": 281.86,
    "temp_min": 280.37,
    "temp_max": 284.26,
    "pressure": 1023,
    "humidity": 100
  },
  "visibility": 16093,
  "wind": {
    "speed": 1.5,
    "deg": 350
  },
  "clouds": {
    "all": 1
  },
  "dt": 1560350645,
  "sys": {
    "type": 1,
    "id": 5122,
    "message": 0.0139,
    "country": "US",
    "sunrise": 1560343627,
    "sunset": 1560396563
  },
  "timezone": -25200,
  "id": 420006353,
  "name": "Mountain View",
  "cod": 200
  }    
  ```
  
# Forecast API
To display Next 7 days forecast 

**API**
https://api.openweathermap.org/data/2.5/onecall?lat=33.44&lon=-94.04&appid=4cd569ffb3ecc3bffe9c0587ff02109f

**Response**: 
```                   
{
   "city":{
      "id":2643743,
      "name":"London",
      "coord":{
         "lon":-0.1258,
         "lat":51.5085
      },
      "country":"GB",
      "population":0,
      "timezone":3600
   },
   "cod":"200",
   "message":0.7809187,
   "cnt":7,
   "list":[
      {
         "dt":1568977200,
         "sunrise":1568958164,
         "sunset":1569002733,
         "temp":{
            "day":293.79,
            "min":288.85,
            "max":294.47,
            "night":288.85,
            "eve":290.44,
            "morn":293.79
         },
         "feels_like":{
            "day":278.87,
            "night":282.73,
            "eve":281.92,
            "morn":278.87
         },
         "pressure":1025.04,
         "humidity":42,
         "weather":[
            {
               "id":800,
               "main":"Clear",
               "description":"sky is clear",
               "icon":"01d"
            }
         ],
         "speed":4.66,
         "deg":102,
         "gust": 5.3,
         "clouds":0,
         "pop":0.24
      },
      ....

```

# Design:

![Weather](https://user-images.githubusercontent.com/36688362/156924318-ac608095-a700-4e84-9654-a74906248568.png)

1. Show current location weather details in home screen
2. Use collection view to display 7 days forecast 
3. On click of next days button, navigate to forecast screen to display next 7 days forecast details 
4. Expected to follow MVC architecture. 
5. Expected to Design the UI as close as possible.


# Home Screen:

In blue card, show current weather details like 

1. Cloud image can be changed by referring **weather -> main** key from above json
2. **main -> temp** is to show current temperature in Fahrenheit, convert Fahrenheit to Celsius 
3. **wind -> speed** is used for wind speed
4. **Main ->  feels_like** is used to for feels like which is in Fahrenheit, convert Fahrenheit to Celsius
5. Instead of UV index, please show **sys ->  sunrise**, convert timestamp to Date object to display the date in hh:mm
6. **main -> pressure** to display pressure
7. Under blue card use the collection view to display 7 days forecast details by call forecast API and the first cell in the collection view should display current day’s weather and time in hh:mm format.
8. Use **hourly -> dt** key to display the hourly date in collection view in hh:mm format

# Next 7 days Screen:

 On click on next 7 days button, navigate to forecast details button and use table view to display all 7 forecasts using **daily** key from forecast API
 
 1.  Use **dt** key to display the date in EEEE, dd MMM
 2.  For Max temp **temp -> Max**, Min temp **temp -> Max**,both values are in Fahrenheit which needs to convert to Celsuis
