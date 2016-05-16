## Overview

| Endpoint | Method | Headers | Query | Function |
|----------|--------|---------|-------|----------|
| `/api/login` | **POST** | | | |
| `/api/users` | **POST** | | | |
| `/api/users/:username` | **GET** | Token | | | 
| `/api/users/:username` | **PUT** | Token | | |
| `/api/users/:username` | **DELETE** | Token | | |
| `/api/users/:username/sensors` | **GET** | Token | `?public=true` (optional)| |
| `/api/users/:username/sensors` | **POST** | Token | | |
| `/api/users/:username/sensors/:sensor_id` | **GET** | Token | | |
| `/api/users/:username/sensors/:sensor_id` | **PUT** | Token | | |
| `/api/users/:username/sensors/:sensor_id` | **DELETE** | Token | | |
| `/api/users/:username/thresholds`| **GET** | Token | | |
| `/api/users/:username/thresholds`| **POST** | Token | | |
| `/api/users/:username/thresholds` | **DELETE** | Token | | |
| `/api/users/:username/thresholds/:threshold_id` | **GET** | Token | | |
| `/api/users/:username/thresholds/:threshold_id` | **PUT** | Token | | |
| `/api/users/:username/thresholds/:threshold_id` | **DELETE** | Token | | |
| `/api/users/:username/subscriptions` | **GET** | Token | | |
| `/api/users/:username/subscriptions` | **POST** | Token | | |
| `/api/users/:username/subscriptions` | **DELETE** | Token | | |
| `/api/users/:username/subscriptions/:subscription_id` | **GET** | Token | | |
| `/api/users/:username/subscriptions/:subscription_id` | **PUT** | Token | | |
| `/api/users/:username/subscriptions/:subscription_id` | **DELETE** | Token | | |
| `/api/sensors` | **GET** | (Token only for admin) | `?bbox=` <br> `[(0.0, 0.0),` <br> `(0.0, 1.0),` <br> `(1.0, 1.0),` <br> `(1.0, 0.0)]` | |
| `/api/sensors/:sensor_id` | **GET** | (Token only for admin) | | |
| `/api/sensors/:sensor_id/measurements` | **GET** | (Token only for admin) | | |
| `/api/sensors/:sensor_id/measurements/measurement_id` | **GET** | (Token only for admin) | | |
| `/api/sensors/:sensor_id/timeseries` | **GET** | (Token only for admin) | `?hours=24`, <br> `?days=7`, <br> `?weeks=2`, <br> `?months=1`, <br> `?months=3`, <br> `?months=6`, <br> `?years=1`, <br> `?years=3` | |
| `/api/vehicles` | **GET** | | `?category=bike`, <br> `?category=car`, <br> etc. | List of all vehicles (bikes, cars, trucks, scooters, motorbikes, wheelchairs) or by category |
| `/api/admin/:admin_name/users` | **GET** | Token | `?sort=DESC`, <br> `?sort=ASC` | List all users, only available for admins |
| `/api/admin/:admin_name/vehicles` | **POST**  | Token | | List of all vehicles (bikes, cars, scooters, motorbikes, wheelchairs) |
| `/api/admin/:admin_name/vehicles/:vehicle_id` | **GET** | Token | | |
| `/api/admin/:admin_name/vehicles/:vehicle_id` | **PUT** | Token | | |
| `/api/admin/:admin_name/vehicles/:vehicle_id` | **DELETE** | Token | | | |

<!-- | `/api/users/:username/sensors/:sensor_id/measurements/measurement_id`| **PUT** | Token | | | -->
<!-- | `/api/users/:username/sensors/:sensor_id/measurements/measurement_id`| **DELETE** | Token | | | -->

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

## 1. Login

Create a new Token

Endpoint: `/api/login`<br>
Body:

```javascript
{
    "username": "nicho90",
    "password": "abc"
}
```

Response `200`:

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

## 2. Users

### 2.1 GET Users

Endpoint: `/api/admin/:admin_name/users`<br>
Parameter: `admin_name` *String*<br>
Query (optional):

* Sort usernames in alphabetic order (default): `?sort:DESC`
* Sort usernames in reverse alphabetic order: `?sort:ASC`

Header:

```javascript
{
    "token" : "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Im5pY2hvOTAiLCJwYXNzd29yZCI6ImFiYyIsImlhdCI6MTQ2MjcxOTAwNCwiZXhwIjoxNDYyODA1NDA0fQ.tAhrym-KBJey4emArB7-zUUE1rYy5aYyg7CNh-qagD0"
}
```

Response `200`:

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

### 2.2 POST User

Create a new User (Registration)

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

Response `201`:

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

### 2.3 GET User by his username

Endpoint: `/api/users/:username`<br>
Parameter: `username` *String*<br>
Header:

```javascript
{
    "token" : "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Im5pY2hvOTAiLCJwYXNzd29yZCI6ImFiYyIsImlhdCI6MTQ2MjcxOTAwNCwiZXhwIjoxNDYyODA1NDA0fQ.tAhrym-KBJey4emArB7-zUUE1rYy5aYyg7CNh-qagD0"
}
```

Response `200`:

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

### 2.4 PUT User by his username

Endpoint: `/api/users/:username`<br>
Parameter: `username` *String*<br>
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

Response `200`:

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

### 2.5 DELETE User by his username

Endpoint: `/api/users/:username`<br>
Parameter: `username` *String*<br>
Header:

```javascript
{
    "token" : "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Im5pY2hvOTAiLCJwYXNzd29yZCI6ImFiYyIsImlhdCI6MTQ2MjcxOTAwNCwiZXhwIjoxNDYyODA1NDA0fQ.tAhrym-KBJey4emArB7-zUUE1rYy5aYyg7CNh-qagD0"
}
```

Response `204`

* * *

## 3. Sensors

### 3.1 GET all public Sensors

List all public sensors

Endpoint: `/api/sensors`<br>

Response `200`:

```javascript
[
    {
        "sensor_id": 1,
        "device_id": "RPi-1",
        "description": "Raspberry Pi at Wersehause",
        "private": false,
        "sensor_height": 320,
        "lng": 51.973314,
        "lat": 7.70013,
        "created": "2016-05-10T08:52:42.174Z",
        "updated": "2016-05-10T08:52:42.174Z"
    },
    {
        "sensor_id": 2,
        "device_id": "RPi-2",
        "description": "2nd Raspberry Pi at Wersehause",
        "private": false,
        "sensor_height": 300,
        "lng": 51.973544,
        "lat": 7.699556,
        "created": "2016-05-10T08:52:42.174Z",
        "updated": "2016-05-10T08:52:42.174Z"
    }
]
```


### 3.2 GET private Sensors by username

List all private sensors of a user. With the optional query, the results can be merged with all public sensors

Endpoint: `/api/users/:username/sensors`<br>
Parameter: `username` *String*<br>
Query: `?public=true` *Boolean*<br>
Header:

```javascript
{
    "token" : "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Im5pY2hvOTAiLCJwYXNzd29yZCI6ImFiYyIsImlhdCI6MTQ2MjcxOTAwNCwiZXhwIjoxNDYyODA1NDA0fQ.tAhrym-KBJey4emArB7-zUUE1rYy5aYyg7CNh-qagD0"
}
```

Response `200`:

```javascript
[
    {
        "created_by": "nicho90",
        "sensor_id": 2,
        "device_id": "RPi-2",
        "description": "2nd Raspberry Pi at Wersehause",
        "private": false,
        "sensor_height": 300,
        "lng": 51.973544,
        "lat": 7.699556,
        "created": "2016-05-10T08:52:42.174Z",
        "updated": "2016-05-10T08:52:42.174Z"
    },
    {
        "created_by": "nicho90",
        "sensor_id": 3,
        "device_id": "RPi-3",
        "description": "3rd private Sensor",
        "private": true,
        "sensor_height": 300,
        "lng": 51.973934,
        "lat": 7.69888,
        "created": "2016-05-10T08:52:42.174Z",
        "updated": "2016-05-10T08:52:42.174Z"
    }
]
```

### 3.3 POST Sensor

Endpoint: `/api/users/:username/sensors`<br>
Parameter: `username` *String*<br>

Header:

```javascript
{
    "token" : "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Im5pY2hvOTAiLCJwYXNzd29yZCI6ImFiYyIsImlhdCI6MTQ2MjcxOTAwNCwiZXhwIjoxNDYyODA1NDA0fQ.tAhrym-KBJey4emArB7-zUUE1rYy5aYyg7CNh-qagD0"
}
```

Body:

```javascript
{
    "device_id": "RPi-4",
    "description": "4th Raspberry Pi at Wersehause",
    "private": false,
    "sensor_height": 280,
    "lng": 51.974454,
    "lat": 7.699119
}
```

Response `201`:

```javascript
{
    "sensor_id": 4,
    "device_id": "RPi-4",
    "created_by": "nicho90",
    "description": "4th Raspberry Pi at Wersehause",
    "private": false,
    "sensor_height": 280,
    "lng": 51.974454,
    "lat": 7.699119,
    "created": "2016-05-10T08:52:42.174Z",
    "updated": "2016-05-10T08:52:42.174Z"
}
```

### 3.4 GET a public sensor by its id

TODO

### 3.5 GET a private sensor by its id

TTODO

### 3.6 PUT Sensor by its id

TODO

### 3.7 DELETE Sensor by its id

Endpoint: `/api/users/:username/sensors/:sensor_id`<br>
Parameter: `username` *String*<br>

Header:

```javascript
{
    "token" : "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Im5pY2hvOTAiLCJwYXNzd29yZCI6ImFiYyIsImlhdCI6MTQ2MjcxOTAwNCwiZXhwIjoxNDYyODA1NDA0fQ.tAhrym-KBJey4emArB7-zUUE1rYy5aYyg7CNh-qagD0"
}
```

Response `204`

* * *

## 4. Thresholds

### 4.1 GET all Thresholds by username

List all thresholds of a user

Endpoint: `/api/users/:username/thresholds`<br>
Parameter: `username` *String*<br>

Header:

```javascript
{
    "token" : "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Im5pY2hvOTAiLCJwYXNzd29yZCI6ImFiYyIsImlhdCI6MTQ2MjcxOTAwNCwiZXhwIjoxNDYyODA1NDA0fQ.tAhrym-KBJey4emArB7-zUUE1rYy5aYyg7CNh-qagD0"
}
```

Response `200`:

```javascript
[
    {
        "threshold_id": 1,
        "created": "2016-05-16T22:20:36.756Z",
        "updated": "2016-05-16T22:20:36.756Z",
        "username": "nicho90",
        "description": "Myself",
        "value": 50,
        "category": "PEDESTRIAN"
    },
    {
        "threshold_id": 2,
        "created": "2016-05-16T22:20:36.756Z",
        "updated": "2016-05-16T22:20:36.756Z",
        "username": "nicho90",
        "description": "VW Golf (2015)",
        "value": 20,
        "category": "CAR"
    },
    {
        "threshold_id": 3,
        "created": "2016-05-16T22:20:36.756Z",
        "updated": "2016-05-16T22:20:36.756Z",
        "username": "nicho90",
        "description": "Yamaha MT-03 (2015)",
        "value": 13,
        "category": "CAR"
    }
]
```

### 4.2 POST Threshold by username

Endpoint: `/api/users/:username/thresholds`<br>
Parameter: `username` *String*<br>

Header:

```javascript
{
    "token" : "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Im5pY2hvOTAiLCJwYXNzd29yZCI6ImFiYyIsImlhdCI6MTQ2MjcxOTAwNCwiZXhwIjoxNDYyODA1NDA0fQ.tAhrym-KBJey4emArB7-zUUE1rYy5aYyg7CNh-qagD0"
}
```

Body:

```javascript
{
    "username": "nicho90",
    "description": "MyDog",
    "value": 20,
    "category": "OTHER"
}
```

Response `200`:

```javascript
{
    "threshold_id": 6,
    "created": "2016-05-16T22:39:50.168Z",
    "updated": "2016-05-16T22:39:50.168Z",
    "username": "nicho90",
    "description": "MyDog",
    "value": 20,
    "category": "OTHER"
}
```

### 4.3 GET Threshold by username and its id

### 4.4 PUT Threshold by username and its id

### 4.5 DELETE Threshold by username and its id

### 4.6 DELETE all Thresholds by username

Endpoint: `/api/users/:username/thresholds`<br>
Parameter: `username` *String*<br>

Header:

```javascript
{
    "token" : "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Im5pY2hvOTAiLCJwYXNzd29yZCI6ImFiYyIsImlhdCI6MTQ2MjcxOTAwNCwiZXhwIjoxNDYyODA1NDA0fQ.tAhrym-KBJey4emArB7-zUUE1rYy5aYyg7CNh-qagD0"
}
```

Response `204`


## 5. Subscriptions

### 5.1 GET all Subscriptions by username

List all subscriptions of a user

Endpoint: `/api/users/:username/subscriptions`<br>
Parameter: `username` *String*<br>

Header:

```javascript
{
    "token" : "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Im5pY2hvOTAiLCJwYXNzd29yZCI6ImFiYyIsImlhdCI6MTQ2MjcxOTAwNCwiZXhwIjoxNDYyODA1NDA0fQ.tAhrym-KBJey4emArB7-zUUE1rYy5aYyg7CNh-qagD0"
}
```

Response `200`:

```javascript
[
    {
        "subscription_id": 1,
        "created": "2016-05-16T22:20:44.110Z",
        "updated": "2016-05-16T22:20:44.110Z",
        "username": "nicho90",
        "sensor_id": 1,
        "threshold_id": 1
    },
    {
        "subscription_id": 2,
        "created": "2016-05-16T22:20:44.110Z",
        "updated": "2016-05-16T22:20:44.110Z",
        "username": "nicho90",
        "sensor_id": 1,
        "threshold_id": 2
    },
    {
        "subscription_id": 3,
        "created": "2016-05-16T22:20:44.110Z",
        "updated": "2016-05-16T22:20:44.110Z",
        "username": "nicho90",
        "sensor_id": 1,
        "threshold_id": 3
    }
]
```

### 5.2 POST Subscription by username

Endpoint: `/api/users/:username/subscriptions`<br>
Parameter: `username` *String*<br>

Header:

```javascript
{
    "token" : "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Im5pY2hvOTAiLCJwYXNzd29yZCI6ImFiYyIsImlhdCI6MTQ2MjcxOTAwNCwiZXhwIjoxNDYyODA1NDA0fQ.tAhrym-KBJey4emArB7-zUUE1rYy5aYyg7CNh-qagD0"
}
```

Body:

```javascript
{
    "username": "nicho90",
    "sensor_id": 2,
    "threshold_id": 1
}
```

Response `200`:

```javascript
{
    "subscription_id": 4,
    "created": "2016-05-16T22:37:35.561Z",
    "updated": "2016-05-16T22:37:35.561Z",
    "username": "nicho90",
    "sensor_id": 2,
    "threshold_id": 1
}
```

### 5.3 GET Subscription by username and its id

### 5.4 PUT Subscription by username and its id

### 5.5 DELETE Subscription by username and its id

### 5.6 DELETE all Subscriptions by username

Endpoint: `/api/users/:username/subscriptions`<br>
Parameter: `username` *String*<br>

Header:

```javascript
{
    "token" : "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Im5pY2hvOTAiLCJwYXNzd29yZCI6ImFiYyIsImlhdCI6MTQ2MjcxOTAwNCwiZXhwIjoxNDYyODA1NDA0fQ.tAhrym-KBJey4emArB7-zUUE1rYy5aYyg7CNh-qagD0"
}
```

Response `204`

## 6. Measurements

TODO

## 7. Time-Series

TODO

## 8. Vehicles
