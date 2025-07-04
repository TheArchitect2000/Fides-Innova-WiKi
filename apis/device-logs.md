# Device Logs API Documentation

This document includes the device log-related API methods from the Fides API.

---

## Base URL

```
/app/v1/device-log
```

---

### 1. Get Last Device Log by Encrypted Device ID and Field Name

**GET** `/get-last-device-log-by-encrypted-deviceid-and-field-name`

Retrieves the last device log by encrypted device ID and field name (default: 'data').

**Query Parameters:**

* `deviceEncryptedId`: Device encrypted ID (string, required)
* `fieldName`: Field name (string, required)

**Response:**

* 200 OK: Device log retrieved

**Example Curl:**

```bash
curl -X GET "https://your-domain.com/app/v1/device-log/get-last-device-log-by-encrypted-deviceid-and-field-name?deviceEncryptedId=abc123&fieldName=data" \
  -H 'Authorization: Bearer <token>'
```

---

### 2. Get Last Devices Log by User ID and Field Name

**GET** `/get-last-devices-log-by-userid-and-field-name`

Retrieves the last device logs for a user by user ID and field name (default: 'data').

**Query Parameters:**

* `userId`: User ID (string, required)
* `fieldName`: Field name (string, required)

**Response:**

* 200 OK: Device logs retrieved

**Example Curl:**

```bash
curl -X GET "https://your-domain.com/app/v1/device-log/get-last-devices-log-by-userid-and-field-name?userId=123&fieldName=data" \
  -H 'Authorization: Bearer <token>'
```

---

### 3. Get Last Local Devices Log by Field Name

**GET** `/get-last-my-local-devices-log-by-field-name`

Retrieves the last logs for devices shared with the user by field name (default: 'data').

**Query Parameters:**

* `fieldName`: Field name (string, required)

**Response:**

* 200 OK: Device logs retrieved

**Example Curl:**

```bash
curl -X GET "https://your-domain.com/app/v1/device-log/get-last-my-local-devices-log-by-field-name?fieldName=data" \
  -H 'Authorization: Bearer <token>'
```

---

### 4. Get Device Log by Encrypted Device ID, Field Name, and Date

**GET** `/get-device-log-by-encrypted-deviceid-and-field-name-and-date`

Retrieves device logs for a specific device by encrypted device ID, field name, and date range.

**Query Parameters:**

* `deviceEncryptedId`: Device encrypted ID (string, required)
* `fieldName`: Field name (string, required)
* `startYear`: Start year (number, required)
* `startMonth`: Start month (number, required)
* `startDay`: Start day (number, required)
* `endYear`: End year (number, required)
* `endMonth`: End month (number, required)
* `endDay`: End day (number, required)

**Response:**

* 200 OK: Device logs retrieved

**Example Curl:**

```bash
curl -X GET "https://your-domain.com/app/v1/device-log/get-device-log-by-encrypted-deviceid-and-field-name-and-date?deviceEncryptedId=abc123&fieldName=data&startYear=2025&startMonth=7&startDay=1&endYear=2025&endMonth=7&endDay=4" \
  -H 'Authorization: Bearer <token>'
```

---

### 5. Get Device Log by Encrypted Device ID and Number of Days Before

**GET** `/get-device-log-by-encrypted-deviceid-and-field-name-and-number-of-days-before`

Retrieves device logs for a specific device by encrypted device ID, field name, and number of days before the current date.

**Query Parameters:**

* `deviceEncryptedId`: Device encrypted ID (string, required)
* `daysBefore`: Number of days before (number, required)

**Response:**

* 200 OK: Device logs retrieved

**Example Curl:**

```bash
curl -X GET "https://your-domain.com/app/v1/device-log/get-device-log-by-encrypted-deviceid-and-field-name-and-number-of-days-before?deviceEncryptedId=abc123&daysBefore=7" \
  -H 'Authorization: Bearer <token>'
```

---

### 6. Get Device Log by Encrypted Device ID and Date Range

**GET** `/get-device-log-by-encrypted-deviceid-and-date-range`

Retrieves aggregated device logs for a specific device by encrypted device ID, date range, and aggregation type (day or hour).

**Query Parameters:**

* `deviceEncryptedId`: Device encrypted ID (string, required)
* `startDate`: Start date of the range (YYYY-MM-DD, required)
* `endDate`: End date of the range (YYYY-MM-DD, required)
* `type`: Type of aggregation (day or hour, required)

**Response:**

* 200 OK: Aggregated device logs retrieved

**Example Curl:**

```bash
curl -X GET "https://your-domain.com/app/v1/device-log/get-device-log-by-encrypted-deviceid-and-date-range?deviceEncryptedId=abc123&startDate=2025-07-01&endDate=2025-07-04&type=day" \
  -H 'Authorization: Bearer <token>'
```

---

## Security

These endpoints require a bearer token.

---

Next Section: [Buildings API Documentation](buildings.md)
