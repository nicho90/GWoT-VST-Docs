## Overview

##### Status-Codes

| Code | Meaning |
|------|---------|
| <span class="green">200</span> | Request successful |
| <span class="green">201</span> | Created |
| <span class="green">204</span> | No Content |
| <span class="red">400</span> | Bad Request |
| <span class="red">401</span> | Unauthorized |
| <span class="red">403</span> | Forbidden |
| <span class="red">404</span> | Not found |
| <span class="red">500</span> | Internal Server Error |
| <span class="blue">501</span> | Not implemented |

(Source: [https://en.wikipedia.org/wiki/List_of_HTTP_status_codes](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes), 2016-05-08)


##### Authentication

| Abbreviation | Description |
|--------------|-------------|
| `PA` | Public access |
| `LPA` | Limited public access (for example, only public sensors) |
| `UT` | User-Access-Token needed |
| `LUA` | Limited User access (for example, only own sensors) |
| `AT` | Admin-Access-Token needed |
| `AO` | Admin only |


##### Endpoints

| Code | Endpoint | Method | Headers | Query | 
|------|----------|--------|---------|-------|
| <span class="green">200</span> | `/api/login` | **POST** | PA |
| <span class="blue">501</span> | `/api/users` | **GET** | AT, AO | |
| <span class="green">201</span> | `/api/users` | **POST** | PA | |
| <span class="blue">501</span> | `/api/users` | **DELETE** (all) | AT, AO| |
| <span class="green">200</span> | `/api/users/:username` | **GET** | UT, AT | |
| <span class="green">200</span> | `/api/users/:username` | **PUT** | UT, AT | |
| <span class="green">204</span> | `/api/users/:username` | **DELETE** | UT, AT | |
| <span class="green">200</span> | `/api/users/:username/sensors` | **GET** | UT, AT | |
| <span class="green">201</span> | `/api/users/:username/sensors` | **POST** | UT, AT | |
| <span class="green">204</span> | `/api/users/:username/sensors` | **DELETE** (all) | UT, AT | |
| <span class="green">200</span> | `/api/users/:username/sensors/:sensor_id` | **GET** | UT, AT | |
| <span class="green">200</span> | `/api/users/:username/sensors/:sensor_id` | **PUT** | UT, AT | |
| <span class="green">204</span> | `/api/users/:username/sensors/:sensor_id` | **DELETE** | UT, AT | |
| <span class="green">200</span> | `/api/users/:username/thresholds`| **GET** | UT, AT | |
| <span class="green">201</span> | `/api/users/:username/thresholds`| **POST** | UT, AT | |
| <span class="green">204</span> | `/api/users/:username/thresholds` | **DELETE** (all) | UT, AT | |
| <span class="green">200</span> | `/api/users/:username/thresholds/:threshold_id` | **GET** | UT, AT | |
| <span class="green">200</span> | `/api/users/:username/thresholds/:threshold_id` | **PUT** | UT, AT | |
| <span class="green">204</span> | `/api/users/:username/thresholds/:threshold_id` | **DELETE** | UT, AT | |
| <span class="green">200</span> | `/api/users/:username/subscriptions` | **GET** | UT, AT | |
| <span class="green">201</span> | `/api/users/:username/subscriptions` | **POST** | UT, AT | |
| <span class="green">204</span> | `/api/users/:username/subscriptions` | **DELETE** (all) | UT, AT | |
| <span class="green">200</span> | `/api/users/:username/subscriptions/:subscription_id` | **GET** | UT, AT | |
| <span class="green">200</span> | `/api/users/:username/subscriptions/:subscription_id` | **PUT** | UT, AT | |
| <span class="green">204</span> | `/api/users/:username/subscriptions/:subscription_id` | **DELETE** | UT, AT | |
| <span class="green">200</span> | `/api/sensors` | **GET** | LPA, LUA, UT, AT | `?bbox=` <br> `[(0.0, 0.0),` <br> `(0.0, 1.0),` <br> `(1.0, 1.0),` <br> `(1.0, 0.0)]` <br> **optional** (currently not implemented) |
| <span class="blue">501</span> | `/api/sensors` | **POST** | AT, AO | |
| <span class="blue">501</span> | `/api/sensors` | **DELETE** (all) | AT, AO  | |
| <span class="green">200</span> | `/api/sensors/:sensor_id` | **GET** | LPA, LUA, UT, AT | |
| <span class="blue">501</span> | `/api/sensors/:sensor_id` | **PUT** | AT, AO | |
| <span class="blue">501</span> | `/api/sensors/:sensor_id` | **DELETE** | AT, AO | |
| <span class="green">200</span> | `/api/sensors/:sensor_id/related_sensors` | **GET** | LPA, LUA, UT, AT | |
| <span class="green">200</span> | `/api/sensors/:sensor_id/measurements` | **GET** | LPA, LUA, UT, AT | `?limit=1000` **optional** |
| <span class="green">201</span> | `/api/sensors/:sensor_id/measurements` | **POST** | LUA, UT, AT | |
| <span class="green">204</span> | `/api/sensors/:sensor_id/measurements` | **DELETE** (all) | LUA, UT, AT | |
| <span class="green">200</span> | `/api/sensors/:sensor_id/measurements/:measurement_id` | **GET** | LUA, UT, AT | |
| <span class="green">200</span> | `/api/sensors/:sensor_id/measurements/:measurement_id` | **PUT** | LUA, UT, AT | |
| <span class="green">204</span> | `/api/sensors/:sensor_id/measurements/:measurement_id` | **DELETE** | LUA, UT, AT | |
| <span class="green">200</span> | `/api/sensors/:sensor_id/timeseries` | **GET** | LPA, LUA, UT, AT | `?minutes=1`, <br> `?minutes=30`, <br> `?hours=1`, <br> `?hours=24`, <br> `?days=1`, <br> `?days=24`, <br>`?weeks=1`, <br>`?weeks=3`, <br> `?months=1`, <br> `?months=3`, <br> `?months=12`, <br> `?years=1`, <br> `?years=3` **required** |
| <span class="green">201</span> | `/api/sensors/:sensor_id/timeseries` | **POST** | LUA, UT, AT | |
| <span class="green">204</span> | `/api/sensors/:sensor_id/timeseries` | **DELETE** (all) | LUA, UT, AT, AO | |
| <span class="green">200</span> | `/api/sensors/:sensor_id/statistics` | **GET** | LPA, LUA, UT, AT | |
| <span class="green">200</span> | `/api/sensors/:sensor_id/service_stations` | **GET** | LPA, LUA, UT, AT | |
| <span class="green">200</span> | `/api/sensors/:sensor_id/emergency_stations` | **GET** | LPA, LUA, UT, AT | |
| <span class="green">200</span> | `/api/service_stations` | **GET** | PA | `?lng=0.0` <br> `&lat=0.0` **required** | |
| <span class="blue">501</span> | `/api/service_stations` | **POST** | AT, AO | |
| <span class="blue">501</span> | `/api/service_stations` | **DELETE** (all) | AT, AO | |
| <span class="green">200</span> | `/api/service_stations/:service_station_id` | **GET** | PA | |
| <span class="blue">501</span> | `/api/service_stations/:service_station_id` | **PUT** | AT, AO | |
| <span class="blue">501</span> | `/api/service_stations/:service_station_id` | **DELETE** | AT, AO | |
| <span class="green">200</span> | `/api/emergency_stations` | **GET** | PA | `?lng=0.0` <br> `&lat=0.0` **required** |
| <span class="blue">501</span> | `/api/emergency_stations` | **POST** | AT, AO | |
| <span class="blue">501</span> | `/api/emergency_stations` | **DELETE** (all) | AT, AO | |
| <span class="green">200</span> | `/api/emergency_stations/:emergency_station_id` | **GET** | PA | |
| <span class="blue">501</span> | `/api/emergency_stations/:emergency_station_id` | **PUT** | AT, AO | |
| <span class="blue">501</span> | `/api/emergency_stations/:emergency_station_id` | **DELETE** | AT, AO | |
| <span class="green">200</span> | `/api/vehicles` | **GET** | PA | `?category=bike`, <br> `?category=wheelchair`, <br> `?category=scooter` <br> `?category=motorbike` <br> `?category=car` <br> `?category=bus` <br> `?category=truck` <br> **optional** |
| <span class="blue">501</span> | `/api/vehicles` | **POST** | AT, AO | |
| <span class="blue">501</span> | `/api/vehicles` | **DELETE** (all) | AT, AO | |
| <span class="green">200</span> | `/api/vehicles/:vehicle_id` | **GET** | PA | |
| <span class="blue">501</span> | `/api/vehicles/:vehicle_id` | **PUT** | AT, AO | |
| <span class="blue">501</span> | `/api/vehicles/:vehicle_id` | **DELETE** | AT, AO | |
| <span class="green">200</span> | `/api/forecast` | **GET** | PA | `?lat=0.0` <br> `&lng=0.0` <br> `&lang=en` **required** |
