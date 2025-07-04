# Services API Documentation

This document includes the service-related API methods from the Fides API.

---

## Base URL

```
/app/v1/service
```

---

### 1. Insert Service

**POST** `/insert`

Inserts a new user service.

**Request Body:**

```json
{
  "serviceName": "Service Name",
  "description": "Service Description",
  "serviceType": "Type",
  "status": "Active",
  "blocklyJson": "{}",
  "code": "service code",
  "devices": ["deviceId1", "deviceId2"]
}
```

**Response:**

* 201 Created: Service inserted

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/service/insert \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"serviceName": "Service Name", "description": "Service Description", "serviceType": "Type", "status": "Active", "blocklyJson": "{}", "code": "service code", "devices": ["deviceId1", "deviceId2"]}'
```

---

### 2. Request Service Publish

**PATCH** `/request-service-publish`

Requests to publish a user service.

**Request Body:**

```json
{
  "serviceId": "123"
}
```

**Response:**

* 201 Created: Publish request submitted

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/service/request-service-publish \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"serviceId": "123"}'
```

---

### 3. Publish Service

**PATCH** `/publish-service`

Publishes a user service that has been requested for publishing.

**Request Body:**

```json
{
  "serviceId": "123"
}
```

**Response:**

* 201 Created: Service published

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/service/publish-service \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"serviceId": "123"}'
```

---

### 4. Reject Service

**PATCH** `/reject-service`

Rejects a user service that has been requested for publishing.

**Request Body:**

```json
{
  "serviceId": "123"
}
```

**Response:**

* 201 Created: Service rejected

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/service/reject-service \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"serviceId": "123"}'
```

---

### 5. Cancel Service Request

**PATCH** `/cancel-service-request`

Cancels a service publish request.

**Request Body:**

```json
{
  "serviceId": "123"
}
```

**Response:**

* 201 Created: Service request canceled

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/service/cancel-service-request \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"serviceId": "123"}'
```

---

### 6. Edit Service

**PATCH** `/edit`

Edits a service by service ID and other fields.

**Request Body:**

```json
{
  "serviceId": "123",
  "serviceName": "Updated Service Name",
  "description": "Updated Description",
  "serviceType": "Type",
  "status": "Active",
  "devices": ["deviceId1", "deviceId2"],
  "serviceImage": "image_url",
  "blocklyJson": "{}",
  "code": "updated service code"
}
```

**Response:**

* 200 OK: Service updated

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/service/edit \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"serviceId": "123", "serviceName": "Updated Service Name", "description": "Updated Description", "serviceType": "Type", "status": "Active", "devices": ["deviceId1", "deviceId2"], "serviceImage": "image_url", "blocklyJson": "{}", "code": "updated service code"}'
```

---

### 7. Get Services by User ID

**GET** `/get-services-by-user-id/{userId}`

Retrieves all services associated with a specific user ID.

**Path Parameter:**

* `userId`: User ID (string, required)

**Response:**

* 200 OK: List of user services

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/service/get-services-by-user-id/123 \
  -H 'Authorization: Bearer <token>'
```

---

### 8. Get Service by Service ID

**GET** `/get-service-by-service-id/{serviceId}`

Retrieves a service by its ID.

**Path Parameter:**

* `serviceId`: Service ID (string, required)

**Response:**

* 200 OK: Service details

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/service/get-service-by-service-id/123 \
  -H 'Authorization: Bearer <token>'
```

---

### 9. Get All Published Services

**GET** `/get-all-published-services`

Retrieves all services that are published.

**Response:**

* 200 OK: List of published services

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/service/get-all-published-services \
  -H 'Authorization: Bearer <token>'
```

---

### 10. Get All Publish Requested Services

**GET** `/get-all-publish-requested-services`

Retrieves all services that have requested to be published.

**Response:**

* 200 OK: List of publish-requested services

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/service/get-all-publish-requested-services \
  -H 'Authorization: Bearer <token>'
```

---

### 11. Get All Services

**GET** `/get-all-services`

Retrieves all services in the system.

**Response:**

* 200 OK: List of all services

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/service/get-all-services \
  -H 'Authorization: Bearer <token>'
```

---

### 12. Delete Service by Service ID

**DELETE** `/delete-service-by-service-id/{serviceId}`

Deletes a service by its ID.

**Path Parameter:**

* `serviceId`: Service ID (string, required)

**Response:**

* 200 OK: Service deleted

**Example Curl:**

```bash
curl -X DELETE https://your-domain.com/app/v1/service/delete-service-by-service-id/123 \
  -H 'Authorization: Bearer <token>'
```

---

## Security

These endpoints require a bearer token.

---

[Next Section: Installed Services API Documentation](installed-services.md)
