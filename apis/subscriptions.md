# Subscriptions API Documentation

This document includes the subscription-related API methods from the Fides API.

---

## Base URL

```
/app/v1/subscriptions
```

---

### 1. Unsubscribe Email with Token

**GET** `/unsubscribe-email`

Unsubscribes a user from email notifications using a token.

**Query Parameter:**

* `token`: Unsubscribe token (string, required)

**Response:**

* 200 OK: Email unsubscribed

**Example Curl:**

```bash
curl -X GET "https://your-domain.com/app/v1/subscriptions/unsubscribe-email?token=unsubscribe_token_string"
```

---

### 2. Check My Email Subscription

**GET** `/check-my-email-subscription`

Checks the email subscription status for the authenticated user.

**Response:**

* 200 OK: Email subscription status

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/subscriptions/check-my-email-subscription \
  -H 'Authorization: Bearer <token>'
```

---

### 3. Set Email Subscription

**POST** `/set-email-subscription`

Sets the email subscription status for a user.

**Request Body:**

```json
{
  "subscribe": true
}
```

**Response:**

* 200 OK: Email subscription status updated

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/subscriptions/set-email-subscription \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"subscribe": true}'
```

---

## Security

The `/check-my-email-subscription` and `/set-email-subscription` endpoints require a bearer token. The `/unsubscribe-email` endpoint does not require authentication.

---

[Next Section: Media API Documentation](media.md)
