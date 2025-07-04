# Smart Contract & ZKP API Documentation

This document includes all endpoints related to smart contracts and zero-knowledge proof (ZKP) workflows in the Fides API.

---

## Base URL

```
/app/smart-contract
```

---

### 1. Submit ZKP Commitment

**POST** `/submit-commitment`

Submits a ZKP commitment from the user for validation.

**Request Body:**

```json
{
  "deviceId": "device001",
  "commitment": "0xabc123...",
  "proof": "zkp-proof-data"
}
```

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/smart-contract/submit-commitment \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{
    "deviceId": "device001",
    "commitment": "0xabc123...",
    "proof": "zkp-proof-data"
  }'
```

---

### 2. Get Commitments by Device ID

**GET** `/get-commitments-by-device-id/{deviceId}`

Fetches all commitments submitted for a given device.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/smart-contract/get-commitments-by-device-id/device001 \
  -H 'Authorization: Bearer <token>'
```

---

### 3. Get All Commitments (Admin)

**GET** `/get-all-commitments`

Returns all commitments across all devices and users.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/smart-contract/get-all-commitments \
  -H 'Authorization: Bearer <token>'
```

---

### 4. Verify Commitment

**POST** `/verify-commitment`

Triggers the verification logic for a submitted commitment.

**Request Body:**

```json
{
  "commitment": "0xabc123...",
  "proof": "zkp-proof-data"
}
```

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/smart-contract/verify-commitment \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{
    "commitment": "0xabc123...",
    "proof": "zkp-proof-data"
  }'
```

---

### 5. Get Commitment by ID

**GET** `/get-commitment-by-id/{commitmentId}`

Returns detailed information about a single commitment.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/smart-contract/get-commitment-by-id/abc123 \
  -H 'Authorization: Bearer <token>'
```

---

### 6. Delete Commitment (Admin)

**DELETE** `/delete-commitment/{commitmentId}`

Deletes a commitment by its ID (admin access).

**Example Curl:**

```bash
curl -X DELETE https://your-domain.com/app/smart-contract/delete-commitment/abc123 \
  -H 'Authorization: Bearer <token>'
```

---

Next Section: [Services API Documentation](services.md)
