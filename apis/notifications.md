# Notifications API Documentation

This document includes the notification-related API methods from the Fides API.

---

## Base URL

```
/app/v1/notification
```

---

### 1. Get Notifications by User ID

**GET** `/get-notifications-by-user-id/{userId}`

Retrieves all notifications for a specific user ID.

**Path Parameter:**

* `userId`: User ID (string, required)

**Response:**

* 200 OK: List of notifications for the user

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/notification/get-notifications-by-user-id/123 \
  -H 'Authorization: Bearer <token>'
```

---

### 2. Mark Notification as Read

**PATCH** `/mark-as-read`

Marks a notification as read by its ID.

**Request Body:**

```json
{
  "notificationId": "123"
}
```

**Response:**

* 200 OK: Notification marked as read

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/notification/mark-as-read \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"notificationId": "123"}'
```

---

### 3. Delete Notification by Notification ID

**DELETE** `/delete-notification-by-notification-id/{notificationId}`

Deletes a notification by its ID.

**Path Parameter:**

* `notificationId`: Notification ID (string, required)

**Response:**

* 200 OK: Notification deleted

**Example Curl:**

```bash
curl -X DELETE https://your-domain.com/app/v1/notification/delete-notification-by-notification-id/123 \
  -H 'Authorization: Bearer <token>'
```

---

### 4. Create Notification

**POST** `/create`

Creates a new notification for a user.

**Request Body:**

```json
{
  "userId": "123",
  "title": "New Notification",
  "message": "This is a notification message",
  "type": "info",
  "priority": "normal"
}
```

**Response:**

* 201 Created: Notification created

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/notification/create \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"userId": "123", "title": "New Notification", "message": "This is a notification message", "type": "info", "priority": "normal"}'
```

---

### 5. Get Unread Notifications by User ID

**GET** `/get-unread-notifications-by-user-id/{userId}`

Retrieves all unread notifications for a specific user ID.

**Path Parameter:**

* `userId`: User ID (string, required)

**Response:**

* 200 OK: List of unread notifications

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/notification/get-unread-notifications-by-user-id/123 \
  -H 'Authorization: Bearer <token>'
```

---

### 6. Mark All Notifications as Read

**PATCH** `/mark-all-as-read/{userId}`

Marks all notifications for a specific user as read.

**Path Parameter:**

* `userId`: User ID (string, required)

**Response:**

* 200 OK: All notifications marked as read

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/notification/mark-all-as-read/123 \
  -H 'Authorization: Bearer <token>'
```

---

### 7. Get Notification by Notification ID

**GET** `/get-notification-by-notification-id/{notificationId}`

Retrieves details of a specific notification by its ID.

**Path Parameter:**

* `notificationId`: Notification ID (string, required)

**Response:**

* 200 OK: Notification details

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/notification/get-notification-by-notification-id/123 \
  -H 'Authorization: Bearer <token>'
```

---

### 8. Update Notification

**PATCH** `/update`

Updates an existing notification by its ID.

**Request Body:**

```json
{
  "notificationId": "123",
  "title": "Updated Notification",
  "message": "Updated notification message",
  "type": "warning",
  "priority": "high"
}
```

**Response:**

* 200 OK: Notification updated

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/notification/update \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"notificationId": "123", "title": "Updated Notification", "message": "Updated notification message", "type": "warning", "priority": "high"}'
```

---

### 9. Get Notifications by Type

**GET** `/get-notifications-by-type/{userId}`

Retrieves notifications for a specific user by notification type.

**Path Parameter:**

* `userId`: User ID (string, required)

**Query Parameters:**

* `type`: Notification type (string, required, e.g., "info", "warning", "error")

**Response:**

* 200 OK: List of notifications of the specified type

**Example Curl:**

```bash
curl -X GET "https://your-domain.com/app/v1/notification/get-notifications-by-type/123?type=info" \
  -H 'Authorization: Bearer <token>'
```

---

### 10. Delete All Notifications by User ID

**DELETE** `/delete-all-notifications-by-user-id/{userId}`

Deletes all notifications for a specific user.

**Path Parameter:**

* `userId`: User ID (string, required)

**Response:**

* 200 OK: All notifications deleted

**Example Curl:**

```bash
curl -X DELETE https://your-domain.com/app/v1/notification/delete-all-notifications-by-user-id/123 \
  -H 'Authorization: Bearer <token>'
```

---

## Security

These endpoints require a bearer token.

---

[Next Section: Device Types API Documentation](device-types.md)
