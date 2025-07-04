# Theme API Documentation

This document includes all endpoints related to theme and UI customization in the Fides API.

---

## Base URL

```
/app/theme
```

---

### 1. Get All Themes

**GET** `/get-all`

Returns a list of all available UI themes.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/theme/get-all \
  -H 'Authorization: Bearer <token>'
```

---

### 2. Get Theme by ID

**GET** `/get-by-id/{themeId}`

Fetches theme details by its unique ID.

**Example Curl:**

```bash
curl -X GET https://your-domain.com/app/theme/get-by-id/abc123 \
  -H 'Authorization: Bearer <token>'
```

---

### 3. Apply Theme to User

**PATCH** `/apply-to-user`

Applies a selected theme to the current user.

**Request Body:**

```json
{
  "themeId": "abc123"
}
```

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/theme/apply-to-user \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"themeId": "abc123"}'
```

---

### 4. Create Theme (Admin)

**POST** `/create`

Creates a new UI theme.

**Request Body:**

```json
{
  "name": "Dark Mode",
  "primaryColor": "#000000",
  "secondaryColor": "#1A1A1A",
  "font": "Roboto"
}
```

**Example Curl:**

```bash
curl -X POST https://your-domain.com/app/theme/create \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{
    "name": "Dark Mode",
    "primaryColor": "#000000",
    "secondaryColor": "#1A1A1A",
    "font": "Roboto"
  }'
```

---

### 5. Edit Theme (Admin)

**PATCH** `/edit/{themeId}`

Updates an existing theme.

**Request Body:**

```json
{
  "primaryColor": "#111111"
}
```

**Example Curl:**

```bash
curl -X PATCH https://your-domain.com/app/theme/edit/abc123 \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"primaryColor": "#111111"}'
```

---

### 6. Delete Theme

**DELETE** `/delete/{themeId}`

Deletes a theme by its ID.

**Example Curl:**

```bash
curl -X DELETE https://your-domain.com/app/theme/delete/abc123 \
  -H 'Authorization: Bearer <token>'
```

---

**➡️ For user customization settings, see `users.md`.**
