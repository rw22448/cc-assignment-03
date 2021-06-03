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

- `username: String` REQUIRED

**Data (body) params:**

- None

**Success responses:**

- Status: 200, JSON: `{ username : String }`

**Error responses:**

- Status: 400, JSON: `{ error : "Bad request" }`
- Status: 400, JSON: `{ error : "Unable to fetch user" }`
- Status: 404, JSON: `{ error : "User not found" }`

**Example:** `curl -H "Content-Type: application/json" -X GET https://avnaanvefh.execute-api.us-east-1.amazonaws.com/dev/users/get-user-by-username/rw22448`

<br /><hr /><br />

## /create-user

**URL:** `/users/create-user`

**Method:** `POST`

**URL (query) params:**

- None

**Data (body) params:**

- `username: String` REQUIRED
- `password: String` REQUIRED

**Success responses:**

- Status: 200, JSON: `{ username : String }`

**Error responses:**

- Status: 400, JSON: `{ error : "Username and/or password must be provided" }`
- Status: 400, JSON: `{ error : "Username and/or password must be a string" }`
- Status: 409, JSON: `{ error : "User 'rw22448' already exists' }`
- Status: 400, JSON: `{ error : "Unable to complete request" }`

**Example:** `curl -H "Content-Type: application/json" -X POST https://avnaanvefh.execute-api.us-east-1.amazonaws.com/dev/users/create-user -d '{"username": "rw22448", "password": "rw22448"}'`

<br /><hr /><br />

## /update-user-password

**URL:** `/users/update-user-password`

**Method:** `PUT`

**URL (query) params:**

- None

**Data (body) params:**

- `username: String` REQUIRED
- `password: String` REQUIRED

**Success responses:**

- Status: 200, JSON: `{ username : String }`

**Error responses:**

- Status: 400, JSON: `{ error: "Bad request" }`
- Status: 400, JSON: `{ error: "Unable to update user" }`
- Status: 404, JSON: `{ error: "User 'rw22448' does not exist" }`

**Example:** `curl -H "Content-Type: application/json" -X PUT https://avnaanvefh.execute-api.us-east-1.amazonaws.com/dev/users/update-user-password -d '{"username": "rw22448", "password": "newPassword"}'`

<br /><hr /><br />

## /delete-user-by-username/:username

**URL:** `/users/delete-user-by-username/:username`

**Method:** `DELETE`

**URL (query) params:**

- `username: String` REQUIRED

**Data (body) params:**

- None

**Success responses:**

- Status: 200, JSON: `{ username : String }`

**Error responses:**

- Status: 400, JSON: `{ error: "Bad request" }`
- Status: 400, JSON: `{ error: "Unable to delete user" }`
- Status: 404, JSON: `{ error: "User 'rw22448' does not exist" }`

**Example:** `curl -H "Content-Type: application/json" -X DELETE https://avnaanvefh.execute-api.us-east-1.amazonaws.com/dev/users/delete-user-by-username/rw22448`

<br /><hr /><br />

## /login

**URL:** `/users/login`

**Method:** `POST`

**URL (query) params:**

- None

**Data (body) params:**

- `username: String` REQUIRED
- `password: String` REQUIRED

**Success responses:**

- Status: 200, JSON: `{ username : String, token: String }`

**Error responses:**

- Status: 400, JSON: `{ error: "Bad request" }`
- Status: 400, JSON: `{ error: "Unable to fetch users" }`
- Status: 400, JSON: `{ error: "Unable to complete request" }`
- Status: 401, JSON: `{ error: "Incorrect username and/or password" }`

**Example:** `curl -H "Content-Type: application/json" -X POST https://avnaanvefh.execute-api.us-east-1.amazonaws.com/dev/users/login -d '{"username": "rw22448", "password": "rw22448"}'`

**Notes:** Token is used for authentication inside the main application and needs to be added to every further request. Therefore, it is wise to store the token in local storage for reuse.

<br /><hr /><br />

## /logout

**URL:** `/users/logout`

**Method:** `POST`

**URL (query) params:**

- None

**Data (body) params:**

- `username: String` REQUIRED

**Success responses:**

- Status: 200, JSON: `{ username : String }`

**Error responses:**

- Status: 400, JSON: `{ error: "Bad request" }`
- Status: 400, JSON: `{ error: "Unable to fetch users" }`

**Example:** `curl -H "Content-Type: application/json" -X POST https://avnaanvefh.execute-api.us-east-1.amazonaws.com/dev/users/logout -d '{"username": "rw22448"}'`

<br /><hr /><br />

## /images/get-image-by-username/:username

**URL:** `/users/images/get-image-by-username/:username`

**Method:** `GET`

**URL (query) params:**

- `username: String` REQUIRED

**Data (body) params:**

- None

**Success responses:**

- Status: 200, JSON: `{ username : String, image: String(Base64) }`

**Error responses:**

- Status: 400, JSON: `{ error: "Bad request" }`
- Status: 400, JSON: `{ error: "Unable to complete request, user image may not exist" }`
- Status: 404, JSON: `{ error: "User image does not exist" }`

**Example:** `curl -H "Content-Type: application/json" -X GET https://avnaanvefh.execute-api.us-east-1.amazonaws.com/dev/users/images/get-image-by-username/rw22448`

<br /><hr /><br />

## /images/create-image

**URL:** `/users/images/create-image`

**Method:** `POST`

**URL (query) params:**

- None

**Data (body) params:**

- `username: String` REQUIRED
- `image: String(Base64)` REQUIRED

**Success responses:**

- Status: 200, JSON: `{ username : String, image: String(Base64) }`

**Error responses:**

- Status: 400, JSON: `{ error: "Bad request" }`
- Status: 400, JSON: `{ error: "Unable to complete request" }`

**Example:** `curl -H "Content-Type: application/json" -X POST https://avnaanvefh.execute-api.us-east-1.amazonaws.com/dev/users/images/create-image -d '{"username": "rw2248", "image": "<Base64 encoded image here>"}'`
