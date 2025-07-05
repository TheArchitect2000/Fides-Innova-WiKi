# Device Management API Documentation

This document includes the device-related API methods from the Fides API.

---

## Base URL

```
/app/v1/device
```

---

### 1. Check Device Existence by MAC Address

**GET** `/check-device-is-exists/{deviceMac}`

Checks whether a device with the given MAC address exists.

**Path Parameter:**

* `deviceMac`: Device MAC address (string, required)

**Response:**

* 200 OK: Device existence status

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/device/check-device-is-exists/00:1A:2B:3C:4D:5E \
  -H 'Authorization: Bearer <token>'
```

---

### 2. Insert Device

**POST** `/insert`

Inserts a new user device.

**Request Body:**

```json
{
  "deviceName": "Device Name",
  "deviceType": "Type",
  "mac": "00:1A:2B:3C:4D:5E",
  "hardwareVersion": 1,
  "firmwareVersion": 1,
  "parameters": ["{\"a1\":\"v1\"}", "{\"a2\":\"v2\"}"],
  "isShared": false,
  "location": "",
  "geometry": ""
}
```

**Response:**

* 201 Created: Device inserted

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/device/insert \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"deviceName": "Device Name", "deviceType": "Type", "mac": "00:1A:2B:3C:4D:5E", "hardwareVersion": 1, "firmwareVersion": 1, "parameters": ["{\"a1\":\"v1\"}", "{\"a2\":\"v2\"}"], "isShared": false, "location": "", "geometry": ""}'
```

---

### 3. Edit Device

**PATCH** `/edit`

Edits an existing device by device ID and other fields.

**Request Body:**

```json
{
  "deviceId": "123",
  "deviceName": "Updated Device Name",
  "deviceType": "Type",
  "mac": "00:1A:2B:3C:4D:5E",
  "hardwareVersion": 1,
  "firmwareVersion": 1,
  "parameters": ["{\"a1\":\"v1\"}", "{\"a2\":\"v2\"}"],
  "isShared": false,
  "costOfUse": 10,
  "location": "",
  "geometry": ""
}
```

**Response:**

* 200 OK: Device updated

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/device/edit \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"deviceId": "123", "deviceName": "Updated Device Name", "deviceType": "Type", "mac": "00:1A:2B:3C:4D:5E", "hardwareVersion": 1, "firmwareVersion": 1, "parameters": ["{\"a1\":\"v1\"}", "{\"a2\":\"v2\"}"], "isShared": false, "costOfUse": 10, "location": "", "geometry": ""}'
```

---

### 4. Get Devices by User ID

**GET** `/get-devices-by-user-id/{userId}`

Retrieves all devices associated with a specific user ID.

**Path Parameter:**

* `userId`: User ID (string, required)

**Response:**

* 200 OK: List of user devices

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/device/get-devices-by-user-id/123 \
  -H 'Authorization: Bearer <token>'
```

---

### 5. Get Devices with Encrypted Device ID by User ID

**GET** `/get-devices-with-encrypted-deviceid-by-user-id/{userId}`

Retrieves devices with encrypted device IDs for a specific user.

**Path Parameter:**

* `userId`: User ID (string, required)

**Response:**

* 200 OK: List of devices with encrypted IDs

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/device/get-devices-with-encrypted-deviceid-by-user-id/123 \
  -H 'Authorization: Bearer <token>'
```

---

### 6. Rename Device

**PATCH** `/rename-device`

Renames a device by its ID.

**Request Body:**

```json
{
  "deviceId": "123",
  "deviceName": "New Device Name"
}
```

**Response:**

* 200 OK: Device renamed

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/device/rename-device \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"deviceId": "123", "deviceName": "New Device Name"}'
```

---

### 7. Get Installed Devices by Date

**GET** `/get-installed-devices-by-date`

Retrieves devices installed on a specific date.

**Query Parameters:**

* `installationYear`: Installation year (number, required)
* `installationMonth`: Installation month (number, required)
* `installationDay`: Installation day (number, required)

**Response:**

* 200 OK: List of devices installed on the specified date

**Example Curl:**

```bash
curl -X GET "https://your-domain.com/app/v1/device/get-installed-devices-by-date?installationYear=2025&installationMonth=7&installationDay=4" \
  -H 'Authorization: Bearer <token>'
```

---

### 8. Get All Shared Devices

**GET** `/get-all-shared-devices`

Retrieves all shared devices.

**Response:**

* 200 OK: List of shared devices

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/device/get-all-shared-devices \
  -H 'Authorization: Bearer <token>'
```

---

### 9. Get All Devices

**GET** `/get-all-devices`

Retrieves all installed devices.

**Response:**

* 200 OK: List of all devices

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/device/get-all-devices \
  -H 'Authorization: Bearer <token>'
```

---

### 10. Get Device Info by Encrypted ID

**GET** `/get-device-info-by-device-encrypted-id/{encryptedId}`

Retrieves device information by its encrypted ID.

**Path Parameter:**

* `encryptedId`: Encrypted device ID (string, required)

**Response:**

* 200 OK: Device information

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/device/get-device-info-by-device-encrypted-id/abc123 \
  -H 'Authorization: Bearer <token>'
```

---

### 11. Delete Device by Device ID

**DELETE** `/delete-device-by-device-id/{deviceId}`

Deletes a device by its ID.

**Path Parameter:**

* `deviceId`: Device ID (string, required)

**Response:**

* 200 OK: Device deleted

**Example Curl:**

```bash
curl -X DELETE https://your-domain.com/app/v1/device/delete-device-by-device-id/123 \
  -H 'Authorization: Bearer <token>'
```

---

### 12. Local Share Device

**PATCH** `/local-share`

Locally shares a device with a user.

**Request Body:**

```json
{
  "deviceId": "123",
  "userEmail": "user@example.com"
}
```

**Response:**

* 200 OK: Device shared

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/device/local-share \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"deviceId": "123", "userEmail": "user@example.com"}'
```

---

### 13. Local Unshare Device

**PATCH** `/local-unshare`

Removes local sharing of a device with a user.

**Request Body:**

```json
{
  "deviceId": "123",
  "userEmail": "user@example.com"
}
```

**Response:**

* 200 OK: Device unshared

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/device/local-unshare \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"deviceId": "123", "userEmail": "user@example.com"}'
```

---

### 14. Get Users Device Sharing With

**GET** `/{deviceId}/local-share/users`

Returns all users that a given device is shared with.

**Path Parameter:**

* `deviceId`: Device ID (string, required)

**Response:**

* 200 OK: List of users

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/device/123/local-share/users \
  -H 'Authorization: Bearer <token>'
```

---

### 15. Get My Local Shared Devices

**GET** `/get-my-local-shared-devices`

Returns all devices shared with the authenticated user.

**Response:**

* 200 OK: List of shared devices

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/device/get-my-local-shared-devices \
  -H 'Authorization: Bearer <token>'
```

---

## Security

These endpoints require a bearer token.

---

Next Section: [Device Types API Documentation](device-types.md)
