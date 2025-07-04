# Users API Documentation

This document provides full details about the user-related endpoints in the Fides API. These endpoints handle signup, OTP verification, password reset, profile management, and more.

---

## Base URL

```
/app/v1/user
```

---

## Endpoints

### 1. Request OTP for Signup (Email)

**URL:** `/request-otp-code-for-signup-by-email`
**Method:** `POST`
**Tag:** `Manage Users`

**Description:**
Sends an OTP code to the user’s email for signup.

**Request Body:**

```json
{
  "email": "user@example.com",
  "password": "yourPassword123"
}
```

**Response:**

* **200 OK**: OTP sent.

---

### 2. Request OTP for Reset Password (Email)

**URL:** `/request-otp-code-for-reset-password-by-email`
**Method:** `POST`

**Description:**
Sends an OTP code to the user’s email to reset their password.

**Request Body:**

```json
{
  "email": "user@example.com"
}
```

**Response:**

* **200 OK**: OTP sent.

---

### 3. Request OTP for Email Verification

**URL:** `/request-otp-code-for-verify-email`
**Method:** `POST`

**Security:** Bearer token required

**Request Body:**

```json
{
  "email": "user@example.com"
}
```

**Response:**

* **200 OK**: OTP sent.

---

### 4. Verify OTP for Signup

**URL:** `/verify-otp-code-sent-by-email-for-signup`
**Method:** `GET`

**Query Parameters:**

* `email` (string, required)
* `otp` (string, required)

**Response:**

* **200 OK**: Verified

---

### 5. Verify OTP for Reset Password

**URL:** `/verify-otp-code-sent-by-email-for-reset-password`
**Method:** `GET`

**Query Parameters:**

* `email` (string, required)
* `otp` (string, required)

**Response:**

* **200 OK**: Verified

---

### 6. Change Password and Activate Account

**URL:** `/change-password-and-activate-account`
**Method:** `POST`

**Request Body:**

```json
{
  "email": "user@example.com",
  "newPassword": "newPassword123",
  "otp": "123456"
}
```

**Response:**

* **200 OK**: Password changed and account activated.

---

### 7. Get My Profile

**URL:** `/get-my-profile`
**Method:** `GET`
**Security:** Bearer token required

**Response:**

* **200 OK**: User profile returned.

---

### 8. Get User By Email

**URL:** `/get-user-by-email/{userEmail}`
**Method:** `GET`
**Path Parameter:** `userEmail`

**Security:** Bearer token required

**Response:**

* **200 OK**: User object returned.

---

### 9. Edit My Profile

**URL:** `/edit-user-by-user/{userId}`
**Method:** `PATCH`

**Security:** Bearer token required

**Request Body:**

```json
{
  "firstName": "John",
  "lastName": "Doe"
}
```

**Response:**

* **200 OK**: Profile updated.

---

### 10. Delete All User Data

**URL:** `/delete-all-user-data`
**Method:** `DELETE`
**Query Parameter:** `userId`

**Security:** Bearer token required

**Response:**

* **200 OK**: All user data deleted.

---

### 11. Check If Email Exists

**URL:** `/check-user-email-is-exists/{userEmail}`
**Method:** `GET`

**Response:**

* **200 OK**: Boolean or status.

---

### 12. Make User Admin / Remove Admin

**POST** `/user/give-admin`
**POST** `/user/take-admin`
**Request Body:**

```json
{
  "email": "user@example.com"
}
```

**Security:** Bearer token required

**Response:**

* **201 Created**

---

**Other Endpoints (Listed):**

* Refresh tokens
* Send OTP by mobile
* Check password
* Set identity/ownership wallets
* Get profile by ID or Email
* Activate or verify profile by admin
* Search users

Due to size, these will be documented in `users_extended.md`

---

Next Section: [Devices API Documentation](devices.md)
