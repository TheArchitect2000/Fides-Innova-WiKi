# MQTT Logs API Documentation

This document provides details on the endpoints related to MQTT communication logs in the Fides API.

---

## Base URL

```
/app/v1/broker-mqtt-log
```


---

### 1. Logs Device Events

**POST** `/log-device-event`

This api requires a user encrypted device id and event.

**Request Body:**

```json
{
  "deviceEncryptedId": "string",
  "event": "string"
}
```

**Response:**

* 200 OK

**Example Curl:**

```bash
curl -X POST https://your-domain.com//app/v1/broker-mqtt-log/log-device-event \
  -H 'Content-Type: application/json' \
  -d '{"deviceEncryptedId": "string", "event": "string"}'
```

---

### 2. Logs Device Data

**POST** `/log-device-data`

This api requires a user encrypted device id and data and sender device id.

**Request Body:**

```json
{
  "deviceEncryptedId": "string",
  "event": "string",
  "data": "string",
  "senderDeviceEncryptedId": "string"
}
```

**Response:**

* 200 OK

**Example Curl:**

```bash
curl -X POST https://your-domain.com//app/v1/broker-mqtt-log/log-device-data \
  -H 'Content-Type: application/json' \
  -d '{"deviceEncryptedId": "string",
  "event": "string",
  "data": "string",
  "senderDeviceEncryptedId": "string"}'
```


---

Next Section: [Smart Contract & ZKP API Documentation](smart-contract.md)
