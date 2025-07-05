# Installed Services API Documentation

This document includes the installed services-related API methods from the Fides API.

---

## Base URL

```
/app/v1/installed-service
```

---

### 1. Install Service

**POST** `/insert`

Inserts a installed service for a user.

**Request Body:**

```json
{
  "serviceId": "123",
  "installedServiceName": "string",
  "installedServiceImage": "string",
  "description": "string",
  "code": "string",
  "deviceMap": {}
}
```

**Response:**

* 201 Created: Service installed

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/installed-service/install \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{
      "serviceId": "123",
      "installedServiceName": "string",
      "installedServiceImage": "string",
      "description": "string",
      "code": "string",
      "deviceMap": {}
      }'
```

---


### 2. Edit Installed Service

**PATCH** `/edit`

Edits an installed service by its ID and other fields.

**Request Body:**

```json
{
  "installedServiceId": "123",
  "installedServiceName": "Service1"
  
}
```

**Response:**

* 200 OK: Installed service updated

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/installed-service/edit \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{
      "installedServiceId": "123",
      "installedServiceName": "Service1"
      }'
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

### 4. Get Installed Services by Device Encrypted ID

**GET** `/get-installed-services-by-device-encrypted-id/{deviceEncryptedId}`

Retrieves all installed services associated with a specific device by its encrypted ID.

**Path Parameter:**

* `deviceEncryptedId`: Device Encrypted ID (string, required)

**Response:**

* 200 OK: List of installed services for the device

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/installed-service/get-installed-services-by-device-encrypted-id/abc123 \
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

### 6. Delete Installed Service by Installed Service ID

**DELETE** `/delete-installed-service-by-installed-service-id/{installedServiceId}`

Deletes an installed service by its ID.

**Path Parameter:**

* `installedServiceId`: Installed Service ID (string, required)

**Response:**

* 200 OK: Installed service deleted

**Example Curl:**

```bash
curl -X DELETE https://your-domain.com/app/v1/installed-service/delete-installed-service-by-installed-service-id/123 \
  -H 'Authorization: Bearer <token>'
```

---

## Security

These endpoints require a bearer token.

---

Next Section: [Device Mangement API Documentation](devices_management.md)
