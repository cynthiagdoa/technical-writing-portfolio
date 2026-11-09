# GeoRoute REST API v1.0 — Developer Documentation

Welcome to the GeoRoute API reference. This documentation is designed to help you integrate our distance calculation and geocoding services into your platform seamlessly.

## 1. Authentication
All API requests require an API key passed in the HTTP header. 

```http
Authorization: Bearer YOUR_API_KEY
```

---

## 2. Calculate Route Distance (`POST /v1/routes/distance`)
Calculates the optimal distance, estimated time, and toll costs between a starting point and a destination.

### HTTP Request
`POST https://georoute.com`

### Headers

| Key | Type | Description |
| :--- | :--- | :--- |
| `Authorization` | `String` | **Required.** Your Bearer API Key. |
| `Content-Type` | `String` | **Required.** Must be `application/json`. |

### Request Body (JSON)

| Field | Type | Description |
| :--- | :--- | :--- |
| `origin` | `Object` | **Required.** Contains `lat` and `lng` of the starting point. |
| `destination` | `Object` | **Required.** Contains `lat` and `lng` of the endpoint. |
| `vehicle_type` | `String` | Optional. Options: `car`, `truck`, `motorcycle`. Default: `car`. |

#### Example Request Body
```json
{
  "origin": {
    "lat": 40.416775,
    "lng": -3.703790
  },
  "destination": {
    "lat": 41.385064,
    "lng": 2.173403
  },
  "vehicle_type": "truck"
}
```

---

### Response (200 OK)
Returns a JSON object containing route measurements and estimated pricing.

#### Example Response Body
```json
{
  "status": "success",
  "data": {
    "distance_km": 505.4,
    "duration_minutes": 290,
    "currency": "EUR",
    "estimated_tolls": 14.50
  }
}
```

---

## 3. Error Codes & Troubleshooting
The API returns standard HTTP status codes. Errors include an explicit error object in the response body.

| Status Code | Description | Common Cause |
| :--- | :--- | :--- |
| `200 OK` | Success | The request was processed successfully. |
| `400 Bad Request` | Invalid payload | Missing required fields or incorrect latitude/longitude formats. |
| `401 Unauthorized` | Authentication failed | Missing, expired, or invalid API key. |
| `500 Internal Error`| Server Error | Something went wrong on our end. Retry in a few minutes. |

#### Example Error Response (401 Unauthorized)
```json
{
  "error": {
    "code": "AUTH_INVALID_KEY",
    "message": "The provided API key is invalid or has expired."
  }
}
```
