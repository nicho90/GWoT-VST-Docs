## Overview

| Direction | Topic | 
|-----|-------|
| **WebClient &rarr; Server** | `startRealtime` |
| **WebClient &rarr; Server** | `stopRealtime` |
| **Server &rarr; WebClient** | `measurements` |
| **Server &rarr; WebClient** | `notification` |

## 1. WebClient &rarr; Server

The following messages will be send from the **WebClient** to the **Server**

### 1.1 Realtime (Start)

Request realtime data from a sensor by its `id`

Topic: `startRealtime`<br>
Message:

```javascript
{
    "sensor_id": 1,
    "device_id": "rpi-1"
}
```

### 1.2 Realtime (Stop)

Close realtime data connection from a sensor by its `id`, for example the user switches the view.

Topic: `stopRealtime`<br>
Message:

```javascript
{
    "sensor_id": 1,
    "device_id": "rpi-1"
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
    "sensor_id": 1,
    "device_id": "rpi-1",
    "distance": 42,
    "timestamp": "2016-05-05T12:35:03.644Z"
}
```

### 2.2 Send notification

The server sends a notification, which opens automatically a (Bootstrap) *Alert* in the WebClient, if the user was subscripted to a sensor and the post-processing triggered a threshold.

Topic: `notification`<br>
Message:

```javascript
{   
    "username": "vst-admin"
    "sensor_id": 1,
    "device_id": "rpi-1",
    "distance": 21,
    "timestamp": "2016-05-05T12:36:22.112Z"
}
```
