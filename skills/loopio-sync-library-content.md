---
name: loopio-sync-library-content
description: Keep an external system in step with the Loopio Library using incremental polling and webhook subscriptions.
api: Loopio Public API v2
base_url: https://api.loopio.com/data/v2
generated: '2026-08-25'
method: generated
source: openapi/loopio-openapi.yaml
scopes:
  - library:read
  - library:write
  - webhook:read
  - webhook:write
operations:
  - listStacks
  - listLibraryEntries
  - getLibraryEntry
  - getLibraryEntryHistories
  - createLibraryEntry
  - bulkCreateLibraryEntries
  - updateLibraryEntry
  - getAsyncStatus
  - createWebhookSubscription
  - listWebhookSubscriptions
---

# Sync the Loopio Library

## Read the shape first

`listStacks` (`GET /stacks`) returns the Library structure — Stack → Category → subCategory.
Every Library Entry lives at one of those locations, so resolve the structure before you write.

## Incremental pull

`listLibraryEntries` (`GET /libraryEntries`) accepts **`lastUpdatedDateGt`**. This is the
supported change-detection mechanism and the one to build on:

1. Store the high-water mark from your last successful run.
2. Call `listLibraryEntries?lastUpdatedDateGt=<mark>&pageSize=200` — 200 is the declared
   maximum on this operation.
3. Page with `page` until you reach `totalPages`.
4. For each changed entry, `getLibraryEntry` for the full record and
   `getLibraryEntryHistories` (`GET /libraryEntryHistories/{libraryEntryId}`) when you need to
   know *what* changed. History item types are `CREATE`, `UPDATE`, `REVIEW_UPDATE`, `RESTORE`.
5. Advance the high-water mark only after the whole page set succeeded.

## Push

- One entry: `createLibraryEntry` (`POST /libraryEntries`).
- Many: `bulkCreateLibraryEntries` (`POST /libraryEntries/bulk`) — this returns **202** with a
  `taskId`, not the created entries. Poll `getAsyncStatus` (`GET /asyncTasks/{taskId}`) until it
  completes. There is no completion callback.
- Edit: `updateLibraryEntry` (`PATCH /libraryEntries/{libraryEntryId}`) takes an **RFC 6902 JSON
  Patch** document — an array of `{op, path, value}` with JSON Pointer paths, `op` in
  `add|replace|test|remove`. A malformed patch returns a dedicated
  `InvalidJSONPatchDocument` 400; a semantically impossible one returns 422.

## Push-based updates

Rather than polling tightly, subscribe: `createWebhookSubscription`
(`POST /webhookSubscriptions`) with `events: ["libraryEntry.updated"]` and an `https://`
callback URL. Loopio validates the URL as part of the create call, so the subscription starts
`PENDING` and becomes `ACTIVE` only once your endpoint answers correctly.

Verify every delivery: `X-Loopio-Content-Signature` is an HMAC of the JSON body with the
subscription's signing secret, and `X-Loopio-Request-Timestamp` bounds replay. Rotate the
secret with `refreshWebhookSigningSecret` rather than recreating the subscription.

Keep the `lastUpdatedDateGt` poll as a backstop — Loopio publishes no delivery guarantee,
retry policy or dead-letter behaviour for webhooks.
