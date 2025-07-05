# Theme API Documentation

---

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

## Security

These endpoints are assumed to require a bearer token, consistent with other Fides API endpoints, though this is not explicitly specified in the provided specification.

---

[Next Section: Devices API Documentation](devices.md)
