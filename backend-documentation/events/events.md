# /events

API for events, including creating an event, deleting an event, fetching an event, etc.

## Base URL

- Local: `http://localhost:3000`
- Dev: `https://avnaanvefh.execute-api.us-east-1.amazonaws.com/dev`

<br /><hr /><br />

## /create-event

**URL:** `/events/create-event`

**Method:** `POST`

**URL (query) params:**

- None

**Data (body) params:**

- `title=[string]` REQUIRED
- `description=[string]` REQUIRED
- `creator=[string]` REQUIRED
- `startTime=[string]` REQUIRED
- `endTime=[string]` REQUIRED

**Success responses:**

- Status: 200, JSON: `{"id": String, "title": String, "description": String, "creator": String, "attendees": [String], "startTime": String, "endTime": String }`

**Error responses:**

- Status: 400, JSON: `{ error : "Bad request" }`
- Status: 400, JSON: `{ error : "Unable to fetch user" }`
- Status: 404, JSON: `{ error : "User not found" }`

**Example:** `curl -H "Content-Type: application/json" -X POST https://avnaanvefh.execute-api.us-east-1.amazonaws.com/dev/events/create-event -d '{"title": "Road trip", "description": "Annual interstate road trip", "creator": "84422wr", "startTime": "2021-05-22T8:30:00.000Z", "endTime": "2021-05-22T11:30:00.000Z"}'`

**Notes:** `creator` should be ID of user that creates the event. `startTime` and `endTime` should be ISO timestamps of event time.
