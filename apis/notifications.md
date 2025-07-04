# Notifications API Documentation

This document includes the notification-related API methods from the Fides API.

---

## Base URL

```
/app/v1/notification
```

---

### 1. Send Firebase Token

**POST** `/sendToken`

Saves a Firebase token for a user to enable push notifications.

**Request Body:**

```json
{
  "token": "firebase_token_string"
}
```

**Response:**

* 201 Created: Firebase token saved

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/notification/sendToken \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"token": "firebase_token_string"}'
```

---

### 2. Add Notification by User ID

**POST** `/add-notification-by-user-id`

Adds a notification for a specific user when opening the app or site.

**Request Body:**

```json
{
  "userId": "123",
  "title": "New Notification",
  "message": "This is a notification message"
}
```

**Response:**

* 201 Created: Notification added

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/notification/add-notification-by-user-id \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{
      "userId": "123",
      "title": "New Notification",
      "message": "This is a notification message"
      }'
```

---

### 3. Add Notification by User Email

**POST** `/add-notification-by-user-email`

Adds a notification for a user identified by their email when opening the app or site.

**Request Body:**

```json
{
  "userEmail": "user@example.com",
  "title": "New Notification",
  "message": "This is a notification message"
}
```

**Response:**

* 201 Created: Notification added

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/notification/add-notification-by-user-email \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{
      "userEmail": "user@example.com",
      "title": "New Notification",
      "message": "This is a notification message"
      }'
```

---

### 4. Add Public Notification

**POST** `/add-public-notification`

Adds a public notification for all users when opening the app or site.

**Request Body:**

```json
{
  "title": "Public Notification",
  "message": "This is a public notification for all users",
  "expiryDate": 0
}
```

**Response:**

* 201 Created: Public notification added

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/notification/add-public-notification \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{
      "title": "Public Notification",
      "message": "This is a public notification for all users",
      "expiryDate": 0
      }'
```

---

### 5. Get Unread Notifications by User ID

**GET** `/get-unread-notifications-by-user-id/{userId}`

Retrieves all unread notifications for a specific user when opening the app or site.

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

### 6. Get All Notifications by User ID

**GET** `/get-all-notifications-by-user-id/{userId}`

Retrieves all notifications (read and unread) for a specific user when opening the app or site.

**Path Parameter:**

* `userId`: User ID (string, required)

**Response:**

* 200 OK: List of all notifications

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/notification/get-all-notifications-by-user-id/123 \
  -H 'Authorization: Bearer <token>'
```

---

### 7. Get Public Notifications

**GET** `/get-public-notifications`

Retrieves all public notifications for all users when opening the app or site.

**Response:**

* 200 OK: List of public notifications

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/notification/get-public-notifications \
  -H 'Authorization: Bearer <token>'
```

---

### 8. Get Notification by ID

**GET** `/get-notification-by-id/{notifId}`

Retrieves a specific notification by its ID when opening the app or site.

**Path Parameter:**

* `notifId`: Notification ID (string, required)

**Response:**

* 200 OK: Notification details

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/notification/get-notification-by-id/123 \
  -H 'Authorization: Bearer <token>'
```

---

### 9. Read Notification by Notification ID List

**PATCH** `/read-notification-by-notif-id-list`

Marks one or more notifications as read by their IDs.

**Request Body:**

```json
{
  "notificationIds": ["notif_123", "notif_456"]
}
```

**Response:**

* 200 OK: Notifications marked as read

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/notification/read-notification-by-notif-id-list \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"notificationIds": ["notif_123", "notif_456"]}'
```

---

### 10. Edit Notification by ID

**PATCH** `/edit-notification-by-id`

Edits a notification by its ID.

**Request Body:**

```json
{
  "notifId": "notif_123",
  "title": "Updated Notification",
  "message": "Updated notification message",
  "notifId": "string"
}
```

**Response:**

* 200 OK: Notification updated

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/notification/edit-notification-by-id \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{
      "notifId": "notif_123",
      "title": "Updated Notification",
      "message": "Updated notification message",
      "notifId": "string"
      }'
```

---

## Security

These endpoints require a bearer token.

---

Next Section: [Subscriptions API Documentation](subscriptions.md)
