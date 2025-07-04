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

## Security

These endpoints require a bearer token.

---

[Next Section: Device Types API Documentation](device-types.md)
