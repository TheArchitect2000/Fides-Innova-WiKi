# Smart Contract API Documentation

This document includes the smart contract-related API methods from the Fides API.

---

## Base URL

```
/app/v1/contract
```

---

### 1. Verify ZKP

**POST** `/verify-zkp`

Verifying the proof.
This api verifies then user proof code.

**Request Body:**

```json
{
  "proof":"string"
}
```

**Response:**

* 201 Created: Smart contract inserted

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/contract/verify-zkp \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"proof":"string"}'
```

---

### 2. Store Commitment

**POST** `/store-commitment`

Storing the Commitment.
This api will store the user commitment file in smart contract.

**Request Body:**

```json
{
  "transactionId": "string",
  "frontPublish": bool,
  "commitmentID": "string",
  "deviceType": "string",
  "deviceIdType": "string",
  "deviceModel": "string",
  "manufacturer": "string",
  "softwareVersion": "string",
  "commitmentData": "string"
}
```

**Response:**

* 201 Created: Smart contract inserted

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/contract/store-commitment \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"transactionId": "string",
      "frontPublish": true,
      "commitmentID": "string",
      "deviceType": "string",
      "deviceIdType": "string",
      "deviceModel": "string",
      "manufacturer": "string",
      "softwareVersion": "string",
      "commitmentData": "string"
      }'
```

---

### 3. Remove Commitment

**POST** `/remove-commitment`

removing the Commitment.
This api will remove the user commitment file in smart contract.

**Request Body:**

```json
{
  "commitmentId": "string",
  "dbId": "string",
  "nodeId": "string"
}
```

**Response:**

* 201 Created: Smart contract inserted

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/contract/remove-commitment \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"commitmentId": "string",
      "dbId": "string",
      "nodeId": "string"
      }'
```
---

### 4. Get Balance of Wallet 

**GET** `/get-wallet-balance`

This api returns balance of entered wallet.

**Path Parameter:**

* `None`

**Response:**

* 200 OK: balance of entered wallet

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/contract/get-wallet-balance \
  -H 'Authorization: Bearer <token>'
```

---

### 5. User Commitment Saved in Database 

**GET** `/my-commitments`

This api returns commitment of a user that are saved in database.

**Path Parameter:**

* `None`

**Response:**

* 200 OK: commitments of a user that are saved in database.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/contract/my-commitments \
  -H 'Authorization: Bearer <token>'
```

---

### 6. Admin Wallet Address 

**GET** `/admin-wallet`

This api returns wallet address of admin.

**Path Parameter:**

* `None`

**Response:**

* 200 OK: Wallet address of admin.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/contract/admin-wallet \
  -H 'Authorization: Bearer <token>'
```

---

### 7. Faucet Wallet Address 

**GET** `/faucet-wallet`

This api returns wallet address of faucet account.

**Path Parameter:**

* `None`

**Response:**

* 200 OK: wallet address of faucet account.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/contract/faucet-wallet \
  -H 'Authorization: Bearer <token>'
```

---

### 8. Requesting Faucet

**POST** `/request-faucet`

This api give some faucet to user wallet address entered in website.

**Request Body:**

```json
{
  "type": "string",
  "ownerShipWalletAddress": "string"
}
```

**Response:**

* 201 Created: Give some faucet to user wallet address entered in website.

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/contract/request-faucet \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{
      "type": "string",
      "ownerShipWalletAddress": "string"
      }'
```

---

### 9. Publish Proof

**POST** `/publish-proof`

This api will publish proof.

**Request Body:**

```json
{
  "frontPublish": true,
  "deviceType": "string",
  "proof": "string",
  "data": {}
}
```

**Response:**

* 201 Created: Publish proof.

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/contract//publish-proof \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{
      "frontPublish": true,
      "deviceType": "string",
      "proof": "string",
      "data": {}
      }'
```

---

## Security

These endpoints require a bearer token.

---

[Next Section: [Services API Documentation](services.md)
