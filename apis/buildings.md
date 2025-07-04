Buildings API Documentation
This document includes the building-related API methods from the Fides API.

Base URL
/app/v1/building


1. Create New Building
POST /create
Adds a new building that includes floors and units with devices.
Request Body:
{
  "name": "Building Name",
  "details": {}
}

Response:

201 Created: Building created

Example Curl:
curl -X POST https://your-domain.com/app/v1/building/create \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"name": "Building Name", "details": {}}'


2. Edit Building by Build ID
PATCH /edit-by-build-id
Edits an existing building, including floors and units with devices.
Request Body:
{
  "buildId": "123",
  "data": {}
}

Response:

200 OK: Building updated

Example Curl:
curl -X PATCH https://your-domain.com/app/v1/building/edit-by-build-id \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{"buildId": "123", "data": {}}'


3. Get All Buildings
GET /get-all-buildings
Returns all created buildings with details.
Response:

200 OK: List of buildings

Example Curl:
curl -X GET https://your-domain.com/app/v1/building/get-all-buildings \
  -H 'Authorization: Bearer <token>'


4. Get Buildings by User ID
GET /get-buildings-by-user-id/{userId}
Returns all buildings created by a specific user.
Path Parameter:

userId: User ID (string)

Response:

200 OK: List of user buildings

Example Curl:
curl -X GET https://your-domain.com/app/v1/building/get-buildings-by-user-id/123 \
  -H 'Authorization: Bearer <token>'


5. Get Building by Build ID
GET /get-building-by-build-id/{buildId}
Returns details of a specific building by its ID.
Path Parameter:

buildId: Building ID (string)

Response:

200 OK: Building details

Example Curl:
curl -X GET https://your-domain.com/app/v1/building/get-building-by-build-id/123 \
  -H 'Authorization: Bearer <token>'


6. Delete Building by Build ID
DELETE /delete-by-build-id/{buildId}
Deletes a building by its ID.
Path Parameter:

buildId: Building ID (string)

Response:

200 OK: Building deleted

Example Curl:
curl -X DELETE https://your-domain.com/app/v1/building/delete-by-build-id/123 \
  -H 'Authorization: Bearer <token>'


Security
These endpoints require a bearer token.

Next Section: Authentication API Documentation
