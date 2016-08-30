## Overview

| Direction | Topic |
|-----------|-------|
| **Server &rarr; Sensor** | `/data/realtime` |
| **Server &rarr; Sensor** | `/settings` |
| **Sensor &rarr; Server** | `/sensor/realtime/measurement` |
| **Sensor &rarr; Server** | `/sensor/scheduled/measurement` |

## 1. Server &rarr; Sensor

The following messages will be send from the **Server** to the **Sensor**. All sensors have to be subscribed to all of the following topics:

### 1.1 /data/realtime (Start)

Request a sensor by its `device_id` to start realtime measuring and publish the results back to the server

Topic: `data/realtime`<br>
Message:

```javascript
{
    "device_id": "rpi-1",
    "status" : true
}
```

### 1.2 /data/realtime (Stop)

Request a sensor by its `device_id` to stop realtime measuring (this message will be send from the Server, when all Websocket-Connections are closed for this sensor)

Topic: `data/realtime`<br>
Message:

```javascript
{
    "device_id": "rpi-1",
    "status" : false
}
```

### 1.3 /settings

Publish new settings to a sensor by its `id` to change for example the measuring-frequency

Topic: `settings`<br>
Message:

```javascript
{
    "id": "rpi-1",
    "interval": 1000
}
```


## 2. Sensor &rarr; Server

The following messages will be send from the **Sensor** to the **Server**. The server with its built-in MQTT-Broker, has to be subscribed to all of the following topics:

### 2.1 /sensor/realtime/measurement

Publishes realtime data from the sensor to the server, which will be forwarded then to the WebClient

Topic: `sensor/realtime/measurement`<br>
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

### 2.2 /sensor/scheduled/measurement

Publishes default measurement form the sensor to the server, which will be saved in the Database for time-series

Topic: `sensor/scheduled/measurement`<br>
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
