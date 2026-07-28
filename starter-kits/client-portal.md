# Starter kit: client portal

> **Beginner-plus · 60–90 minutes · Signed-in, user-owned records**

[← All starter kits](README.md) ·
[Permission lesson](../docs/03-data-auth-security.md) ·
[Testing lesson](../docs/05-testing-debugging.md)

## The outcome

A client signs in, sees only their own projects and requests, and submits a new
request. An administrator sees all clients, projects, and requests and updates
their status.

Success means Client A can never discover Client B's records—even by using a
direct URL—while the administrator can manage the complete workflow.

## Version-one boundary

**Include:**

- Sign-in
- Client dashboard with owned projects and requests
- New-request form
- Admin dashboard with all requests
- Status updates and admin response
- Empty, loading, permission-denied, and failure states

**Not yet:**

- File uploads containing sensitive information
- Payments or invoices
- Live chat
- Email or Slack notifications
- Multiple staff permission levels
- Multi-company tenancy

## Plan mode prompt

```text
Plan a small client portal for [SERVICE BUSINESS]. There are two signed-in roles:
Client and Admin.

Each Client should see only their own profile, projects, and requests. They can
open a project, view its title/status/summary, submit a request connected to that
project, and view the status and admin response for their own requests.

Admins can see every client, project, and request; create or update projects;
and update request status and the admin response. Direct URLs, search, and data
queries must enforce the same ownership rules as the interface.

Keep version one small. Do not add payments, invoices, file uploads, chat,
notifications, multiple companies, or extra staff roles. Ask questions that
would materially change version one, then return pages, minimum entities and
relationships, an ownership-based CRUD matrix, build stages, cross-user tests,
acceptance criteria, and a not-now list. Do not build until I approve the plan.
```

## Minimum data model

### `ClientProfiles`

| Field     | Type           | Required | Notes                         |
| --------- | -------------- | :------: | ----------------------------- |
| `user_id` | User reference |   Yes    | Establishes profile ownership |
| `name`    | Text           |   Yes    | Display name                  |
| `company` | Text           |    No    | Optional business name        |

### `Projects`

| Field       | Type                     | Required | Notes                      |
| ----------- | ------------------------ | :------: | -------------------------- |
| `client_id` | Client profile reference |   Yes    | Establishes project owner  |
| `title`     | Text                     |   Yes    | Short project name         |
| `summary`   | Long text                |   Yes    | Safe client-facing summary |
| `status`    | Text                     |   Yes    | Controlled values          |

### `Requests`

| Field            | Type              | Required | Notes                              |
| ---------------- | ----------------- | :------: | ---------------------------------- |
| `project_id`     | Project reference |   Yes    | Connects request to owned project  |
| `client_id`      | Client reference  |   Yes    | Supports explicit ownership checks |
| `subject`        | Text              |   Yes    | Short summary                      |
| `details`        | Long text         |   Yes    | Apply a sensible length limit      |
| `status`         | Text              |   Yes    | Defaults to `Submitted`            |
| `admin_response` | Long text         |    No    | Admin-managed, client-readable     |
| `created_at`     | Date/time         |   Yes    | System-managed                     |

Avoid duplicating user emails across tables unless the workflow requires a
historical snapshot.

## Permission matrix

| Entity         | Client Create | Client Read       | Client Update | Client Delete | Admin |
| -------------- | :-----------: | ----------------- | :-----------: | :-----------: | :---: |
| ClientProfiles |      No       | Own profile only  |      No       |      No       | Full  |
| Projects       |      No       | Own projects only |      No       |      No       | Full  |
| Requests       |      Yes      | Own requests only |      No       |      No       | Full  |

If clients need editing or cancellation later, define a narrow rule based on
status and ownership instead of granting general update/delete access.

## Five-stage build order

1. **Identity and ownership:** sign-in, client profile, roles, and relationships.
2. **Read-only client dashboard:** projects and requests filtered by ownership.
3. **Request submission:** allow clients to create only for their own project.
4. **Admin workflow:** global list, filters, status, and admin response.
5. **Adversarial testing:** Client A, Client B, Admin, signed out, and direct URLs.

## Acceptance tests

| Role       | Test                                         | Expected result                                      |
| ---------- | -------------------------------------------- | ---------------------------------------------------- |
| Signed out | Open a client or admin URL                   | Redirected or denied; no private data appears        |
| Client A   | Open own project and requests                | Only Client A data appears                           |
| Client A   | Change a URL or search for Client B's record | Denied with no private fields revealed               |
| Client A   | Submit a request for Client B's project ID   | Rejected; no record is created                       |
| Client B   | Search, filter, and navigate normally        | Only Client B data appears                           |
| Admin      | View and update requests from both clients   | Updates persist and appear to the correct client     |
| Any client | Submit twice rapidly                         | One request or an explicit duplicate-safe outcome    |
| Any role   | Encounter an unavailable request             | Safe error; no other record or internal detail leaks |

## Definition of done

- [ ] Every cross-user test passes in preview and on the live URL.
- [ ] Ownership is enforced at the data layer, not only by filtering the page.
- [ ] Admin-only fields cannot be changed by clients.
- [ ] Empty and permission-denied states are visibly different.
- [ ] The security scan has been reviewed.
- [ ] Test data contains no real confidential client information.

## Version-two upgrade triggers

- **File uploads:** clients genuinely exchange files and retention rules exist.
- **Notifications:** users miss status changes without them.
- **Payments:** the service, refund, and reconciliation rules are decided first.
- **Multiple staff roles:** real responsibilities require narrower access.
- **Organization tenancy:** multiple businesses—not merely multiple clients—use
  the same product.

The risk rises sharply with files, payments, and multi-tenant access. Revisit the
data model, permission matrix, privacy obligations, and plan requirements before
adding them.

---

[← All starter kits](README.md) · [Review data security →](../docs/03-data-auth-security.md)
