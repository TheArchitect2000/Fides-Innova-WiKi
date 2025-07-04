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


---

## Security

These endpoints require a bearer token.

---

[Next Section: Device Logs API Documentation](device-logs.md)
