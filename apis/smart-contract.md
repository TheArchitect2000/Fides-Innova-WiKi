# Smart Contract API Documentation

This document includes the smart contract-related API methods from the Fides API.

---

## Base URL

```
/app/v1/smart-contract
```

---

### 1. Insert Smart Contract

**POST** `/insert`

Inserts a new smart contract.

**Request Body:**

```json
{
  "contractName": "Contract Name",
  "description": "Contract Description",
  "contractType": "Type",
  "status": "Active",
  "blocklyJson": "{}",
  "code": "contract code",
  "devices": ["deviceId1", "deviceId2"],
  "services": ["serviceId1", "serviceId2"]
}
```

**Response:**

* 201 Created: Smart contract inserted

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/v1/smart-contract/insert \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"contractName": "Contract Name", "description": "Contract Description", "contractType": "Type", "status": "Active", "blocklyJson": "{}", "code": "contract code", "devices": ["deviceId1", "deviceId2"], "services": ["serviceId1", "serviceId2"]}'
```

---

### 2. Request Smart Contract Publish

**PATCH** `/request-smart-contract-publish`

Requests to publish a smart contract.

**Request Body:**

```json
{
  "smartContractId": "123"
}
```

**Response:**

* 201 Created: Publish request submitted

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/smart-contract/request-smart-contract-publish \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"smartContractId": "123"}'
```

---

### 3. Publish Smart Contract

**PATCH** `/publish-smart-contract`

Publishes a smart contract that has been requested for publishing.

**Request Body:**

```json
{
  "smartContractId": "123"
}
```

**Response:**

* 201 Created: Smart contract published

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/smart-contract/publish-smart-contract \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"smartContractId": "123"}'
```

---

### 4. Reject Smart Contract

**PATCH** `/reject-smart-contract`

Rejects a smart contract that has been requested for publishing.

**Request Body:**

```json
{
  "smartContractId": "123"
}
```

**Response:**

* 201 Created: Smart contract rejected

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/smart-contract/reject-smart-contract \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"smartContractId": "123"}'
```

---

### 5. Cancel Smart Contract Request

**PATCH** `/cancel-smart-contract-request`

Cancels a smart contract publish request.

**Request Body:**

```json
{
  "smartContractId": "123"
}
```

**Response:**

* 201 Created: Smart contract request canceled

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/smart-contract/cancel-smart-contract-request \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"smartContractId": "123"}'
```

---

### 6. Edit Smart Contract

**PATCH** `/edit`

Edits a smart contract by its ID and other fields.

**Request Body:**

```json
{
  "smartContractId": "123",
  "contractName": "Updated Contract Name",
  "description": "Updated Description",
  "contractType": "Type",
  "status": "Active",
  "devices": ["deviceId1", "deviceId2"],
  "services": ["serviceId1", "serviceId2"],
  "contractImage": "image_url",
  "blocklyJson": "{}",
  "code": "updated contract code"
}
```

**Response:**

* 200 OK: Smart contract updated

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/v1/smart-contract/edit \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"smartContractId": "123", "contractName": "Updated Contract Name", "description": "Updated Description", "contractType": "Type", "status": "Active", "devices": ["deviceId1", "deviceId2"], "services": ["serviceId1", "serviceId2"], "contractImage": "image_url", "blocklyJson": "{}", "code": "updated contract code"}'
```

---

### 7. Get Smart Contracts by User ID

**GET** `/get-smart-contracts-by-user-id/{userId}`

Retrieves all smart contracts associated with a specific user ID.

**Path Parameter:**

* `userId`: User ID (string, required)

**Response:**

* 200 OK: List of user smart contracts

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/smart-contract/get-smart-contracts-by-user-id/123 \
  -H 'Authorization: Bearer <token>'
```

---

### 8. Get Smart Contract by Smart Contract ID

**GET** `/get-smart-contract-by-smart-contract-id/{smartContractId}`

Retrieves a smart contract by its ID.

**Path Parameter:**

* `smartContractId`: Smart Contract ID (string, required)

**Response:**

* 200 OK: Smart contract details

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/smart-contract/get-smart-contract-by-smart-contract-id/123 \
  -H 'Authorization: Bearer <token>'
```

---

### 9. Get All Published Smart Contracts

**GET** `/get-all-published-smart-contracts`

Retrieves all smart contracts that are published.

**Response:**

* 200 OK: List of published smart contracts

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/smart-contract/get-all-published-smart-contracts \
  -H 'Authorization: Bearer <token>'
```

---

### 10. Get All Publish Requested Smart Contracts

**GET** `/get-all-publish-requested-smart-contracts`

Retrieves all smart contracts that have requested to be published.

**Response:**

* 200 OK: List of publish-requested smart contracts

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/smart-contract/get-all-publish-requested-smart-contracts \
  -H 'Authorization: Bearer <token>'
```

---

### 11. Get All Smart Contracts

**GET** `/get-all-smart-contracts`

Retrieves all smart contracts in the system.

**Response:**

* 200 OK: List of all smart contracts

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/v1/smart-contract/get-all-smart-contracts \
  -H 'Authorization: Bearer <token>'
```

---

### 12. Delete Smart Contract by Smart Contract ID

**DELETE** `/delete-smart-contract-by-smart-contract-id/{smartContractId}`

Deletes a smart contract by its ID.

**Path Parameter:**

* `smartContractId`: Smart Contract ID (string, required)

**Response:**

* 200 OK: Smart contract deleted

**Example Curl:**

```bash
curl -X DELETE https://your-domain.com/app/v1/smart-contract/delete-smart-contract-by-smart-contract-id/123 \
  -H 'Authorization: Bearer <token>'
```

---

## Security

These endpoints require a bearer token.

---

[Next Section: Device Types API Documentation](device-types.md)
