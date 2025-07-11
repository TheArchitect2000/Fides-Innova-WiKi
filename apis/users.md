# Users API Documentation 

This document includes the user-related API methods from the Fides API.

---

## Base URL

```
/app/v1/user
```

---

### 1. Request OTP for Signup (Email)

**POST** `/request-otp-code-for-signup-by-email`

Sends an OTP to the user's email address for signup.

**Request Body:**

```json
{
  "email": "user@example.com",
  "password": "securePassword123"
}
```

**Response:**

* 200 OK: OTP sent

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/user/request-otp-code-for-signup-by-email \
  -H 'Content-Type: application/json' \
  -d '{"email": "user@example.com", "password": "securePassword123"}'
```

---

### 2. Request OTP for Reset Password (Email)

**POST** `/request-otp-code-for-reset-password-by-email`

Sends an OTP to the user's email for resetting the password.

**Request Body:**

```json
{
  "email": "user@example.com"
}
```

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/user/request-otp-code-for-reset-password-by-email \
  -H 'Content-Type: application/json' \
  -d '{"email": "user@example.com"}'
```

---

### 3. Request OTP for Verify Email

**POST** `/request-otp-code-for-verify-email`

Requires Bearer Token.

**Request Body:**

```json
{
  "email": "user@example.com"
}
```

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/user/request-otp-code-for-verify-email \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"email": "user@example.com"}'
```

---

### 4. Verify OTP for Signup

**GET** `/verify-otp-code-sent-by-email-for-signup`

**Query Parameters:**

* `email`: Email address
* `otp`: One-time password code

**Example Curl:**

```bash
curl -X GET "https://your-domain.com/app/v1/user/verify-otp-code-sent-by-email-for-signup?email=user@example.com&otp=123456"
```

---

### 5. Verify OTP for Reset Password

**GET** `/verify-otp-code-sent-by-email-for-reset-password`

**Query Parameters:**

* `email`: Email address
* `otp`: One-time password code

**Example Curl:**

```bash
curl -X GET "https://your-domain.com/app/v1/user/verify-otp-code-sent-by-email-for-reset-password?email=user@example.com&otp=123456"
```

---

### 6. Verify OTP for Verify Email

**GET** `/verify-otp-code-sent-by-email-for-verify-email`

**Query Parameters:**

* `email`: Email address
* `otp`: One-time password code

**Example Curl:**

```bash
curl -X GET "https://your-domain.com/app/v1/user/verify-otp-code-sent-by-email-for-verify-email?email=user@example.com&otp=123456"
```

---

### 7. Generic OTP Verification

**POST** `/verify-otp-code-sent-by-email`

Verifies the OTP sent to a user’s email.

**Request Body:**

```json
{
  "email": "user@example.com",
  "otp": "123456",
  "otpType": "Type1"
}
```

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/user/verify-otp-code-sent-by-email \
  -H 'Content-Type: application/json' \
  -d '{"email": "user@example.com", "otp": "123456", "otpType": "Type1"}'
```

---

### 8. Change Password and Activate Account

**POST** `/change-password-and-activate-account`

**Request Body:**

```json
{
  "email": "user@example.com",
}
```

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/user/change-password-and-activate-account \
  -H 'Content-Type: application/json' \
  -d '{"email": "user@example.com"}'
```

---

### 9. Request OTP by Mobile

**GET** `/request-otp-code/{mobile}`

**Path Parameter:**

* `mobile`: Phone number

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/user/request-otp-code/+1234567890
```

---

### 10. Reset Password by OTP

**PATCH** `/reset-password-by-otp-code`

**Request Body:**

```json
{
  "email": "user@example.com",
  "otp": "123456",
  "password": "StrongPassword!2024"
}
```

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/user/reset-password-by-otp-code \
  -H 'Content-Type: application/json' \
  -d '{"email": "user@example.com", "otp": "123456", "password": "StrongPassword!2024"}'
```

---

### 11. User Credential (Login)

**POST** `/credential`

Logs in the user using email and password.

**Request Body:**

```json
{
  "email": "user@example.com",
  "password": "yourPassword123"
}
```

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/user/credential \
  -H 'Content-Type: application/json' \
  -d '{"email": "user@example.com", "password": "yourPassword123"}'
```

---

### 12. Admin Credential (Login)

**POST** `/admin-credential`

Logs in an admin user.

**Request Body:**

```json
{
  "email": "admin@example.com",
  "password": "adminPassword"
}
```

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/user/admin-credential \
  -H 'Content-Type: application/json' \
  -d '{"email": "admin@example.com", "password": "adminPassword"}'
```

---

### 13. Check Password

**POST** `/check-password`

Validates a user’s password.

**Request Body:**

```json
{
  "enteredPassword": "userPassword123",
  "userPassword": "userPassword123"
}
```

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/user/check-password \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"enteredPassword": "userPassword123", "userPassword": "userPassword123"}'
```

---

### 14. Refresh Tokens

**POST** `/refresh-tokens`

Returns a new access token and refresh token.

**Request Body:**

```json
{
  "oldAccessToken": "your_old_access_token",
  "refreshToken": "your_refresh_token"
}
```

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/user/refresh-tokens \
  -H 'Content-Type: application/json' \
  -d '{"oldAccessToken": "your_old_access_token", "refreshToken": "your_refresh_token"}'
```

---

### 15. Get My Profile

**GET** `/get-my-profile`

Returns the profile data of the currently logged-in user.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/user/get-my-profile \
  -H 'Authorization: Bearer <token>'
```

---

### 16. Get User by Email

**GET** `/get-user-by-email/{userEmail}`

Returns user details for the given email.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/user/get-user-by-email/user@example.com \
  -H 'Authorization: Bearer <token>'
```

---

### 17. Set Identity Wallet

**POST** `/set-my-identitity-wallet`

Sets the identity wallet for the user.

**Request Body:**

```json
{
  "wallet": "0xABCDEF..."
}
```

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/user/set-my-identitity-wallet \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"wallet": "0xABCDEF..."}'
```

---

### 18. Set Ownership Wallet

**POST** `/set-my-ownership-wallet`

Sets the ownership wallet for the user.

**Request Body:**

```json
{
  "wallet": "0x123456..."
}
```

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/user/set-my-ownership-wallet \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"wallet": "0x123456..."}'
```

---

### 19. Edit My Profile

**PATCH** `/edit-user-by-user/{userId}`

Edits the user profile fields such as name.

**Request Body:**

```json
{
  "firstName": "John",
  "lastName": "Doe",
  "email": "user@example.com",
  "mobile": "+1234567890",
  "walletAddress": "0xABCDEF...",
  "title": "Your Title",
  "avatar": "Your Avatar",
  "lang": "en"
}
```

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/user/edit-user-by-user/123 \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"firstName": "John",
    "lastName": "Doe",
    "email": "user@example.com",
    "mobile": "+1234567890",
    "walletAddress": "0xABCDEF...",
    "title": "Your Title",
    "avatar": "Your Avatar",
    "lang": "en"}'
```

---

### 20. Change My Profile Activation

**PATCH** `/change-my-profile-activation`

Activates or deactivates the user's profile.

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/user/change-my-profile-activation \
  -H 'Authorization: Bearer <token>'
```

---

### 21. Request Reset Password Code (Mobile)

**GET** `/request-reset-password-code`

Sends a reset password OTP to the user’s registered mobile number.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/user/request-reset-password-code \
  -H 'Authorization: Bearer <token>'
```

---

### 22. Verify Reset Password Code

**PATCH** `/verify-reset-password-code`

Verifies OTP for resetting the password via mobile.

**Request Body:**

```json
{
  "email": "user@example.com",
  "otp": "123456",
  "newPassword": "NewPass@2024"
}
```

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/user/verify-reset-password-code \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"email": "user@example.com", "otp": "123456", "newPassword": "NewPass@2024"}'
```

---

### 23. Get Profile by ID

**GET** `/get-profile-by-id/{userId}`

Returns profile details for the given user ID.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/user/get-profile-by-id/123 \
  -H 'Authorization: Bearer <token>'
```

---

### 24. Get Profile by Email

**GET** `/get-profile-by-email/{userEmail}`

Returns profile details for the given email.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/user/get-profile-by-email/user@example.com \
  -H 'Authorization: Bearer <token>'
```

---

### 25. Check if Email Exists

**GET** `/check-user-email-is-exists/{userEmail}`

Checks whether a user with the given email exists.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/user/check-user-email-is-exists/user@example.com
```

---

### 26. Make User Admin

**POST** `/give-admin`

Grants admin privileges to a user.

**Request Body:**

```json
{
  "userEmail": "user@example.com",
  "roleNames": [
    "role1"
  ]
}
```

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/user/give-admin \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"userEmail": "user@example.com",
    "roleNames": [
    "role1"
  ]
}'
```

---

### 27. Get Short Roles by Email

**GET** `/get-short-roles/{userEmail}`

Retrieves a summarized list of roles for a user.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/user/get-short-roles/user@example.com \
  -H 'Authorization: Bearer <token>'
```

---

### 28. Take an User Admin Ranks

**POST** `/take-admin`

This api will take user admin ranks.

**Request Body:**

```json
{
  "userEmail": "user@example.com",
  "roleNames": [
    "role1"
  ]
}
```

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/user/take-admin \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"userEmail": "user@example.com",
      "roleNames": [
        "role1"
        ]
      }'
```

---

### 29. Change Profile Activation 

**PATCH** `/change-profile-activation/{userId}`

Toggles the activation status of a user's profile.

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/user/change-profile-activation/123 \
  -H 'Authorization: Bearer <token>'
```

---

### 30. Change Profile Verification 

**PATCH** `/change-profile-verification/{userId}`

Toggles the verification status of a user's profile.

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/user/change-profile-verification/123 \
  -H 'Authorization: Bearer <token>'
```

---

### 31. Get All Users

**GET** `/get-all-users`

Retrieves all users in the system .

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/user/get-all-users \
  -H 'Authorization: Bearer <token>'
```


---

### 32. Search Users

**GET** `/search?searchText=...&pageNumber=...&limit=...`

Search users by keyword with pagination.

**Query Parameters:**

* `pageNumber`: Number of Page (number)
* `limit`: Limit item in each page (number)
* `sortMode`: sortMode of all advertising (string)
* `searchText`: Each text you want to search (string)
* `fromDate`: From Date (string)
* `toDate`: To Date (string)
* `activation`: Activation status of users Available values : active, inactive, banned, blocked (string)
* `verification`: Verification status of users Available values : unverified, pending, verified (string)
 


**Example Curl:**

```bash
curl -X GET "https://your-domain.com/app/user/search?searchText=admin&pageNumber=1&limit=10&...." \
  -H 'Authorization: Bearer <token>'
```


---

### 33. Delete All User Data

**DELETE** `/delete-all-user-data?userId=...`

Deletes all data related to the specified user ID.

**Query Parameters:**

* `userId`: user ID (string)


**Example Curl:**

```bash
curl -X DELETE "https://your-domain.com/app/v1/user/delete-all-user-data?userId=123" \
  -H 'Authorization: Bearer <token>'
```

---

### 34. Request Change Email Token

**POST** `/request-change-email-token`

Sends a token to the user to verify their intention to change email.

**Request Body:**

```json
{
  "newEmail": "new@example.com"
}
```

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/user/request-change-email-token \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"newEmail": "new@example.com"}'
```

---

### 35. Verify Change Email with Token

**POST** `/verify-change-email-with-token`

Verifies token and changes the user's email.
This api save a token for changing email in database.

**Request Body:**

```json
{
  "token": "email-change-token"
}
```

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/user/verify-change-email-with-token \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"token": "email-change-token"}'
```

---

## Security

These endpoints typically require a bearer token.

---

Next Section: [MQTT Logs API Documentation](mqtt-logs.md)

