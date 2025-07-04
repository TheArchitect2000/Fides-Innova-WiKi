# Media API Documentation

This document includes the media-related API methods from the Fides API.

---

## Base URL

```
/app/v1/media
```

---

### 1. Upload Media

**POST** `/upload`

Uploads a new media file (e.g., image, video, or document) for a user or resource.

**Request Body:**

* Content-Type: `multipart/form-data`
* Parameters:
  * `file`: The media file to upload (binary, required)
  * `userId`: User ID associated with the media (string, required)
  * `resourceType`: Type of resource (e.g., "user", "device", "service", string, optional)
  * `resourceId`: ID of the associated resource (string, optional)
  * `description`: Description of the media (string, optional)

**Response:**

* 201 Created: Media uploaded

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/media/upload \
  -H 'Authorization: Bearer <token>' \
  -F 'file=@/path/to/file.jpg' \
  -F 'userId=123' \
  -F 'resourceType=device' \
  -F 'resourceId=device_123' \
  -F 'description=Device image'
```

---

### 2. Get Media by Media ID

**GET** `/get-media-by-media-id/{mediaId}`

Retrieves details of a specific media file by its ID.

**Path Parameter:**

* `mediaId`: Media ID (string, required)

**Response:**

* 200 OK: Media details (e.g., metadata and file URL)

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/media/get-media-by-media-id/media_123 \
  -H 'Authorization: Bearer <token>'
```

---

### 3. Get Media by User ID

**GET** `/get-media-by-user-id/{userId}`

Retrieves all media files associated with a specific user ID.

**Path Parameter:**

* `userId`: User ID (string, required)

**Response:**

* 200 OK: List of media files

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/media/get-media-by-user-id/123 \
  -H 'Authorization: Bearer <token>'
```

---

### 4. Get Media by Resource

**GET** `/get-media-by-resource/{resourceType}/{resourceId}`

Retrieves all media files associated with a specific resource (e.g., device or service).

**Path Parameters:**

* `resourceType`: Type of resource (e.g., "device", "service", string, required)
* `resourceId`: Resource ID (string, required)

**Response:**

* 200 OK: List of media files

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/media/get-media-by-resource/device/device_123 \
  -H 'Authorization: Bearer <token>'
```

---

### 5. Update Media

**PATCH** `/update`

Updates metadata for an existing media file by its ID.

**Request Body:**

```json
{
  "mediaId": "media_123",
  "description": "Updated media description",
  "resourceType": "service",
  "resourceId": "service_456"
}
```

**Response:**

* 200 OK: Media metadata updated

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/media/update \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"mediaId": "media_123", "description": "Updated media description", "resourceType": "service", "resourceId": "service_456"}'
```

---

### 6. Delete Media by Media ID

**DELETE** `/delete-media-by-media-id/{mediaId}`

Deletes a media file by its ID.

**Path Parameter:**

* `mediaId`: Media ID (string, required)

**Response:**

* 200 OK: Media deleted

**Example Curl:**

```bash
curl -X DELETE https://your-domain.com/app/v1/media/delete-media-by-media-id/media_123 \
  -H 'Authorization: Bearer <token>'
```

---

### 7. Get All Media

**GET** `/get-all-media`

Retrieves all media files in the system (admin access required).

**Response:**

* 200 OK: List of all media files

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/media/get-all-media \
  -H 'Authorization: Bearer <token>'
```

---

### 8. Share Media

**PATCH** `/share`

Shares a media file with another user.

**Request Body:**

```json
{
  "mediaId": "media_123",
  "userEmail": "user@example.com"
}
```

**Response:**

* 200 OK: Media shared

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/media/share \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"mediaId": "media_123", "userEmail": "user@example.com"}'
```

---

### 9. Unshare Media

**PATCH** `/unshare`

Removes sharing of a media file with a user.

**Request Body:**

```json
{
  "mediaId": "media_123",
  "userEmail": "user@example.com"
}
```

**Response:**

* 200 OK: Media unshared

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/media/unshare \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"mediaId": "media_123", "userEmail": "user@example.com"}'
```

---

### 10. Get Shared Media by User ID

**GET** `/get-shared-media-by-user-id/{userId}`

Retrieves all media files shared with a specific user.

**Path Parameter:**

* `userId`: User ID (string, required)

**Response:**

* 200 OK: List of shared media files

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/media/get-shared-media-by-user-id/123 \
  -H 'Authorization: Bearer <token>'
```

---

## Security

These endpoints require a bearer token.

---

[Next Section: Device Types API Documentation](device-types.md)
