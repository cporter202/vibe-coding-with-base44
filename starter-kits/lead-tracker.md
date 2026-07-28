# Starter kit: lead tracker

> **Beginner · 45–60 minutes · Public submission, private administration**

[← All starter kits](README.md) ·
[Full build-along](../docs/01-build-your-first-app.md) ·
[Permission lesson](../docs/03-data-auth-security.md)

## The outcome

A prospective customer submits an inquiry. The business owner sees it in a
private dashboard, assigns a status, and records the next follow-up action.

Success means a visitor can submit exactly one valid lead without seeing any
lead records, while an admin can review and update every submission.

## Version-one boundary

**Include:**

- Public landing page and inquiry form
- Private admin dashboard
- Lead status and next-follow-up date
- Search or filtering by status
- Clear loading, success, validation, empty, and failure states

**Not yet:**

- Automated email sequences
- Calendar sync
- SMS
- Payments
- Multiple sales teams or organizations
- AI lead scoring

## Plan mode prompt

```text
Plan the smallest useful lead tracker for [BUSINESS TYPE]. It has two audiences:
anonymous prospective customers and one business administrator.

The visitor must be able to open a public page and submit name, email, optional
phone, service interest, and a short message. The visitor must never be able to
read, search, update, or delete any lead record.

The administrator must sign in to a private dashboard, view leads, filter by
status, open a lead, set status to New, Contacted, Qualified, Won, or Lost, and
record a next-follow-up date and private notes.

Keep version one intentionally small. Do not add email automation, calendar
sync, payments, multiple organizations, or AI scoring. Ask questions that would
materially change the workflow, then return pages, tables and fields, a CRUD
permission matrix, build stages, acceptance criteria, and a not-now list. Do not
build until I approve the plan.
```

## Minimum data model

### `Leads`

| Field            | Type       | Required | Notes                                      |
| ---------------- | ---------- | :------: | ------------------------------------------ |
| `name`           | Text       |   Yes    | Person submitting                          |
| `email`          | Email/text |   Yes    | Validate format                            |
| `phone`          | Text       |    No    | Do not assume a national format            |
| `service`        | Text       |   Yes    | Use a short controlled list if appropriate |
| `message`        | Long text  |   Yes    | Apply a sensible length limit              |
| `status`         | Text       |   Yes    | Default to `New`                           |
| `next_follow_up` | Date       |    No    | Admin-managed                              |
| `private_notes`  | Long text  |    No    | Admin-only                                 |
| `created_at`     | Date/time  |   Yes    | System-managed                             |

Do not place `status`, `private_notes`, or `next_follow_up` in the public form.

## Permission matrix

| Role                | Create | Read | Update | Delete |
| ------------------- | :----: | :--: | :----: | :----: |
| Anonymous visitor   |  Yes   |  No  |   No   |   No   |
| Signed-in non-admin |   No   |  No  |   No   |   No   |
| Admin               |  Yes   | Yes  |  Yes   |  Yes   |

Verify the actual Base44 data rules; hiding the dashboard is not enough.

## Five-stage build order

1. **Public form:** fields, inline validation, save behavior, and success state.
2. **Data protection:** apply the permission matrix before adding admin screens.
3. **Admin list:** show newest first, status, service, and follow-up date.
4. **Admin detail:** status, notes, and next follow-up with clear save feedback.
5. **Polish and test:** mobile layout, empty state, filters, failure behavior, and
   security scan.

Build and test each stage separately.

## Acceptance tests

| Test                  | Steps                                                             | Expected result                                     |
| --------------------- | ----------------------------------------------------------------- | --------------------------------------------------- |
| Valid submission      | Submit all required fields once                                   | One record is saved and success is clear            |
| Missing required data | Remove email or message and submit                                | Nothing saves; the exact field explains the problem |
| Double click          | Click submit repeatedly while saving                              | Only one lead is created                            |
| Visitor privacy       | Try to navigate to or query lead data while signed out            | No lead or private field is exposed                 |
| Non-admin privacy     | Sign in as a normal user and try the admin route                  | Access is denied and no records are revealed        |
| Admin update          | Change status and follow-up date, reload, and reopen              | The saved values remain                             |
| Failure recovery      | Simulate or observe a failed save                                 | Input remains and a useful retry action appears     |
| Published app         | Repeat the main tests on the live URL in a private browser window | Live behavior matches the tested preview            |

## Definition of done

- [ ] All eight acceptance tests pass.
- [ ] The security scan has no unexplained finding.
- [ ] The public response never includes admin-only fields.
- [ ] The form works comfortably at a 360px-wide mobile viewport.
- [ ] A person unfamiliar with the project can submit without instructions.
- [ ] The administrator can identify the next action for every active lead.

## Version-two upgrade triggers

Add a feature only when real use creates the need:

- **Email notification:** the owner misses new submissions.
- **Calendar integration:** follow-ups are regularly forgotten.
- **Assignment:** more than one person handles leads.
- **Duplicate detection:** repeated contacts make the list unreliable.
- **Analytics:** enough leads exist for conversion trends to guide decisions.
- **CRM sync:** this app is no longer the system where the team works.

Every integration adds credentials, failure modes, and possibly plan
requirements. Recheck the official Base44 plan and integration documentation
before implementing it.

---

[← All starter kits](README.md) ·
[Continue with the full build-along →](../docs/01-build-your-first-app.md)
