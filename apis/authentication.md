# Authentication API Documentation

This document provides detailed information about the authentication-related endpoints in the Fides API. These endpoints are responsible for handling Google login and token verification.

---

## Base URL

```
/app/authentication
```

---

## Endpoints

### 1. Verify Google Token

**URL:** `/google/token`
**Method:** `POST`
**Tag:** `Manage Authentication`

**Description:**
Verifies the Google ID token sent by the client and performs the login/registration process.

**Request Body:**

```json
{

}
```

**Response:**

* **201 Created**: Token verified successfully and user authenticated.

**Example Curl:**

```bash
curl -X POST \
  https://your-domain.com/app/authentication/google/token \
  -H 'Content-Type: application/json' \
  -d '{"idToken": "your_google_id_token"}'
```

---

### 2. Google Login Callback

**URL:** `/google/redirect`
**Method:** `GET`
**Tag:** `Manage Authentication`

**Description:**
Handles the OAuth2 redirect callback from Google after user login.

**Request Parameters:** None

**Response:**

* **200 OK**: The redirect and token handling completed.

**Example Curl:**

```bash
curl -X GET \
  https://your-domain.com/app/authentication/google/redirect
```

---

## Security

These endpoints typically do not require a bearer token as they are part of the authentication initiation process.

---

Next Section: [Users API Documentation](users.md)
