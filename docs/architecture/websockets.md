## Overview

| Direction | Topic | 
|-----------|-------|
| **WebClient &rarr; Server** | `/data/realtime` |
| **Server &rarr; WebClient** | `measurements` |
| **Server &rarr; WebClient** | `notification` |

## 1. WebClient &rarr; Server

The following messages will be send from the **WebClient** to the **Server**

### 1.1 /data/realtime (Start)

Request realtime data from a sensor by its `device_id`

Topic: `startRealtime`<br>
Message:

```javascript
{
    "device_id": "rpi-1",
    "status" : true
}
```

### 1.2 /data/realtime (Stop)

Close realtime data connection from a sensor by its `device_id`, for example the user switches the view.

Topic: `stopRealtime`<br>
Message:

```javascript
{
    "device_id": "rpi-1",
    "status" : false
}
```


## 2. Server &rarr; WebClient

The following messages will be send from the **Server** to the **WebClient**.

### 2.1 Forward measurements

Forwards the realtime data from the server to the WebClient

Topic: `measurements`<br>
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

### 2.2 Send notification

The server sends a notification, which opens automatically a (Bootstrap) *Alert* in the WebClient, if the user was subscripted to a sensor and the post-processing triggered a threshold.

Topic: `notification`<br>
Message:

```javascript
{ 
    "subscription_id": 6,
    "threshold_id": 3,
    "creator": "nicho90",
    "description": "Yamaha MT-03 (2015)",
    "category": "MOTORBIKE",
    "level": "danger",
    "device_id": "rpi-3",
    "height": 412
}
```
