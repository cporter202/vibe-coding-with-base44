# Build your first app: a lead tracker

This build-along creates a small but real product for a solo service business:

- A public page where potential customers submit an inquiry
- A private dashboard where the owner reviews leads
- Status and follow-up tracking
- Safe permissions so visitors cannot read submissions
- A tested, publishable main flow

The point is not the specific business. The same structure works for contact requests, applications, bookings, support tickets, and intake forms.

## What version one includes

### Users

- **Visitor:** can view the public page and submit a lead
- **Admin:** can sign in, view all leads, and update or delete them

### Data

Create one `Lead` table with:

| Field            | Type      | Purpose                                                   |
| ---------------- | --------- | --------------------------------------------------------- |
| `name`           | Text      | Contact name                                              |
| `email`          | Text      | Reply address                                             |
| `phone`          | Text      | Optional phone number; text avoids number-format problems |
| `service`        | Text      | Requested service                                         |
| `message`        | Text      | Details from the visitor                                  |
| `status`         | Text      | New, Contacted, Qualified, Won, or Lost                   |
| `follow_up_at`   | Date/time | Next action date                                          |
| `internal_notes` | Text      | Private admin notes                                       |

Base44 may add system fields such as IDs and timestamps. Do not duplicate them unless you have a specific reason.

## Step 1: plan the app

Choose Plan mode from the initial Base44 prompt and paste:

```text
Plan a responsive lead-tracking app for a solo home-service business.

There are two experiences:
1. A public landing page where a visitor learns about the service and submits
   their name, email, optional phone, requested service, and message.
2. A private admin experience where the business owner signs in, sees leads,
   filters by status, opens a lead, writes internal notes, sets a follow-up date,
   and changes the status to New, Contacted, Qualified, Won, or Lost.

Data safety is essential. Public visitors may create a Lead but must never read,
update, or delete Lead records. Only admins can read, update, or delete leads.
Internal notes must never appear in the public experience.

Version one should not include payments, calendar syncing, SMS, multiple staff
roles, or AI lead scoring.

Use a trustworthy, friendly visual style with excellent mobile layout. Before
building, show me the user flows, pages, Lead schema, permission matrix, and
acceptance criteria. Ask questions where a decision is genuinely missing.
```

Review the plan and then start building.

## Step 2: verify the public journey

Use the preview like a visitor:

1. Open the landing page on a desktop width and a mobile width.
2. Submit a valid inquiry.
3. Confirm the user gets a clear success message.
4. Submit with each required field missing.
5. Double-click the submit button and verify only one record is created.
6. Confirm no admin link or private data is exposed.

If behavior is missing, prompt for the outcome rather than saying “the form is broken”:

```text
Improve the public lead form without changing the page's overall design.

Requirements:
- Validate required fields inline with plain-language messages.
- Validate the email format.
- Disable the submit button while saving to prevent duplicate records.
- After success, clear the form and show the expected response time.
- If saving fails, keep the visitor's entries and show a useful retry message.

Test the valid, invalid, duplicate-click, and failed-save states after making the
change. Tell me what you verified.
```

## Step 3: verify permissions

The permission matrix should be:

| Action on `Lead` | Public visitor | Admin |
| ---------------- | -------------: | ----: |
| Create           |            Yes |   Yes |
| Read             |             No |   Yes |
| Update           |             No |   Yes |
| Delete           |             No |   Yes |

Ask Base44 to confirm it:

```text
Review the Lead entity permissions. Anonymous visitors may create leads but may
not read, update, or delete any Lead. Only users with the Admin role may read,
update, or delete leads. Explain the resulting rule for each CRUD action before
changing anything. Then apply it and tell me how to test it as both a visitor
and an admin.
```

Then inspect **Dashboard → Data → Lead → Permissions**. Never rely only on the chat summary for a sensitive rule.

## Step 4: improve the admin workflow

```text
Improve the admin lead-management workflow.

On the Leads dashboard:
- Show New leads first, then sort each status group by newest first.
- Add filters for status, service, and follow-up date.
- Add a search box for name, email, and phone.
- Make overdue follow-ups visually noticeable without relying on color alone.
- Clicking a lead should open its details, including internal notes.
- After an update, show confirmation and keep the user's current filters.

Only admins can access this page or its data. Preserve the public page.
```

## Step 5: add useful empty and error states

Generated apps often look good when data exists and confusing when it does not.

```text
Add complete states to the admin Leads page:
- loading state,
- no leads yet,
- no results for the current filters,
- permission denied,
- failed to load with a Retry action,
- successful update,
- failed update that preserves unsaved text.

Keep the messages concise and tell the user what to do next.
```

## Step 6: use realistic test data

Add at least:

- Two new leads
- One contacted lead with a future follow-up
- One qualified lead with an overdue follow-up
- One won lead
- One lost lead
- Similar names or emails to test search
- A long message to test layout

Do not use real customer information while experimenting. Base44 provides separate test-data and testing features; use them when available in your account.

## Step 7: test the critical flows

At minimum, test:

1. Visitor submits a valid lead.
2. Invalid form shows useful errors.
3. Visitor cannot access admin data.
4. Admin signs in and sees the submitted lead.
5. Admin changes status and follow-up date.
6. Filters and search find the expected records.
7. Mobile layout remains usable.

If the Testing Agent is available, create browser tests for these flows. It cannot currently test the login process itself, but it can start a test already authenticated. See [Testing and debugging](05-testing-debugging.md).

## Step 8: run the launch checks

Before publishing:

- Run Base44's security scan.
- Resolve every permission warning.
- Confirm no API keys, secrets, or real customer test data are visible.
- Test with an admin and a non-admin account.
- Check privacy/contact language appropriate to your business and location.
- Export important data before any destructive migration.

Continue with the full [launch checklist](06-launch-checklist.md).

## Optional version-two prompts

Add only after version one is stable:

- Email the owner when a new lead arrives
- Daily digest of overdue follow-ups
- Calendar connection for scheduled estimates
- Separate staff roles and lead assignment
- Source tracking and conversion analytics
- Payments or deposits

Each addition changes the data, permissions, cost, or failure surface. Add one, test it, then continue.

Official references: [managing data](https://docs.base44.com/Building-your-app/Managing-your-app-data), [data permissions](https://docs.base44.com/Setting-up-your-app/Managing-security-settings), and [testing flows](https://docs.base44.com/documentation/managing-app-data/testing-agent).
