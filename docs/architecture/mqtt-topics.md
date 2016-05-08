## MQTT-Topics

Overview of all MQTT-Topics and messages:

| Direction | Topic | 
|-----|-------|
| Server -> Sensor | `data/realtime` |
| Server -> Sensor | `settings` |
| Sensor -> Server | `sensor/realtime/measurement` |
| Sensor -> Server | `sensor/scheduled/measurement` |

#### Server -> Sensor

The following messages will be send from the **Server** to the **Sensor**. All sensors have to be subscribed to all of the following topics:

##### data/realtime (Start)

Request a sensor by its `id` to start realtime measuring and publish the results back to the server

Topic: `data/realtime`

Message:

```javascript
{
    "id": "rpi-1",
    "status" : true
}
```

##### data/realtime (Stop)

Request a sensor by its `id` to stop realtime measuring (this message will be send from the Server, when all Websocket-Connections are closed for this sensor)

Topic: `data/realtime`

Message:

```javascript
{
    "id": "rpi-1",
    "status" : false
}
```

##### settings

Publish new settings to a sensor by its `id` to change for example the measuring-frequency

Topic: `settings`

Message:

```javascript
{
    "id": "rpi-1",
    "interval": 1000
}
```


#### Sensor -> Server

The following messages will be send from the **Sensor** to the **Server**. The server with its built-in MQTT-Broker, has to be subscribed to all of the following topics:

##### sensor/realtime/measurement

Publishes realtime data from the sensor to the server, which will be forwarded then to the WebClient

Topic: `sensor/realtime/measurement`

Message:

```javascript
{
    "type": "FeatureCollection",
    "features": [
        {
            "type": "Feature",
            "geometry": {
                "type":" Point",
                "coordinates": [
                    7.0,
                    51.0
                ]
            },
            "properties": {
                "id": "rpi-1",
                "timestamp": "2016-05-05T12:35:03.644Z",
                "distance": 42
            }
        }
    ]
}
```

##### sensor/scheduled/measurement

Publishes default measurement form the sensor to the server, which will be saved in the Database for time-series

Topic: `sensor/scheduled/measurement`

Message:

```javascript
{
    "type": "FeatureCollection",
    "features": [
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    7.0,
                    51.0
                ]
            },
            "properties": {
                "id": "rpi-1",
                "timestamp": "2016-05-05T12:35:03.644Z",
                "distance": 42
            }
        }
    ]
}
```
