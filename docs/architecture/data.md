The following images gives an overview of the relationships of our data, which we store in the PostgreSQL-Database. The main entities (tables) are:

1. Users
2. Thresholds
3. Sensors
4. Measurements
4. Subscriptions
5. Vehicles

All other entities are optional and might be not used in the project, depending on the time, we have. But these entities can enrich the existing data, to build a much smarter application.
With additional datasets, the application is able to find the next *Emergency stations* or *Service Stations* to a sensor by using spatial queries of PostGIS. This information is helpful, if the user plans his trip and might get in trouble when crossing a floodway. If he recognized that the next *Emergency* or *Service Station* is about 100km away, he will maybe overthink the crossing or take a different route.
Regarding routing for vehicles, the relationship *has_neighbour* or *belongs_to* the same *River system* can be used to find the next possible river-crossing, which might be still usable during a flood.

![relationships](../img/relationships.png)
