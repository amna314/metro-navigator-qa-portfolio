# API Testing: AI-Powered Metro Bus Navigator

## Overview

Manual UI testing confirms an application looks correct from a user's point of view, but it cannot always tell you whether a bug lives in the interface or in the backend logic underneath it. To close that gap, the backend REST API was tested directly using Postman, independent of the Flutter frontend, to validate that the Flask server returns correct data, correct status codes, and correct error handling under both normal and invalid conditions.

This complements the manual UI test suite (`Login_Test_Cases.xlsx`, `Route_Test_Cases.xlsx`) already documented in this repository.

**Key difference between the two suites:**
- UI test suite: does the screen behave correctly?
- API test suite: does the backend behave correctly, regardless of what the screen shows?

## Scope

The backend exposes REST endpoints for authentication, station/route data, route search, feedback, notifications, and admin operations. Testing focused on the two highest-traffic, highest-risk areas of the application:

- **`/api/login`**: authentication is the entry point to the app; a failure here blocks every other feature
- **`/api/search`**: the app's core feature, and the most complex endpoint in the codebase (fuzzy station matching, interchange disambiguation, multi-priority pathfinding)

A supporting check on `/api/stations` confirms the underlying station data, used by nearly every other feature, loads correctly.

**Note on scope:** the application's endpoints are entirely GET and POST. There are no PUT, PATCH, or DELETE operations, because the app does not expose any user-facing "edit" or "delete" functionality on existing records (admin station open/close is handled as a POST action instead). This was confirmed by reviewing the Flask route definitions directly rather than assumed.

## Approach

Each test case follows a predict-then-verify structure: the expected HTTP status code and response shape were written down before sending the request, then compared against the actual result. This mirrors how status codes are used in real QA work, as a fast, reliable signal of success or failure, checked alongside the response body itself.

**Test coverage includes:**
- Positive cases: valid login, valid route search
- Negative cases: wrong password, missing required field
- Edge case: searching from a station name that is genuinely ambiguous (an interchange where two lines meet), which the backend is designed to catch and resolve by returning clarification options rather than silently guessing the wrong platform

## Results

| Metric | Value |
|---|---|
| Test cases executed | 6 |
| Passed | 6 |
| Failed | 0 |
| Tool | Postman |

Full details, endpoint, method, request payload, expected vs. actual status, and result, are in [`API_Test_Cases.xlsx`](./API_Test_Cases.xlsx).

The saved Postman collection used to run these tests is included as `Metro_Bus_API_Test.postman_collection.json`, and can be imported directly into Postman to re-run the full suite against a locally running instance of the backend (`python app.py`, served at `http://127.0.0.1:5000`).

## Key Finding Worth Highlighting

The interchange-ambiguity test (`TC_API_002`) is not a bug. It's a verification that a deliberate safety feature in the backend works as intended.

**What it checks:** when a station name matches more than one physical platform (for example, "Faiz Ahmed Faiz" exists on both the Red Line and Orange Line), the backend refuses to guess and instead returns both options for the caller to disambiguate.

**Why it matters:** this confirms the app won't silently route a user onto the wrong line at a shared station name, a real-world failure mode that would be easy to miss with UI testing alone, since the UI would simply show a route, not necessarily reveal that a wrong assumption was made underneath it.
