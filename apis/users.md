# Users API Documentation

This document provides full details about all user-related endpoints in the Fides API. These endpoints handle signup, OTP verification, password reset, profile management, role management, and administrative actions.

---

## Base URL

```
/app/v1/user
```

---

## Endpoints

### 🔐 Authentication & OTP

#### 1. Request OTP for Signup (Email)

* **POST** `/request-otp-code-for-signup-by-email`
* Sends OTP to email for signup

#### 2. Request OTP for Reset Password (Email)

* **POST** `/request-otp-code-for-reset-password-by-email`

#### 3. Request OTP for Email Verification

* **POST** `/request-otp-code-for-verify-email` *(Requires Bearer Token)*

#### 4. Verify OTP for Signup

* **GET** `/verify-otp-code-sent-by-email-for-signup?email=...&otp=...`

#### 5. Verify OTP for Reset Password

* **GET** `/verify-otp-code-sent-by-email-for-reset-password?email=...&otp=...`

#### 6. Verify OTP for Email Verification

* **GET** `/verify-otp-code-sent-by-email-for-verify-email?email=...&otp=...`

#### 7. Generic OTP Verification (Email)

* **POST** `/verify-otp-code-sent-by-email`

#### 8. Change Password and Activate Account

* **POST** `/change-password-and-activate-account`

#### 9. Request OTP via Mobile

* **GET** `/request-otp-code/{mobile}`

#### 10. Reset Password by OTP

* **PATCH** `/reset-password-by-otp-code`

### 🔑 Credentials and Tokens

#### 11. User Credential (Login)

* **POST** `/credential`

#### 12. Admin Credential (Login)

* **POST** `/admin-credential`

#### 13. Check Password

* **POST** `/check-password`

#### 14. Refresh Tokens

* **POST** `/refresh-tokens`

### 👤 Profile & Account Management

#### 15. Get My Profile

* **GET** `/get-my-profile` *(Requires Bearer Token)*

#### 16. Get User by Email

* **GET** `/get-user-by-email/{userEmail}` *(Requires Bearer Token)*

#### 17. Set Identity Wallet

* **POST** `/set-my-identitity-wallet` *(Requires Bearer Token)*

#### 18. Set Ownership Wallet

* **POST** `/set-my-ownership-wallet` *(Requires Bearer Token)*

#### 19. Edit My Profile

* **PATCH** `/edit-user-by-user/{userId}` *(Requires Bearer Token)*

#### 20. Change Profile Activation (Self)

* **PATCH** `/change-my-profile-activation` *(Requires Bearer Token)*

#### 21. Request Reset Password Code (Mobile)

* **GET** `/request-reset-password-code` *(Requires Bearer Token)*

#### 22. Verify Reset Password Code

* **PATCH** `/verify-reset-password-code` *(Requires Bearer Token)*

#### 23. Get Profile by ID

* **GET** `/get-profile-by-id/{userId}` *(Requires Bearer Token)*

#### 24. Get Profile by Email

* **GET** `/get-profile-by-email/{userEmail}` *(Requires Bearer Token)*

#### 25. Check Email Exists

* **GET** `/check-user-email-is-exists/{userEmail}`

#### 26. Delete All User Data

* **DELETE** `/delete-all-user-data?userId=...` *(Requires Bearer Token)*

### 🛡️ Admin Actions

#### 27. Make User Admin

* **POST** `/app/user/give-admin` *(Requires Bearer Token)*

#### 28. Remove Admin Rank

* **POST** `/app/user/take-admin` *(Requires Bearer Token)*

#### 29. Change Profile Activation (By Admin)

* **PATCH** `/app/user/change-profile-activation/{userId}` *(Requires Bearer Token)*

#### 30. Change Profile Verification (By Admin)

* **PATCH** `/app/user/change-profile-verification/{userId}` *(Requires Bearer Token)*

#### 31. Get Short Roles

* **GET** `/app/user/get-short-roles/{userEmail}` *(Requires Bearer Token)*

### 🔍 Search & Retrieve

#### 32. Get All Users

* **GET** `/get-all-users` *(Requires Bearer Token)*

#### 33. Search Users

* **GET** `/app/user/search?searchText=...&pageNumber=...&limit=...` *(Requires Bearer Token)*

### ✉️ Change Email

#### 34. Request Change Email Token

* **POST** `/request-change-email-token` *(Requires Bearer Token)*

#### 35. Verify Change Email with Token

* **POST** `/verify-change-email-with-token` *(Requires Bearer Token)*

---

This document now includes **all 59 user-related endpoints** found in the Swagger definition.

Next Section: [Devices API Documentation](devices.md)
