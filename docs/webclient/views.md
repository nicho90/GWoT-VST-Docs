## Overview

Overview of the WebClient-Routes:

| Endpoint | Function |
|----------|----------|
| `/` | Main map |
| `/map/sensors/:sensor_id` | Main map and focus Sensor, by its Id |
| `/map/emergency_stations/:emergency_station_id` | Main map and focus Emergency-station, by its Id |
| `/map/service_stations/:service_station_id` | Main map and focus Service-station, by its Id |
| `/new/user` | Sign up (Registration) |
| `/users/:username` | Profile of a User (Settings, List of Users sensors, thresholds and subscriptions) |
| `/users/:username/edit` | Change the profile and set settings of a User |
| `/users/:username/tab/:tab` | Go to the profile and switch to tab (1 = Settings, 2 = Thresholds, 3 = Subscriptions, 4 = Sensors) |
| `/new/threshold` | Create a new Threshold |
| `/new/sensor` | Create a new Sensor |
| `/sensors` | List of all sensors |
| `/sensors/:sensor_id` | Details of a Sensor, with its settings, current water level, weather conditions and Chart with timeseries, real-time-data and subscripted thresholds of a User |
| `/sensors/:sensor_id/edit` | Change the settings of a sensor |
| `/help` | User guide |
| `/about` | About page |
