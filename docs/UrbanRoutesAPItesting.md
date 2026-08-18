# Urban Scooter Backend API — Courier Test Cases

## Overview

This is Task 3 of the TripleTen QA Engineering final project: API testing of the **Add Courier** (`POST`) and **Delete Courier** (`DELETE`) endpoints in the Urban Scooter backend, using the project's test environment.

Test cases cover successful creation and deletion, required vs. optional field validation, duplicate-resource handling (`409 Conflict`), and not-found/malformed-request handling (`404`/`400`) — each request is documented with exact JSON request bodies or path parameters.

**Approach:** Requests were sent directly against the API using Postman, with each test case documenting the exact JSON request body or path parameter used, so results are independently reproducible.

- **Component:** Urban Scooter Backend API
- **Endpoints tested:** `POST /api/v1/courier`, `DELETE /api/v1/courier/{id}`
- **Tool:** Postman

## Summary

| Metric | Count |
|---|---|
| Total test cases | 9 |
| Passed | 8 |
| Failed | 1 |
| Bugs filed in Jira | 1 |

## Bugs Found

| Bug ID | Endpoint | Summary |
|---|---|---|
| [FPQT-31](https://tstewart5487qa.atlassian.net/browse/FPQT-31) | `DELETE /api/v1/courier/` | Missing `:id` path parameter returns `404 Not Found` instead of the expected `400 Bad Request` with a clear validation message. |

---

## Courier Creation — `POST /api/v1/courier`

| ID | Test Case | Precondition | Request Body | Expected Result | Actual Result | Status | Bug |
|---|---|---|---|---|---|---|---|
| 1 | Verify `201 Created` on successful courier creation | Server is started | `{"login": "ninja", "password": "1234", "firstName": "saske"}` | `201 Created` — `{ ok: true }` | `201 Created` … |
| 2 | Verify `400 Bad Request` with missing `login` parameter | Server is started | `{"password": "1234", "firstName": "saske"}` | `400 Bad Request` — `"Not enough data to create an account"` | … |
| 3 | Verify `400 Bad Request` with missing `password` parameter | Server is started | `{"login": "ninja", "firstName": "saske"}` | `400 Bad Request` — `"Not enough data to create an account"` | … |
| 4 | Verify `201 Created` with missing `firstName` parameter (optional field) | Server is started | `{"login": "ninja", "password": "1234"}` | `201 Created` — `{ ok: true }` | `201 Created` — … |
| 5 | Verify `409 Conflict` when creating a duplicate courier | Server is started, courier already created | `{"login": "ninja", "password": "1234", "firstName": "saske"}` | `409 Conflict` — `\"T…` |

**Notes:** Test case 4 confirms `firstName` is an optional field per the requirements — omitting it still returns a successful `201 Created`, distinguishing it from the required `login` and `password` fields.

## Courier Deletion — `DELETE /api/v1/courier/{id}`

| ID | Test Case | Precondition | Request | Expected Result | Actual Result | Status | Bug |
|---|---|---|---|---|---|---|---|
| 6 | Verify `200 OK` when an existing courier is removed | Server is started, courier is created | `DELETE /api/v1/courier/1` | `200 OK` — `{ ok: true }` | `200 OK` — `{ ok: true }` | Passed … |
| 7 | Verify `404 Not Found` when deleting an already-deleted courier | Server is started, courier is created and deleted | `DELETE /api/v1/courier/1` | `404 Not Found` — `"There's no courier wi…` |
| 8 | Verify `404 Not Found` when deleting a courier that does not exist | Server is started, courier is created | `DELETE /api/v1/courier/99` | `404 Not Found` — `"There's no courier with this …` |
| 9 | Verify `400 Bad Request` when the `:id` path parameter is missing | Server is started, courier is created | `DELETE /api/v1/courier/` | `400 Bad Request` — `"Not enough data to remove the …` |

### Notes

- **FPQT-31:** When the `:id` path parameter is omitted entirely (hitting the base `/courier/` route with no trailing ID), the API returns a generic routing-level `404 Not Found` rather than the application-level `400 Bad Request` expected by the requirements.
