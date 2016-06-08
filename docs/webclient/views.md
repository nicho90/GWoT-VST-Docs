## Overview

Overview of the WebClient-Views:

| Endpoint | Function |
|----------|----------|
| `/` | Map with Sensors |
| `/new/user` | Sign up for application |
| `/users/:username` | Profile of a User and show the Users sensors, thresholds and subscriptions |
| `/users/:username/edit` | Change the profile and set settings of a User |
| `/new/threshold` | Create a new Threshold |
| `/new/sensor` | Create a new Sensor |
| `/sensors` | List of all sensors |
| `/sensors/:sensor_id` | Details of a Sensor, with its settings, current water level, weather conditions and Chart with timeseries, real-time-data and subscripted thresholds of a User |
| `/sensors/:sensor_id/edit` | Change the settings of a sensor |
