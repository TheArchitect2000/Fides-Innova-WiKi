# Notifications API Documentation

This document contains all the endpoints used to manage and deliver notifications within the Fides API.

---

## Base URL

```
/app/notification
```

---

### 1. Send Notification

**POST** `/send`

Sends a new notification to a user or group.

**Request Body:**

```json
{
  "title": "System Alert",
  "message": "The system will go down for maintenance at midnight.",
  "userIds": ["user123", "user456"],
  "type": "info"
}
```

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/notification/send \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{
    "title": "System Alert",
    "message": "The system will go down for maintenance at midnight.",
    "userIds": ["user123", "user456"],
    "type": "info"
  }'
```

---

### 2. Get My Notifications

**GET** `/get-my-notifications`

Fetches all notifications sent to the current user.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/notification/get-my-notifications \
  -H 'Authorization: Bearer <token>'
```

---

### 3. Mark Notification as Read

**PATCH** `/mark-as-read/{notificationId}`

Marks a specific notification as read.

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/notification/mark-as-read/notify789 \
  -H 'Authorization: Bearer <token>'
```

---

### 4. Mark All Notifications as Read

**PATCH** `/mark-all-as-read`

Marks all current user's notifications as read.

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/notification/mark-all-as-read \
  -H 'Authorization: Bearer <token>'
```

---

### 5. Delete Notification

**DELETE** `/delete/{notificationId}`

Deletes a specific notification.

**Example Curl:**

```bash
curl -X DELETE https://your-domain.com/app/notification/delete/notify789 \
  -H 'Authorization: Bearer <token>'
```

---

### 6. Delete All Notifications

**DELETE** `/delete-all`

Deletes all notifications for the authenticated user.

**Example Curl:**

```bash
curl -X DELETE https://your-domain.com/app/notification/delete-all \
  -H 'Authorization: Bearer <token>'
```

---

**➡️ For user profiles and alerts, see `users.md`.**
