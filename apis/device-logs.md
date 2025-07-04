# Device Logs API Documentation

This document includes all endpoints related to device operation logs in the Fides API.

---

## Base URL

```
/app/device-log
```

---

### 1. Get All Device Logs

**GET** `/get-all`

Returns a list of all device logs (admin access).

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/device-log/get-all \
  -H 'Authorization: Bearer <token>'
```

---

### 2. Get Logs by Device ID

**GET** `/get-by-device-id/{deviceId}`

Fetches logs for a specific device.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/device-log/get-by-device-id/device123 \
  -H 'Authorization: Bearer <token>'
```

---

### 3. Get Device Log by ID

**GET** `/get-by-id/{logId}`

Returns a specific log entry by its unique ID.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/device-log/get-by-id/log456 \
  -H 'Authorization: Bearer <token>'
```

---

### 4. Delete Log by ID

**DELETE** `/delete-by-id/{logId}`

Deletes a specific log record.

**Example Curl:**

```bash
curl -X DELETE https://your-domain.com/app/device-log/delete-by-id/log456 \
  -H 'Authorization: Bearer <token>'
```

---

### 5. Filter Logs by Type

**GET** `/filter-by-type?type=error`

Filters device logs by the log type (e.g., error, info).

**Example Curl:**

```bash
curl -X GET "https://your-domain.com/app/device-log/filter-by-type?type=error" \
  -H 'Authorization: Bearer <token>'
```

---

### 6. Search Device Logs

**GET** `/search?query=overheat&page=1&limit=10`

Search logs by keyword with pagination.

**Example Curl:**

```bash
curl -X GET "https://your-domain.com/app/device-log/search?query=overheat&page=1&limit=10" \
  -H 'Authorization: Bearer <token>'
```

---

**➡️ For device management and services, see `devices.md` and `services.md`.**
