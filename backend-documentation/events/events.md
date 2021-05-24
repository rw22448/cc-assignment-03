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
- Status: 400, JSON: `{ error : "Unable to create event" }`

**Example:** `curl -H "Content-Type: application/json" -X POST https://avnaanvefh.execute-api.us-east-1.amazonaws.com/dev/events/create-event -d '{"title": "Road trip", "description": "Annual interstate road trip", "creator": "84422wr", "startTime": "2021-05-22T8:30:00.000Z", "endTime": "2021-05-22T11:30:00.000Z"}'`

**Notes:** `creator` should be ID of user that creates the event. `startTime` and `endTime` should be ISO timestamps of event time.

<br /><hr /><br />

## /get-event-by-id/:id

**URL:** `/events/get-event-by-id/:id`

**Method:** `GET`

**URL (query) params:**

- `id=[string]` REQUIRED

**Data (body) params:**

- None

**Success responses:**

- Status: 200, JSON: `{"id": String, "title": String, "description": String, "creator": String, "attendees": [String], "startTime": String, "endTime": String }`

**Error responses:**

- Status: 400, JSON: `{ error : "Bad request" }`
- Status: 400, JSON: `{ error : "Unable to fetch event" }`
- Status: 404, JSON: `{ error : "Event not found" }`

**Example:** `curl -H "Content-Type: application/json" -X GET https://avnaanvefh.execute-api.us-east-1.amazonaws.com/dev/events/get-event-by-id/672efe76-4e3a-4f0b-8897-056940f0e9b8`

<br /><hr /><br />

## /delete-event-by-id/:id

**URL:** `/events/delete-event-by-id/:id`

**Method:** `DELETE`

**URL (query) params:**

- `id=[string]` REQUIRED

**Data (body) params:**

- None

**Success responses:**

- Status: 200, JSON: `{"id": String }`

**Error responses:**

- Status: 400, JSON: `{ error : "Bad request" }`
- Status: 400, JSON: `{ error : "Unable to delete event" }`
- Status: 404, JSON: `{ error : "Event does not exist found" }`

**Example:** `curl -H "Content-Type: application/json" -X DELETE https://avnaanvefh.execute-api.us-east-1.amazonaws.com/dev/events/delete-event-by-id/672efe76-4e3a-4f0b-8897-056940f0e9b8`

<br /><hr /><br />

## /update-event

**URL:** `/events/update-event`

**Method:** `PUT`

**URL (query) params:**

- None

**Data (body) params:**

- `id=[string]` REQUIRED
- `title=[string]`
- `description=[string]`
- `startTime=[string]`
- `endTime=[string]`

**Success responses:**

- Status: 200, JSON: `{"id": String }`

**Error responses:**

- Status: 400, JSON: `{ error : "Bad request" }`
- Status: 400, JSON: `{ error : "Unable to update event" }`
- Status: 404, JSON: `{ error : "Event does not exist found" }`

**Example:** `curl -H "Content-Type: application/json" -X PUT https://avnaanvefh.execute-api.us-east-1.amazonaws.com/dev/events/update-event -d '{"id": "e2ed2576-32b0-4a31-be86-8d5c711301a7", "description": "This event is cool!"}'`
