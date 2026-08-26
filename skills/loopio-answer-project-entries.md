---
name: loopio-answer-project-entries
description: Walk a Loopio Project's questions, find matching approved answers in the Library, and write them back into the Project's entries.
api: Loopio Public API v2
base_url: https://api.loopio.com/data/v2
generated: '2026-08-25'
method: generated
source: openapi/loopio-openapi.yaml
scopes:
  - project:read
  - project:write
  - library:read
operations:
  - getProject
  - listProjectSections
  - listProjectSubSections
  - listProjectEntries
  - listLibraryEntries
  - getLibraryEntry
  - updateProjectEntry
  - getProjectSummary
---

# Answer a Loopio Project from the Library

The core Loopio flow: a Project holds the questions from an RFP or questionnaire; the Library
holds reusable approved answers. This skill maps one onto the other.

## Before you start

- Get a token: `POST https://api.loopio.com/oauth2/access_token` with
  `grant_type=client_credentials`, `client_id`, `client_secret` and a space-delimited `scope`
  of `project:read project:write library:read`. The token is a Bearer token and lives 3600s.
- Scopes are fixed when the Loopio Admin creates the App. If a call returns `403` with
  `name: FORBIDDEN`, the App lacks the scope and no retry will fix it — a new App is required.

## Steps

1. **Read the project.** `getProject` on `GET /projects/{projectId}`. Confirm status and type
   before writing anything.
2. **Walk the structure.** `listProjectSections` (`GET /sections?projectId=`) then
   `listProjectSubSections` (`GET /subSections`). Loopio nests Section → subSection → Entry.
3. **List the questions.** `listProjectEntries` (`GET /projectEntries`). Paginate with
   `page` and `pageSize`; stop when `page` exceeds `totalPages` in the response envelope.
4. **Search the Library.** `listLibraryEntries` (`GET /libraryEntries`) with `searchQuery` set
   from the question text. Filter to entries whose `status` is `APPROVED`. Read
   `scores.freshness` and `lastReviewedDate` — a stale answer is a worse answer.
5. **Read the full answer.** `getLibraryEntry` (`GET /libraryEntries/{libraryEntryId}`) with
   `inline[]` where you need images resolved.
6. **Write the answer back.** `updateProjectEntry` — `PUT /projectEntries/{projectEntryId}`.
   This is a full replacement, not a merge: send the complete entry body.
7. **Check your work.** `getProjectSummary` (`GET /projects/{projectId}/summary`) returns the
   status roll-up for the Project.

## Rules

- **No idempotency keys.** This API has none. `updateProjectEntry` is a PUT and is safe to
  repeat, but never blind-retry a `createProjectEntry` POST — you will create a duplicate.
  On an ambiguous failure, re-list and reconcile before writing again.
- **No rate-limit signal.** No `429`, no `X-RateLimit-*`, no `Retry-After` is declared. Pace
  yourself conservatively and back off on any `500`/`503`.
- **Errors** are `{name, message, debugId}` — not RFC 9457. `debugId` is the only correlation
  handle in this API; capture it on every failure, because a successful call gives you nothing
  to trace with.
- **Deletes are irreversible through the API.** Never call `deleteProjectEntry` to "clear" an
  answer — update it instead.
