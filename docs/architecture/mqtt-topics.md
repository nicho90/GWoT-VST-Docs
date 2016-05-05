## MQTT-Topics

Overview of all MQTT-Topics and messages:

#### Server -> Sensor

The following messages will be send from the **Server** to the **Sensor**. All sensors have to be subscribed to all of the following topics:

| Topic | Message | Function |
|----------|--------|----------|
| `data/realtime/start` | ```{"sensor_id": 1 }``` | Request sensor to start realtime measuring and publish the results back to the server |
| `data/realtime/stop` | `{"sensor_id": 1 }` | Request sensor to stop realtime measuring |
| `settings` | `{"sensor_id": 1, "interval": 1000 }` | Publish settings to sensor to enter a new measuring-interval |

#### Sensor -> Server

The following messages will be send from the **Sensor** to the **Server**. The server with its built MQTT-Broker, has to be subscribed to all of the following topics:

| Topic | Message | Function |
|----------|--------|----------|
| `sensor/realtime/measurement` | ```{"sensor_id": 1, "value": 120, "timestamp": 1462449511 }``` | Publishes realtime data from the sensor to the server, which will be forwarded then to the WebClient |
| `sensor/default/measurement` | ```{"sensor_id": 1, "value": 120, "timestamp": 1462449512 }``` | Publishes default measurement form the sensor to the server, which will be saved in the Database for time-series |
