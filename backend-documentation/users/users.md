# /users

API for user-related features, such as creating a user, fetching a user, updating user details, etc.

## Base URL

- Local: `http://localhost:3000`
- Dev: `https://avnaanvefh.execute-api.us-east-1.amazonaws.com/dev`

<br /><hr /><br />

## /get-user-by-username/:username

**URL:** `/users/get-user-by-username/:username`

**Method:** `GET`

**URL (query) params:**

- `username=[string]` REQUIRED

**Data (body) params:**

- None

**Success responses:**

- Status: 200, JSON: `{ username : username }`

**Error responses:**

- Status: 400, JSON: `{ error : "Bad request" }`
- Status: 400, JSON: `{ error : "Unable to fetch user" }`
- Status: 404, JSON: `{ error : "User not found" }`

**Example:** `curl -H "Content-Type: application/json" -X GET https://avnaanvefh.execute-api.us-east-1.amazonaws.com/dev/users/get-user-by-username/rw22448`

<br /><hr /><br />

## /get-user-by-username/:username

**URL:** `/users/create-user`

**Method:** `POST`

**URL (query) params:**

- None

**Data (body) params:**

- `username=[string]` REQUIRED
- `password=[string]` REQUIRED

**Success responses:**

- Status: 200, JSON: `{ username : username }`

**Error responses:**

- Status: 400, JSON: `{ error : "Username and/or password must be a string" }`
- Status: 400, JSON: `{ error : "Unable to create user" }`
- Status: 400, JSON: `{ error : "User 'rw22448" already exists' }`

**Example:** `curl -H "Content-Type: application/json" -X POST https://avnaanvefh.execute-api.us-east-1.amazonaws.com/dev/users/create-user -d '{"username": "rw22448", "password": "rw22448"}'`
