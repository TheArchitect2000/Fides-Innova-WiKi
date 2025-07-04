# Installed Services API Documentation

This document includes the installed services-related API methods from the Fides API.

---

## Base URL

```
/app/v1/installed-service
```

---

### 1. Install Service

**POST** `/install`

Installs a service for a user.

**Request Body:**

```json
{
  "serviceId": "123",
  "devices": ["deviceId1", "deviceId2"]
}
```

**Response:**

* 201 Created: Service installed

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/installed-service/install \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"serviceId": "123", "devices": ["deviceId1", "deviceId2"]}'
```

---

### 2. Uninstall Service

**DELETE** `/uninstall/{installedServiceId}`

Uninstalls a service by its installed service ID.

**Path Parameter:**

* `installedServiceId`: Installed Service ID (string, required)

**Response:**

* 200 OK: Service uninstalled

**Example Curl:**

```bash
curl -X DELETE https://your-domain.com/app/v1/installed-service/uninstall/123 \
  -H 'Authorization: Bearer <token>'
```

---

### 3. Get Installed Services by User ID

**GET** `/get-installed-services-by-user-id/{userId}`

Retrieves all installed services for a specific user ID.

**Path Parameter:**

* `userId`: User ID (string, required)

**Response:**

* 200 OK: List of installed services

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/installed-service/get-installed-services-by-user-id/123 \
  -H 'Authorization: Bearer <token>'
```

---

### 4. Get Installed Service by Installed Service ID

**GET** `/get-installed-service-by-installed-service-id/{installedServiceId}`

Retrieves details of a specific installed service by its ID.

**Path Parameter:**

* `installedServiceId`: Installed Service ID (string, required)

**Response:**

* 200 OK: Installed service details

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/installed-service/get-installed-service-by-installed-service-id/123 \
  -H 'Authorization: Bearer <token>'
```

---

### 5. Get All Installed Services

**GET** `/get-all-installed-services`

Retrieves all installed services in the system.

**Response:**

* 200 OK: List of all installed services

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/installed-service/get-all-installed-services \
  -H 'Authorization: Bearer <token>'
```

---

## Security

These endpoints require a bearer token.

---

[Next Section: Device Types API Documentation](device-types.md)
