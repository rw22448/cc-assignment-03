# /events

API for events, including creating an event, deleting an event, fetching an event, etc.

## Base URL

- Local: `http://localhost:3000`
- Dev: `https://avnaanvefh.execute-api.us-east-1.amazonaws.com/dev`

**Notes:** All of the endpoints below require the `cc-authentication-user` and `cc-authentication-token` header to be set correctly after logging in.

<br /><hr /><br />

## /create-event

**URL:** `/events/create-event`

**Method:** `POST`

**URL (query) params:**

- None

**Data (body) params:**

- `title: String` REQUIRED
- `description: String` REQUIRED
- `creator: String` REQUIRED
- `startTime: String` REQUIRED
- `endTime: String` REQUIRED

**Success responses:**

- Status: 200, JSON: `{"id": String, "title": String, "description": String, "creator": String, "attendees": [String], "startTime": String, "endTime": String }`

**Error responses:**

- Status: 400, JSON: `{ error: "Bad request" }`
- Status: 400, JSON: `{ error: "Unable to create event" }`
- Status: 401, JSON: `{ error: "Unauthorized" }`

**Example:** `curl -H "Content-Type: application/json" -H "cc-authentication-user: 84422wr" -H "cc-authentication-token: 6207adb3-521f-46cc-84cf-e00acb5e515c" -X POST https://avnaanvefh.execute-api.us-east-1.amazonaws.com/dev/events/create-event -d '{"title": "Road trip", "description": "Annual interstate road trip", "creator": "84422wr", "startTime": "2021-05-22T8:30:00.000Z", "endTime": "2021-05-22T11:30:00.000Z"}'`

**Notes:** `creator` should be ID of user that creates the event. `startTime` and `endTime` should be ISO timestamps of event time.

<br /><hr /><br />

## /get-event-by-id/:id

**URL:** `/events/get-event-by-id/:id`

**Method:** `GET`

**URL (query) params:**

- `id: String` REQUIRED

**Data (body) params:**

- None

**Success responses:**

- Status: 200, JSON: `{"id": String, "title": String, "description": String, "creator": String, "attendees": [String], "startTime": String, "endTime": String }`

**Error responses:**

- Status: 400, JSON: `{ error: "Bad request" }`
- Status: 400, JSON: `{ error: "Unable to fetch event" }`
- Status: 404, JSON: `{ error: "Event not found" }`
- Status: 401, JSON: `{ error: "Unauthorized" }`

**Example:** `curl -H "Content-Type: application/json" -H "cc-authentication-user: 84422wr" -H "cc-authentication-token: 6207adb3-521f-46cc-84cf-e00acb5e515c" -X GET https://avnaanvefh.execute-api.us-east-1.amazonaws.com/dev/events/get-event-by-id/672efe76-4e3a-4f0b-8897-056940f0e9b8`

<br /><hr /><br />

## /delete-event-by-id/:id

**URL:** `/events/delete-event-by-id/:id`

**Method:** `DELETE`

**URL (query) params:**

- `id: String` REQUIRED

**Data (body) params:**

- None

**Success responses:**

- Status: 200, JSON: `{"id": String }`

**Error responses:**

- Status: 400, JSON: `{ error: "Bad request" }`
- Status: 400, JSON: `{ error: "Unable to delete event" }`
- Status: 404, JSON: `{ error: "Event does not exist" }`
- Status: 401, JSON: `{ error: "Unauthorized" }`

**Example:** `curl -H "Content-Type: application/json" -H "cc-authentication-user: 84422wr" -H "cc-authentication-token: 6207adb3-521f-46cc-84cf-e00acb5e515c" -X DELETE https://avnaanvefh.execute-api.us-east-1.amazonaws.com/dev/events/delete-event-by-id/672efe76-4e3a-4f0b-8897-056940f0e9b8`

<br /><hr /><br />

## /update-event

**URL:** `/events/update-event`

**Method:** `PUT`

**URL (query) params:**

- None

**Data (body) params:**

- `id: String` REQUIRED
- `title: String`
- `description: String`
- `startTime: String`
- `endTime: String`

**Success responses:**

- Status: 200, JSON: `{"id": String }`

**Error responses:**

- Status: 400, JSON: `{ error: "Bad request" }`
- Status: 400, JSON: `{ error: "Unable to update event" }`
- Status: 404, JSON: `{ error: "Event does not exist" }`
- Status: 401, JSON: `{ error: "Unauthorized" }`

**Example:** `curl -H "Content-Type: application/json" -H "cc-authentication-user: 84422wr" -H "cc-authentication-token: 6207adb3-521f-46cc-84cf-e00acb5e515c" -X PUT https://avnaanvefh.execute-api.us-east-1.amazonaws.com/dev/events/update-event -d '{"id": "e2ed2576-32b0-4a31-be86-8d5c711301a7", "description": "This event is cool!"}'`

<br /><hr /><br />

## /add-attendees

**URL:** `/events/add-attendees`

**Method:** `PUT`

**URL (query) params:**

- None

**Data (body) params:**

- `id: String` REQUIRED
- `attendees: String[]` REQUIRED

**Success responses:**

- Status: 200, JSON: `{"id": String, "attendees": String[] }`

**Error responses:**

- Status: 400, JSON: `{ error: "Bad request" }`
- Status: 400, JSON: `{ error: "Unable to update event" }`
- Status: 404, JSON: `{ error: "Event does not exist" }`
- Status: 401, JSON: `{ error: "Unauthorized" }`

**Example:** `curl -H "Content-Type: application/json" -H "cc-authentication-user: 84422wr" -H "cc-authentication-token: 6207adb3-521f-46cc-84cf-e00acb5e515c" -X PUT https://avnaanvefh.execute-api.us-east-1.amazonaws.com/dev/events/add-attendees -d '{"id": "f0426f8e-b354-4d0a-b5bf-fd3ee99c588b", "attendees": ["rw22448"]}'`

<br /><hr /><br />

## /remove-attendees

**URL:** `/events/remove-attendees`

**Method:** `PUT`

**URL (query) params:**

- None

**Data (body) params:**

- `id: String` REQUIRED
- `attendees: String[]` REQUIRED

**Success responses:**

- Status: 200, JSON: `{"id": String, "attendees": String[] }`

**Error responses:**

- Status: 400, JSON: `{ error: "Bad request" }`
- Status: 400, JSON: `{ error: "Unable to update event" }`
- Status: 404, JSON: `{ error: "Event does not exist" }`
- Status: 401, JSON: `{ error: "Unauthorized" }`

**Example:** `curl -H "Content-Type: application/json" -H "cc-authentication-user: 84422wr" -H "cc-authentication-token: 6207adb3-521f-46cc-84cf-e00acb5e515c" -X PUT https://avnaanvefh.execute-api.us-east-1.amazonaws.com/dev/events/remove-attendees -d '{"id": "f0426f8e-b354-4d0a-b5bf-fd3ee99c588b", "attendees": ["rw22448"]}'`
