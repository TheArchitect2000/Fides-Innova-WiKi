# MQTT Logs API Documentation

This document provides details on the endpoints related to MQTT communication logs in the Fides API.

---

## Base URL

```
/app/mqtt-log
```

---

### 1. Get All MQTT Logs

**GET** `/get-all`

Retrieves a list of all MQTT logs (admin access).

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/mqtt-log/get-all \
  -H 'Authorization: Bearer <token>'
```

---

### 2. Get MQTT Logs by Device ID

**GET** `/get-by-device-id/{deviceId}`

Fetches logs related to a specific device.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/mqtt-log/get-by-device-id/device123 \
  -H 'Authorization: Bearer <token>'
```

---

### 3. Get MQTT Log by ID

**GET** `/get-by-id/{logId}`

Retrieves details for a single MQTT log entry by its ID.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/mqtt-log/get-by-id/log789 \
  -H 'Authorization: Bearer <token>'
```

---

### 4. Delete MQTT Log by ID

**DELETE** `/delete-by-id/{logId}`

Deletes a specific MQTT log entry.

**Example Curl:**

```bash
curl -X DELETE https://your-domain.com/app/mqtt-log/delete-by-id/log789 \
  -H 'Authorization: Bearer <token>'
```

---

### 5. Filter Logs by Topic

**GET** `/filter-by-topic?topic=device/temperature`

Filters logs based on MQTT topic string.

**Example Curl:**

```bash
curl -X GET "https://your-domain.com/app/mqtt-log/filter-by-topic?topic=device/temperature" \
  -H 'Authorization: Bearer <token>'
```

---

### 6. Search Logs by Keyword

**GET** `/search?query=error&page=1&limit=20`

Searches MQTT logs for a given keyword.

**Example Curl:**

```bash
curl -X GET "https://your-domain.com/app/mqtt-log/search?query=error&page=1&limit=20" \
  -H 'Authorization: Bearer <token>'
```

---

**➡️ For general device logs, see `device-logs.md`.**
