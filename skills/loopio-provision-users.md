---
name: loopio-provision-users
description: Provision, assign and deactivate Loopio users and teams safely, preferring reversible operations.
api: Loopio Public API v2
base_url: https://api.loopio.com/data/v2
generated: '2026-08-25'
method: generated
source: openapi/loopio-openapi.yaml
scopes:
  - user:read
  - user:write
  - role:read
  - businessUnit:write
operations:
  - identifyUser
  - listUsers
  - getUser
  - createUser
  - updateUser
  - listRoles
  - getRole
  - listTeams
  - getTeam
  - bulkAssignRole
  - bulkAssignUsersToTeams
  - bulkAssignBusinessUnitUsers
  - bulkResendActivationEmail
  - bulkUserDisableByEmail
  - bulkRemoveUsers
---

# Provision Loopio users

## Orient yourself

`identifyUser` (`GET /identify/me`) tells you which principal the token represents — call it
first, before any write, to confirm you are acting in the tenant you think you are.

`listRoles` (`GET /roles`) and `listTeams` (`GET /teams`) give you the assignable ids. Roles
are read-only through the API.

## Create and assign

- `createUser` (`POST /users`) creates one user; `updateUser` (`PUT /users/{userId}`) edits one,
  including `UserStatus`.
- Bulk paths exist for the repetitive work: `bulkAssignRole`, `bulkAssignUsersToTeams`,
  `bulkAssignBusinessUnitUsers` and `bulkResendActivationEmail`.
- `bulkAssignBusinessUnitUsers` requires the `businessUnit:write` scope, which the
  authorization server advertises but the OpenAPI `securitySchemes` block does **not** declare.
  If the App was created before that scope existed, expect `403 FORBIDDEN`.

## Deactivate, do not delete

This is the one place in the Loopio API where a reversible option exists, so use it:

- **`bulkUserDisableByEmail`** disables users. A disabled user can be re-enabled through
  `updateUser` by setting `UserStatus` back. This is reversible.
- **`bulkRemoveUsers`** removes them. There is **no** documented restore path and no retention
  window. Treat it as permanent.

Prefer disable. Only remove when the caller has explicitly confirmed permanence.

## Directory sync

Loopio's authorization server advertises `scim.user:read`, `scim.user:write`,
`scim.group:read` and `scim.group:write` scopes, which indicates a SCIM 2.0 provisioning
surface. Those endpoints are **not** in the published OpenAPI — if you need directory-driven
provisioning rather than these REST calls, ask Loopio for the SCIM documentation rather than
guessing at paths.
