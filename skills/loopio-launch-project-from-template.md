---
name: loopio-launch-project-from-template
description: Create a Loopio Project from a template, attach the source document, set custom fields and merge variables, and assign participants.
api: Loopio Public API v2
base_url: https://api.loopio.com/data/v2
generated: '2026-08-25'
method: generated
source: openapi/loopio-openapi.yaml
scopes:
  - project:read
  - project:write
  - project.participant:write
  - customProjectField:read
  - mergeVariable:read
  - crm:write
operations:
  - listProjectTemplates
  - createProjectFromTemplate
  - getProjectTemplateCopyAsyncStatus
  - createProject
  - addProjectSourceDocument
  - listProjectSourceDocuments
  - listCustomProjectFields
  - setCustomProjectFieldValuesForProject
  - setMergeVariableValuesForProject
  - updateProjectParticipants
  - createOpportunityLink
  - updateProject
---

# Launch a Loopio Project

## Pick a start

- **From a template (preferred):** `listProjectTemplates` (`GET /projectTemplates`), then
  `createProjectFromTemplate` (`POST /projectTemplates/{projectTemplateId}/projects`). This is
  **asynchronous**: it returns `202` with a `taskId`. Poll
  `getProjectTemplateCopyAsyncStatus` (`GET /asyncTasks/{taskId}/projectTemplateCopy`) until it
  resolves, and take the project id from there. Do not re-POST while a task is pending — there
  are no idempotency keys and you will create a second Project.
- **From scratch:** `createProject` (`POST /projects`).

## Fill it in

1. **Source document.** `addProjectSourceDocument`
   (`POST /projects/{projectId}/sourceDocuments`), then confirm with
   `listProjectSourceDocuments`.
2. **Custom fields.** `listCustomProjectFields` to learn the field ids, then
   `setCustomProjectFieldValuesForProject`
   (`PATCH /projects/{projectId}/customProjectFields`) — a JSON Patch document.
3. **Merge variables.** `setMergeVariableValuesForProject`
   (`PATCH /projects/{projectId}/mergeVariables`). Requires both `project:write` and
   `mergeVariable:write`.
4. **Participants.** `updateProjectParticipants`
   (`PUT /projects/{projectId}/participants`) — a full replacement of the participant set, so
   read `getProjectParticipants` first and send the complete list.
5. **CRM link.** `createOpportunityLink` (`POST /projects/{projectId}/opportunityLink`) ties
   the Project to a CRM opportunity; `listCRMProjects` (`GET /crm/{opportunityID}/projects`)
   resolves the other direction.
6. **Status.** `updateProject` (`PUT /projects/{projectId}`) moves the Project's status. Watch
   for the `project.statusChanged` webhook if you subscribe.

## Rules

- `deleteProject` deletes "a Project and its data" with **no restore operation and no published
  retention window**. Treat it as permanent. If a Project is unwanted, change its status
  instead.
- Async operations expose status but no cancel — once `createProjectFromTemplate` is accepted,
  it runs.
