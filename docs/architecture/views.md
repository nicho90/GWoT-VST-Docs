## Views

Overview of the WebClient-Views:


| Endpoint | Function |
|----------|----------|
| `/` | Map with Sensors with real-time-data, when a user clicks on a sensor |
| `/new/user` | Registration formular for new user |
| `/users` | [onyl for admin] Overview of all registered users |
| `/users/:username` | Profile of a User |
| `/users/:username/edit` | Formular to change the profile of a User |
| `/new/sensor` | Formular to change the profile of a User |
| `/sensors` | Overview of all sensors |
| `/sensors/:sensor_id` | Timeseries & Settings-Overview of a sensor & Map-View [& onyl for admins: overview of all subscribers] |
| `/sensors/:sensor_id/subscribe` | user subscription for sensor [onyl for admins: overview of all subscribers] |
| `/sensors/:sensor_id/edit` | [onyl for admin or creator] change sensor settings |