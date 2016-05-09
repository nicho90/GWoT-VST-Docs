## Overview

| Endpoint | Method | Headers | Query | Function |
|----------|--------|---------|-------|----------|
| `/api/users` | **POST** | | | Create a new user (User-Registration) |
| `/api/users/:username` | **GET** | Token | | | 
| `/api/users/:username` | **PUT** | Token | | |
| `/api/users/:username` | **DELETE** | Token | | |
| `/api/users/:username/sensors` | **GET** | Token | | |
| `/api/users/:username/sensors` | **POST** | Token | | |
| `/api/users/:username/sensors/:sensor_id` | **GET** | Token | | |
| `/api/users/:username/sensors/:sensor_id` | **PUT** | Token | | |
| `/api/users/:username/sensors/:sensor_id` | **DELETE** | Token | | |
| `/api/users/:username/sensors/:sensor_id/measurements/measurement_id`| **PUT** | Token | | |
| `/api/users/:username/sensors/:sensor_id/measurements/measurement_id`| **DELETE** | Token | | |
| `/api/users/:username/thresholds`| **GET** | Token | | |
| `/api/users/:username/thresholds`| **POST** | Token | | |
| `/api/users/:username/thresholds/:threshold_id` | **GET** | Token | | |
| `/api/users/:username/thresholds/:threshold_id` | **PUT** | Token | | |
| `/api/users/:username/thresholds/:threshold_id` | **DELETE** | Token | | |
| `/api/users/:username/subscriptions` | **GET** | Token | | |
| `/api/users/:username/subscriptions` | **POST** | Token | | |
| `/api/users/:username/subscriptions/:subscription_id` | **GET** | Token | | |
| `/api/users/:username/subscriptions/:subscription_id` | **PUT** | Token | | |
| `/api/users/:username/subscriptions/:subscription_id` | **DELETE** | Token | | |
| `/api/sensors` | **GET** | Token (optional) | `?bbox=[(0.0, 0.0), (0.0, 1.0), (1.0, 1.0), (1.0, 0.0)]` | |
| `/api/sensors/:sensor_id` | **GET** | Token (optional) | | |
| `/api/sensors/:sensor_id/measurements` | **GET** | Token (optional) | | |
| `/api/sensors/:sensor_id/measurements/measurement_id` | **GET** | Token (optional) | | |
| `/api/vehicles` | **GET** | | `?type=bike`, `?type=car`, etc. | List of all vehicles (bikes, cars, scooters, motorbikes, wheelchairs) or by category |
| `/api/admin/:admin_name/users` | **GET** | Token | `?sort=DESC`, `?sort=ASC` | List all users, only available for admins |
| `/api/admin/:admin_name/vehicles` | **POST** | Token | | List of all vehicles (bikes, cars, scooters, motorbikes, wheelchairs) |
| `/api/admin/:admin_name/vehicles/:vehicle_id` | **GET** | Token | | |
| `/api/admin/:admin_name/vehicles/:vehicle_id` | **PUT** | Token | | |
| `/api/admin/:admin_name/vehicles/:vehicle_id` | **DELETE** | Token | | | |


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


## 1. Users

### 1.1 GET Users

Endpoint: `/api/admin/:admin_name/users`<br>
Parameter: `admin_name` (String)<br>
Query (optional):

* Sort usernames in alphabetic order (default): `?sort:DESC`
* Sort usernames in reverse alphabetic order: `?sort:ASC`

Header:

```javascript
{
    "token" : "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Im5pY2hvOTAiLCJwYXNzd29yZCI6ImFiYyIsImlhdCI6MTQ2MjcxOTAwNCwiZXhwIjoxNDYyODA1NDA0fQ.tAhrym-KBJey4emArB7-zUUE1rYy5aYyg7CNh-qagD0"
}
```

Response (`200`):

```javascript
[
    {
        "created": "2016-05-08T11:43:31.397Z",
        "updated": "2016-05-08T11:43:31.397Z",
        "username": "Timmimim",
        "password": "jkl",
        "email_address": "t_kueh06@uni-muenster.de",
        "first_name": "Timm",
        "last_name": "K.",
        "role": "user"
    },
    {
        "created": "2016-05-08T11:43:31.397Z",
        "updated": "2016-05-08T11:43:31.397Z",
        "username": "heinrichloewen",
        "password": "def",
        "email_address": "loewen.heinrich@uni-muenster.de",
        "first_name": "Heinrich",
        "last_name": "L.",
        "role": "user"
    },
    {
        "created": "2016-05-08T11:43:31.397Z",
        "updated": "2016-05-08T15:03:05.637Z",
        "username": "nicho90",
        "password": "abc",
        "email_address": "n.schiestel@uni-muenster.de",
        "first_name": "Nicho",
        "last_name": "S.",
        "role": "user"
    },
    {
        "created": "2016-05-08T11:43:31.397Z",
        "updated": "2016-05-08T11:43:31.397Z",
        "username": "rehans516",
        "password": "ghi",
        "email_address": "r_chau02@uni-muenster.de",
        "first_name": "Rehan",
        "last_name": "C.",
        "role": "user"
    }
]
```

### 1.2 POST User

Endpoint: `/api/users`<br>
Body:

```javascript
{
    "username": "nicho90",
    "password": "abc",
    "email_address": "n.schiestel@uni-muenster.de",
    "first_name": "Nicho",
    "last_name": "S."
}
```

Response (`201`):

```javascript
{
  "created": "2016-05-08T11:43:31.397Z",
  "updated": "2016-05-08T15:03:05.637Z",
  "username": "nicho90",
  "password": "abc",
  "email_address": "n.schiestel@uni-muenster.de",
  "first_name": "Nicho",
  "last_name": "S.",
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Im5pY2hvOTAiLCJwYXNzd29yZCI6ImFiYyIsImlhdCI6MTQ2MjcxOTAwNCwiZXhwIjoxNDYyODA1NDA0fQ.tAhrym-KBJey4emArB7-zUUE1rYy5aYyg7CNh-qagD0"
}
```

### 1.3 GET User by his username

Endpoint: `/api/users/:username`<br>
Parameter: `username` (String)<br>
Header:

```javascript
{
    "token" : "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Im5pY2hvOTAiLCJwYXNzd29yZCI6ImFiYyIsImlhdCI6MTQ2MjcxOTAwNCwiZXhwIjoxNDYyODA1NDA0fQ.tAhrym-KBJey4emArB7-zUUE1rYy5aYyg7CNh-qagD0"
}
```

Response (`200`):

```javascript
{
  "created": "2016-05-08T11:43:31.397Z",
  "updated": "2016-05-08T15:03:05.637Z",
  "username": "nicho90",
  "password": "abc",
  "email_address": "n.schiestel@uni-muenster.de",
  "first_name": "Nicho",
  "last_name": "S.",
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Im5pY2hvOTAiLCJwYXNzd29yZCI6ImFiYyIsImlhdCI6MTQ2MjcxOTAwNCwiZXhwIjoxNDYyODA1NDA0fQ.tAhrym-KBJey4emArB7-zUUE1rYy5aYyg7CNh-qagD0"
}
```

### 1.4 PUT User by his username

Endpoint: `/api/users/:username`<br>
Parameter: `username` (String)<br>
Header:

```javascript
{
    "token" : "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Im5pY2hvOTAiLCJwYXNzd29yZCI6ImFiYyIsImlhdCI6MTQ2MjcxOTAwNCwiZXhwIjoxNDYyODA1NDA0fQ.tAhrym-KBJey4emArB7-zUUE1rYy5aYyg7CNh-qagD0"
}
```

Body:
```javascript
{
  "username": "nicho_90",
  "password": "123456",
  "email_address": "n.schiestel@uni-muenster.de",
  "first_name": "Nicho",
  "last_name": "S."
}
```

Response (`200`):

```javascript
{
  "created": "2016-05-08T11:43:31.397Z",
  "updated": "2016-05-09T13:12:34.124Z",
  "username": "nicho_90",
  "password": "123456",
  "email_address": "n.schiestel@uni-muenster.de",
  "first_name": "Nicho",
  "last_name": "S.",
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Im5pY2hvOTAiLCJwYXNzd29yZCI6ImFiYyIsImlhdCI6MTQ2MjcxOTAwNCwiZXhwIjoxNDYyODA1NDA0fQ.tAhrym-KBJey4emArB7-zUUE1rYy5aYyg7CNh-qagD0"
}
```

### 1.5 DELETE User by his username

Endpoint: `/api/users/:username`<br>
Parameter: `username` (String)<br>
Header:

```javascript
{
    "token" : "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Im5pY2hvOTAiLCJwYXNzd29yZCI6ImFiYyIsImlhdCI6MTQ2MjcxOTAwNCwiZXhwIjoxNDYyODA1NDA0fQ.tAhrym-KBJey4emArB7-zUUE1rYy5aYyg7CNh-qagD0"
}
```

Response (`204`):

```javascript
null
```

* * *

## 2. Sensors

TO-DO