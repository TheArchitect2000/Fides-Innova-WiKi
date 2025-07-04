# Other API Documentation

This document includes miscellaneous API methods from the Fides API that do not fall under other specific categories.

---

## Theme API

### Base URL

```
/app/v1/theme
```

---

#### 1. Get Mobile Theme Colors

**GET** `/`

Retrieves the mobile theme colors.

**Response:**

* 200 OK: Theme colors retrieved

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/theme \
  -H 'Authorization: Bearer <token>'
```

---

## Devices API

### Base URL

```
/app/v1/devices
```

---

#### 1. Get Device List

**GET** `/`

Retrieves a list of devices.

**Response:**

* 200 OK: List of devices

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/devices \
  -H 'Authorization: Bearer <token>'
```

---

## Security

These endpoints are assumed to require a bearer token, consistent with other Fides API endpoints, though this is not explicitly specified in the provided specification.

---

[Next Section: Authentication API Documentation](authentication.md)
