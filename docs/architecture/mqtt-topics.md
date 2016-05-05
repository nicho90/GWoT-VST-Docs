## MQTT-Topics

Overview of all MQTT-Topics and messages:

#### Server -> Sensor

The following messages will be send from the **Server** to the **Sensor**. All sensors have to be subscribed to all of the following topics:

| Topic | Message | Function |
|----------|--------|----------|
| `data/realtime` | `{"sensor_id": 1, "value" : 1 }` | Request a sensor by its `sensor_id` to start realtime measuring and publish the results back to the server |
| `data/realtime` | `{"sensor_id": 1, "value" : 0 }` | Request a sensor by its `sensor_id` to stop realtime measuring (this message will be send from the Server, when all Websocket-Connections are closed for this sensor) |
| `settings` | `{"sensor_id": 1, "interval": 1000 }` | Publish new settings to a sensor by its `sensor_id` to change for example the measuring-frequency |

#### Sensor -> Server

The following messages will be send from the **Sensor** to the **Server**. The server with its built-in MQTT-Broker, has to be subscribed to all of the following topics:

| Topic | Message | Function |
|----------|--------|----------|
| `sensor/realtime/measurement` | `{`<br>&ensp;`"type":"FeatureCollection",`<br>&ensp;`"features":[{`<br>&ensp;&ensp;`"type":"Feature",`<br>&ensp;&ensp;`"geometry":{`<br>&ensp;&ensp;&ensp;`"type":"Point",`<br>&ensp;&ensp;&ensp;`"coordinates":[7,51]`<br>&ensp;&ensp;`},`<br>&ensp;&ensp;`"properties":{`<br>&ensp;&ensp;&ensp;`"id":"rpi-1",`<br>&ensp;&ensp;&ensp;`"timestamp":"2016-05-05T12:35:03.644Z",`<br>&ensp;&ensp;&ensp;`"distance":42`<br>&ensp;&ensp;`}`<br>&ensp;`}]`<br>`}` | Publishes realtime data from the sensor to the server, which will be forwarded then to the WebClient |
| `sensor/scheduled/measurement` | `{`<br>&ensp;`"type":"FeatureCollection",`<br>&ensp;`"features":[{`<br>&ensp;&ensp;`"type":"Feature",`<br>&ensp;&ensp;`"geometry":{`<br>&ensp;&ensp;&ensp;`"type":"Point",`<br>&ensp;&ensp;&ensp;`"coordinates":[7,51]`<br>&ensp;&ensp;`},`<br>&ensp;&ensp;`"properties":{`<br>&ensp;&ensp;&ensp;`"id":"rpi-1",`<br>&ensp;&ensp;&ensp;`"timestamp":"2016-05-05T12:35:03.644Z",`<br>&ensp;&ensp;&ensp;`"distance":42`<br>&ensp;&ensp;`}`<br>&ensp;`}]`<br>`}` | Publishes default measurement form the sensor to the server, which will be saved in the Database for time-series |
