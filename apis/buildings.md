# Buildings API Documentation

This document outlines the endpoints used to manage buildings, locations, and spaces in the Fides API.

---

## Base URL

```
/app/building
```

---

### 1. Create Building

**POST** `/create`

Creates a new building record.

**Request Body:**

```json
{
  "name": "Headquarters",
  "location": "Amsterdam, Netherlands",
  "description": "Main office building"
}
```

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/building/create \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{
    "name": "Headquarters",
    "location": "Amsterdam, Netherlands",
    "description": "Main office building"
  }'
```

---

### 2. Get All Buildings

**GET** `/get-all`

Retrieves all buildings available in the system.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/building/get-all \
  -H 'Authorization: Bearer <token>'
```

---

### 3. Get Building by ID

**GET** `/get-by-id/{buildingId}`

Retrieves detailed info for a specific building.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/building/get-by-id/abc123 \
  -H 'Authorization: Bearer <token>'
```

---

### 4. Edit Building

**PATCH** `/edit/{buildingId}`

Updates details of an existing building.

**Request Body:**

```json
{
  "name": "Updated HQ",
  "description": "Renovated main office"
}
```

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/building/edit/abc123 \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"name": "Updated HQ", "description": "Renovated main office"}'
```

---

### 5. Delete Building

**DELETE** `/delete/{buildingId}`

Deletes a building from the system.

**Example Curl:**

```bash
curl -X DELETE https://your-domain.com/app/building/delete/abc123 \
  -H 'Authorization: Bearer <token>'
```

---

### 6. Search Buildings

**GET** `/search?query=office`

Searches for buildings by keyword.

**Example Curl:**

```bash
curl -X GET "https://your-domain.com/app/building/search?query=office" \
  -H 'Authorization: Bearer <token>'
```

---

**➡️ For devices inside buildings, see `devices.md`.**
