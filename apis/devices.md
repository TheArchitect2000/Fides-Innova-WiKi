# Devices API Documentation

This document includes all endpoints related to device registration, management, and control in the Fides API.

---

## Base URL

```
/app/device
```

---

### 1. Register Device

**POST** `/register-device`

Registers a new device.

**Request Body:**

```json
{
  "name": "Thermostat X",
  "macAddress": "AA:BB:CC:DD:EE:FF",
  "type": "temperature-sensor",
  "description": "Living room thermostat"
}
```

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/device/register-device \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{
    "name": "Thermostat X",
    "macAddress": "AA:BB:CC:DD:EE:FF",
    "type": "temperature-sensor",
    "description": "Living room thermostat"
  }'
```

---

### 2. Get All Devices (Admin)

**GET** `/get-all`

Returns a list of all registered devices (admin access).

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/device/get-all \
  -H 'Authorization: Bearer <token>'
```

---

### 3. Get My Devices

**GET** `/get-my-devices`

Returns a list of devices owned by the authenticated user.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/device/get-my-devices \
  -H 'Authorization: Bearer <token>'
```

---

### 4. Get Device by ID

**GET** `/get-by-id/{deviceId}`

Returns device information by ID.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/device/get-by-id/abc123 \
  -H 'Authorization: Bearer <token>'
```

---

### 5. Edit Device by Owner

**PATCH** `/edit-my-device/{deviceId}`

Updates a device owned by the user.

**Request Body:**

```json
{
  "name": "Updated Device Name",
  "description": "Updated description"
}
```

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/device/edit-my-device/abc123 \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"name": "Updated Device Name", "description": "Updated description"}'
```

---

### 6. Edit Device by Admin

**PATCH** `/edit-device-by-admin/{deviceId}`

Admin endpoint to edit any device.

**Request Body:**

```json
{
  "status": "active"
}
```

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/device/edit-device-by-admin/abc123 \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"status": "active"}'
```

---

### 7. Delete Device (User)

**DELETE** `/delete-my-device/{deviceId}`

Deletes a device owned by the current user.

**Example Curl:**

```bash
curl -X DELETE https://your-domain.com/app/device/delete-my-device/abc123 \
  -H 'Authorization: Bearer <token>'
```

---

### 8. Delete Device (Admin)

**DELETE** `/delete-device-by-admin/{deviceId}`

Deletes any device by ID (admin only).

**Example Curl:**

```bash
curl -X DELETE https://your-domain.com/app/device/delete-device-by-admin/abc123 \
  -H 'Authorization: Bearer <token>'
```

---

### 9. Get All Device Types

**GET** `/get-all-device-types`

Returns a list of supported device types.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/device/get-all-device-types \
  -H 'Authorization: Bearer <token>'
```

---

### 10. Filter Devices by Status

**GET** `/get-devices-by-status?status=active`

Filters devices by given status.

**Example Curl:**

```bash
curl -X GET "https://your-domain.com/app/device/get-devices-by-status?status=active" \
  -H 'Authorization: Bearer <token>'
```

---

**➡️ For installed services and service-device interactions, see `services.md`.**
