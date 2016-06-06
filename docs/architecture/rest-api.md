## Overview


##### Authentication
* `UT` - User-Access-Token
* `AT` - Admin-Access-Token
* `OA` - Only the Admin has access to this endpoint

##### Endpoints

| Endpoint | Method | Headers | Query | 
|----------|--------|---------|-------|
| `/api/login` | **POST** | |
| `/api/users` | **GET** | AT | |
| `/api/users` | **POST** | | |
| `/api/users/:username` | **GET** | UT | |
| `/api/users/:username` | **PUT** | UT | |
| `/api/users/:username` | **DELETE** | UT | |
| &#128679; `/api/users/:username/sensors` | **GET** | UT | |
| `/api/users/:username/sensors` | **POST** | UT | |
| `/api/users/:username/sensors/:sensor_id` | **GET** | UT | |
| `/api/users/:username/sensors/:sensor_id` | **PUT** | UT | |
| `/api/users/:username/sensors/:sensor_id` | **DELETE** | UT | |
| `/api/users/:username/thresholds`| **GET** | UT | |
| `/api/users/:username/thresholds`| **POST** | UT | |
| `/api/users/:username/thresholds` | **DELETE** | UT | |
| `/api/users/:username/thresholds/:threshold_id` | **GET** | UT | |
| `/api/users/:username/thresholds/:threshold_id` | **PUT** | UT | |
| `/api/users/:username/thresholds/:threshold_id` | **DELETE** | UT | |
| `/api/users/:username/subscriptions` | **GET** | UT | |
| `/api/users/:username/subscriptions` | **POST** | UT | |
| `/api/users/:username/subscriptions` | **DELETE** | UT | |
| `/api/users/:username/subscriptions/:subscription_id` | **GET** | UT | |
| `/api/users/:username/subscriptions/:subscription_id` | **PUT** | UT | |
| `/api/users/:username/subscriptions/:subscription_id` | **DELETE** | UT | |
| &#128679; `/api/sensors` | **GET** | (UT) | `?bbox=` <br> `[(0.0, 0.0),` <br> `(0.0, 1.0),` <br> `(1.0, 1.0),` <br> `(1.0, 0.0)]` &#128679; |
| `/api/sensors/:sensor_id` | **GET** | (UT) | |
| `/api/sensors/:sensor_id/related_sensors` | **GET** | (UT) | |
| `/api/sensors/:sensor_id/measurements` | **GET** | (UT) | `?latest=true` <br> `?minimum=true` <br> `?maximum=true` |
| `/api/sensors/:sensor_id/measurements` | **DELETE** | UT | |
| `/api/sensors/:sensor_id/measurements/:measurement_id` | **DELETE** | (UT) | |
| `/api/sensors/:sensor_id/timeseries` | **GET** | | `?hours=1`, <br> `?hours=24`, <br> `?days=1`, <br> `?days=24`, <br>`?weeks=1`, <br>`?weeks=3`, <br> `?months=1`, <br> `?months=3`, <br> `?months=12`, <br> `?years=1`, <br> `?years=3` |
| `/api/sensors/:sensor_id/service_stations` | **GET** | (UT) | |
| `/api/sensors/:sensor_id/emergency_stations` | **GET** | (UT) | |
| `/api/service_stations` | **GET** | `?lng=0.0` <br> `&lat=0.0` <br> **required** | |
| `/api/service_stations` | **POST** | AT | |
| `/api/service_stations/:service_station_id` | **GET** | | |
| `/api/service_stations/:service_station_id` | **PUT** | AT | |
| `/api/service_stations/:service_station_id` | **DELETE** | AT | |
| `/api/emergency_stations` | **GET** | `?lng=0.0` <br> `&lat=0.0` <br> **required** | |
| `/api/emergency_stations` | **POST** | AT | |
| `/api/emergency_stations/:emergency_station_id` | **GET** | | |
| `/api/emergency_stations/:emergency_station_id` | **PUT** | AT | |
| `/api/emergency_stations/:emergency_station_id` | **DELETE** | AT | |
| `/api/vehicles` | **GET** | | `?category=bike`, <br> `?category=car`, <br> etc. |
| `/api/vehicles` | **POST** | AT | |
| `/api/vehicles/:vehicle_id` | **GET** | | |
| `/api/vehicles/:vehicle_id` | **PUT** | AT | |
| `/api/vehicles/:vehicle_id` | **DELETE** | AT | |
| `/api/vehicles` | **POST** | AT | |
| `/api/forecast` | **GET** | | `?lat=0.0` <br> `&lng=0.0` <br> `&lang=en` **required** |


## Status-Codes

| Code | Meaning |
|------|---------|
| `200` | Request successful |
| `201` | Created |
| `204` | No Content |
| `400` | Bad Request |
| `401` | Unauthorized |
| `403` | Forbidden |
| `404` | Not found |
| `500` | Internal Server Error |
| `501` | Not implemented |

(Source: [https://en.wikipedia.org/wiki/List_of_HTTP_status_codes](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes), 2016-05-08)
