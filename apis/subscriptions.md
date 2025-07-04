# Subscriptions API Documentation

This document includes the subscription-related API methods from the Fides API.

---

## Base URL

```
/app/v1/subscription
```

---

### 1. Create Subscription

**POST** `/create`

Creates a new subscription for a user.

**Request Body:**

```json
{
  "userId": "123",
  "planId": "plan_001",
  "status": "active",
  "startDate": "2025-07-04",
  "endDate": "2026-07-04",
  "paymentMethod": "credit_card"
}
```

**Response:**

* 201 Created: Subscription created

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/subscription/create \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"userId": "123", "planId": "plan_001", "status": "active", "startDate": "2025-07-04", "endDate": "2026-07-04", "paymentMethod": "credit_card"}'
```

---

### 2. Get Subscription by Subscription ID

**GET** `/get-subscription-by-subscription-id/{subscriptionId}`

Retrieves details of a specific subscription by its ID.

**Path Parameter:**

* `subscriptionId`: Subscription ID (string, required)

**Response:**

* 200 OK: Subscription details

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/subscription/get-subscription-by-subscription-id/sub_123 \
  -H 'Authorization: Bearer <token>'
```

---

### 3. Get Subscriptions by User ID

**GET** `/get-subscriptions-by-user-id/{userId}`

Retrieves all subscriptions for a specific user ID.

**Path Parameter:**

* `userId`: User ID (string, required)

**Response:**

* 200 OK: List of user subscriptions

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/subscription/get-subscriptions-by-user-id/123 \
  -H 'Authorization: Bearer <token>'
```

---

### 4. Update Subscription

**PATCH** `/update`

Updates an existing subscription by its ID.

**Request Body:**

```json
{
  "subscriptionId": "sub_123",
  "planId": "plan_002",
  "status": "active",
  "endDate": "2026-12-31",
  "paymentMethod": "paypal"
}
```

**Response:**

* 200 OK: Subscription updated

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/subscription/update \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"subscriptionId": "sub_123", "planId": "plan_002", "status": "active", "endDate": "2026-12-31", "paymentMethod": "paypal"}'
```

---

### 5. Cancel Subscription

**PATCH** `/cancel`

Cancels a subscription by its ID.

**Request Body:**

```json
{
  "subscriptionId": "sub_123"
}
```

**Response:**

* 200 OK: Subscription canceled

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/subscription/cancel \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"subscriptionId": "sub_123"}'
```

---

### 6. Get All Subscriptions

**GET** `/get-all-subscriptions`

Retrieves all subscriptions in the system.

**Response:**

* 200 OK: List of all subscriptions

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/subscription/get-all-subscriptions \
  -H 'Authorization: Bearer <token>'
```

---

### 7. Get Active Subscriptions

**GET** `/get-active-subscriptions`

Retrieves all active subscriptions in the system.

**Response:**

* 200 OK: List of active subscriptions

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/subscription/get-active-subscriptions \
  -H 'Authorization: Bearer <token>'
```

---

### 8. Renew Subscription

**PATCH** `/renew`

Renews an existing subscription by its ID.

**Request Body:**

```json
{
  "subscriptionId": "sub_123",
  "endDate": "2027-07-04"
}
```

**Response:**

* 200 OK: Subscription renewed

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/subscription/renew \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"subscriptionId": "sub_123", "endDate": "2027-07-04"}'
```

---

### 9. Get Subscription Plans

**GET** `/get-subscription-plans`

Retrieves all available subscription plans.

**Response:**

* 200 OK: List of subscription plans

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/subscription/get-subscription-plans \
  -H 'Authorization: Bearer <token>'
```

---

### 10. Delete Subscription by Subscription ID

**DELETE** `/delete-subscription-by-subscription-id/{subscriptionId}`

Deletes a subscription by its ID.

**Path Parameter:**

* `subscriptionId`: Subscription ID (string, required)

**Response:**

* 200 OK: Subscription deleted

**Example Curl:**

```bash
curl -X DELETE https://your-domain.com/app/v1/subscription/delete-subscription-by-subscription-id/sub_123 \
  -H 'Authorization: Bearer <token>'
```

---

## Security

These endpoints require a bearer token.

---

[Next Section: Device Types API Documentation](device-types.md)
