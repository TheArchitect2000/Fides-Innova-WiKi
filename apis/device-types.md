# Device Types API Documentation

This document includes the device type-related API methods from the Fides API.

---

## Base URL

```
/app/v1/device-type
```

---

### 1. Get All Device Types

**GET** `/get-all-device-types`

Retrieves all available device types in the system.

**Response:**

* 200 OK: List of all device types

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/device-type/get-all-device-types \
  -H 'Authorization: Bearer <token>'
```

---

### 2. Get Device Type by Device Type ID

**GET** `/get-device-type-by-device-type-id/{deviceTypeId}`

Retrieves details of a specific device type by its ID.

**Path Parameter:**

* `deviceTypeId`: Device Type ID (string, required)

**Response:**

* 200 OK: Device type details

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/device-type/get-device-type-by-device-type-id/123 \
  -H 'Authorization: Bearer <token>'
```

---

### 3. Insert Device Type

**POST** `/insert`

Inserts a new device type.

**Request Body:**

```json
{
  "deviceTypeName": "Device Type Name",
  "description": "Device Type Description",
  "parameters": ["param1", "param2"]
}
```

**Response:**

* 201 Created: Device type inserted

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/device-type/insert \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"deviceTypeName": "Device Type Name", "description": "Device Type Description", "parameters": ["param1", "param2"]}'
```

---

### 4. Edit Device Type

**PATCH** `/edit`

Edits an existing device type by its ID.

**Request Body:**

```json
{
  "deviceTypeId": "123",
  "deviceTypeName": "Updated Device Type Name",
  "description": "Updated Device Type Description",
  "parameters": ["param1", "param2"]
}
```

**Response:**

* 200 OK: Device type updated

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/device-type/edit \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"deviceTypeId": "123", "deviceTypeName": "Updated Device Type Name", "description": "Updated Device Type Description", "parameters": ["param1", "param2"]}'
```

---

### 5. Delete Device Type by Device Type ID

**DELETE** `/delete-device-type-by-device-type-id/{deviceTypeId}`

Deletes a device type by its ID.

**Path Parameter:**

* `deviceTypeId`: Device Type ID (string, required)

**Response:**

* 200 OK: Device type deleted

**Example Curl:**

```bash
curl -X DELETE https://your-domain.com/app/v1/device-type/delete-device-type-by-device-type-id/123 \
  -H 'Authorization: Bearer <token>'
```

---

## Security

These endpoints require a bearer token.

---
