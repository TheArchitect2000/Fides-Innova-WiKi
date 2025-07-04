# Services API Documentation

This document describes all service-related endpoints in the Fides API, including managing available services and those installed on user devices.

---

## Base URL

```
/app/service
```

---

### 1. Get All Services

**GET** `/get-all`

Returns a list of all available services.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/service/get-all \
  -H 'Authorization: Bearer <token>'
```

---

### 2. Get Service by ID

**GET** `/get-by-id/{serviceId}`

Returns detailed information about a specific service.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/service/get-by-id/abc123 \
  -H 'Authorization: Bearer <token>'
```

---

### 3. Get All Installed Services by Device ID

**GET** `/get-all-installed-services-by-device-id/{deviceId}`

Returns a list of services currently installed on a specific device.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/service/get-all-installed-services-by-device-id/device001 \
  -H 'Authorization: Bearer <token>'
```

---

### 4. Install Service to Device

**POST** `/install`

Installs a service to a device.

**Request Body:**

```json
{
  "deviceId": "device001",
  "serviceId": "service001"
}
```

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/service/install \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"deviceId": "device001", "serviceId": "service001"}'
```

---

### 5. Uninstall Service from Device

**DELETE** `/uninstall-service/{installedServiceId}`

Uninstalls a service from a device.

**Example Curl:**

```bash
curl -X DELETE https://your-domain.com/app/service/uninstall-service/installed123 \
  -H 'Authorization: Bearer <token>'
```

---

### 6. Update Installed Service

**PATCH** `/edit-installed-service/{installedServiceId}`

Updates the installed service information.

**Request Body:**

```json
{
  "status": "active"
}
```

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/service/edit-installed-service/installed123 \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"status": "active"}'
```

---

### 7. Get All Installed Services (Admin)

**GET** `/get-all-installed-services`

Returns all installed services across all users and devices.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/service/get-all-installed-services \
  -H 'Authorization: Bearer <token>'
```

---

### 8. Get Installed Service by ID

**GET** `/get-installed-service-by-id/{installedServiceId}`

Returns details about a specific installed service.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/service/get-installed-service-by-id/installed123 \
  -H 'Authorization: Bearer <token>'
```

---

**➡️ For Smart Contract and ZKP management, see `smart-contract.md`.**
