# Starter kit: booking request manager

> **Beginner-plus · 60–90 minutes · Request and confirmation workflow**

[← All starter kits](README.md) ·
[Integration lesson](../docs/04-integrations-workflows.md) ·
[Launch checklist](../docs/06-launch-checklist.md)

## The outcome

A visitor requests an appointment from offered time windows. An administrator
reviews the request and confirms or declines it. This version deliberately does
not promise real-time calendar availability.

Success means a visitor understands that they submitted a request—not a
guaranteed appointment—and the administrator can prevent two confirmations for
the same time window.

## Version-one boundary

**Include:**

- Public service and booking-request page
- Admin-managed offered time windows
- Visitor contact details and requested service
- Pending, confirmed, and declined statuses
- Private admin review screen
- Clear confirmation language and duplicate safeguards

**Not yet:**

- Google or Outlook calendar sync
- Payments or deposits
- Recurring appointments
- Staff assignment
- Time-zone conversion
- Automated SMS or email reminders

## Plan mode prompt

```text
Plan a booking request manager for [BUSINESS TYPE]. Anonymous visitors can view
offered time windows and request one by entering name, email, optional phone,
service, and optional notes. Submitting creates a Pending request; it must never
claim the appointment is confirmed.

One Admin signs in to manage offered time windows, review requests, and mark each
request Confirmed or Declined. The app must prevent the Admin from confirming two
active bookings for the same time window. Visitors must never read booking or
contact records.

Keep version one intentionally small. Do not add calendar sync, payments,
reminders, recurring bookings, multiple staff, or automatic time-zone handling.
Ask questions that materially change the workflow, then return pages, minimum
entities and fields, relationships, a CRUD matrix, conflict rules, build stages,
acceptance tests, and a not-now list. Do not build until I approve the plan.
```

## Minimum data model

### `TimeSlots`

| Field        | Type      | Required | Notes                                |
| ------------ | --------- | :------: | ------------------------------------ |
| `starts_at`  | Date/time |   Yes    | Store consistently                   |
| `ends_at`    | Date/time |   Yes    | Must be later than start             |
| `is_offered` | Boolean   |   Yes    | Admin can remove from public choices |
| `label`      | Text      |    No    | Optional client-facing description   |

### `BookingRequests`

| Field         | Type                | Required | Notes                                      |
| ------------- | ------------------- | :------: | ------------------------------------------ |
| `slot_id`     | Time slot reference |   Yes    | Requested window                           |
| `name`        | Text                |   Yes    | Visitor                                    |
| `email`       | Email/text          |   Yes    | Validate format                            |
| `phone`       | Text                |    No    | Optional                                   |
| `service`     | Text                |   Yes    | Controlled list when appropriate           |
| `notes`       | Long text           |    No    | Length-limit and keep out of public output |
| `status`      | Text                |   Yes    | `Pending`, `Confirmed`, or `Declined`      |
| `admin_notes` | Long text           |    No    | Admin-only                                 |
| `created_at`  | Date/time           |   Yes    | System-managed                             |

## Permission matrix

| Entity          | Visitor Create | Visitor Read | Visitor Update | Visitor Delete | Admin |
| --------------- | :------------: | :----------: | :------------: | :------------: | :---: |
| TimeSlots       |       No       | Offered only |       No       |       No       | Full  |
| BookingRequests |      Yes       |      No      |       No       |       No       | Full  |

Return only the minimum safe success response after a visitor submits. Never
expose the request list, contact details, internal status history, or admin notes.

## Five-stage build order

1. **Admin time slots:** create, edit, and hide offered windows.
2. **Public request flow:** show offered windows and validate visitor input.
3. **Private admin queue:** newest pending requests first.
4. **Conflict guard:** prevent two confirmed requests for one slot.
5. **Language and testing:** clearly distinguish requested from confirmed.

## Acceptance tests

| Test                        | Expected result                                             |
| --------------------------- | ----------------------------------------------------------- |
| Valid request               | One Pending record and an accurate “request received” state |
| Missing or invalid input    | No record; exact fields explain the correction              |
| Repeated submit             | No accidental duplicate request                             |
| Hidden time slot            | Not offered publicly and cannot receive a normal request    |
| Two requests for one slot   | Both may remain Pending; only one can become Confirmed      |
| Second confirmation attempt | Blocked with a clear admin explanation                      |
| Visitor direct-data attempt | No booking/contact record or internal field is exposed      |
| Declined request            | Slot behavior matches the approved business rule            |
| Published mobile flow       | Selection and submission work on a narrow screen            |

## Definition of done

- [ ] The interface never labels Pending as Confirmed.
- [ ] The conflict rule is enforced when status changes, not only visually.
- [ ] Visitors cannot read any request records.
- [ ] Date and time labels include a clear business time zone.
- [ ] All acceptance tests pass on the published URL.
- [ ] The security scan has been reviewed.

## Version-two upgrade triggers

- **Calendar connector:** manual schedule updates create repeated conflicts.
- **Email or SMS:** confirmed customers miss appointments without reminders.
- **Deposits:** no-shows justify the operational and legal complexity.
- **Staff assignment:** more than one provider offers independent availability.
- **Time-zone support:** customers actually book from multiple time zones.

Before adding calendar, messaging, or payments, document what happens on provider
failure, retry, cancellation, duplicate events, and exhausted credits. Verify the
current Base44 plan and integration requirements.

---

[← All starter kits](README.md) ·
[Plan integrations safely →](../docs/04-integrations-workflows.md)
