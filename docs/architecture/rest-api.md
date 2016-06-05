## Overview

| Endpoint | Method | Headers | Query |
|----------|--------|---------|-------|
| `/api/login` | **POST** | |
| `/api/users` | **GET** | Admin-Token | |
| `/api/users` | **POST** | | |
| `/api/users/:username` | **GET** | User-Token | |
| `/api/users/:username` | **PUT** | User-Token | |
| `/api/users/:username` | **DELETE** | User-Token | |
| &#128679; `/api/users/:username/sensors` | **GET** | User-Token | |
| `/api/users/:username/sensors` | **POST** | User-Token | |
| `/api/users/:username/sensors/:sensor_id` | **GET** | User-Token | |
| `/api/users/:username/sensors/:sensor_id` | **PUT** | User-Token | |
| `/api/users/:username/sensors/:sensor_id` | **DELETE** | User-Token | |
| `/api/users/:username/thresholds`| **GET** | User-Token | |
| `/api/users/:username/thresholds`| **POST** | User-Token | |
| `/api/users/:username/thresholds` | **DELETE** | User-Token | |
| `/api/users/:username/thresholds/:threshold_id` | **GET** | User-Token | |
| `/api/users/:username/thresholds/:threshold_id` | **PUT** | User-Token | |
| `/api/users/:username/thresholds/:threshold_id` | **DELETE** | User-Token | |
| `/api/users/:username/subscriptions` | **GET** | User-Token | |
| `/api/users/:username/subscriptions` | **POST** | User-Token | |
| `/api/users/:username/subscriptions` | **DELETE** | User-Token | |
| `/api/users/:username/subscriptions/:subscription_id` | **GET** | User-Token | |
| `/api/users/:username/subscriptions/:subscription_id` | **PUT** | User-Token | |
| `/api/users/:username/subscriptions/:subscription_id` | **DELETE** | User-Token | |
| &#128679; `/api/sensors` | **GET** | (User-Token) | `?bbox=` <br> `[(0.0, 0.0),` <br> `(0.0, 1.0),` <br> `(1.0, 1.0),` <br> `(1.0, 0.0)]` &#128679; |
| `/api/sensors/:sensor_id` | **GET** | (User-Token) | |
| `/api/sensors/:sensor_id/related_sensors` | **GET** | (User-Token) | |
| `/api/sensors/:sensor_id/measurements` | **GET** | (User-Token) | `?latest=true` <br> `?minimum=true` <br> `?maximum=true` |
| `/api/sensors/:sensor_id/measurements` | **DELETE** | User-Token | |
| `/api/sensors/:sensor_id/measurements/:measurement_id` | **DELETE** | (User-Token) | |
| `/api/sensors/:sensor_id/timeseries` | **GET** | | `?hours=1`, <br> `?hours=24`, <br> `?days=1`, <br> `?days=24`, <br>`?weeks=1`, <br>`?weeks=3`, <br> `?months=1`, <br> `?months=3`, <br> `?months=12`, <br> `?years=1`, <br> `?years=3` |
| `/api/sensors/:sensor_id/service_stations` | **GET** | (User-Token) | |
| `/api/sensors/:sensor_id/emergency_stations` | **GET** | (User-Token) | |
| `/api/service_stations` | **GET** | `?lng=0.0` <br> `&lat=0.0` <br> **required** | |
| `/api/service_stations` | **POST** | Admin-Token | |
| `/api/service_stations/:service_station_id` | **GET** | | |
| `/api/service_stations/:service_station_id` | **PUT** | Admin-Token | |
| `/api/service_stations/:service_station_id` | **DELETE** | Admin-Token | |
| `/api/emergency_stations` | **GET** | `?lng=0.0` <br> `&lat=0.0` <br> **required** | |
| `/api/emergency_stations` | **POST** | Admin-Token | |
| `/api/emergency_stations/:emergency_station_id` | **GET** | | |
| `/api/emergency_stations/:emergency_station_id` | **PUT** | Admin-Token | |
| `/api/emergency_stations/:emergency_station_id` | **DELETE** | Admin-Token | |
| `/api/vehicles` | **GET** | | `?category=bike`, <br> `?category=car`, <br> etc. |
| `/api/vehicles` | **POST** | Admin-Token | |
| `/api/vehicles/:vehicle_id` | **GET** | | |
| `/api/vehicles/:vehicle_id` | **PUT** | Admin-Token | |
| `/api/vehicles/:vehicle_id` | **DELETE** | Admin-Token | |
| `/api/vehicles` | **POST** | Admin-Token | |
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
