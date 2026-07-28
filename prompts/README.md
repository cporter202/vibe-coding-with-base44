# Base44 prompt library

Replace every `[BRACKETED VALUE]`. Read the prompt before sending it; a copied prompt is only useful when it matches your app.

## Plan a minimum viable app

```text
Help me plan the smallest useful version of [APP IDEA] for [PRIMARY USER]. Their
main job is [JOB], and success means [MEASURABLE/OBSERVABLE RESULT].

Ask questions about the main flow, necessary data, roles and permissions, and
visual direction. Prevent scope creep. Finish with pages, data tables/fields,
permission matrix, acceptance criteria, and a not-now list. Do not build until I
approve the plan.
```

## Turn a messy idea into requirements

```text
Do not build yet. Organize the following notes into confirmed requirements,
assumptions, contradictions, unanswered decisions, and optional ideas:

[PASTE NOTES]

Then ask only the questions whose answers would materially change version one.
```

## Create a data model

```text
Do not change the app. For [WORKFLOW], propose the minimum data model. For each
table show its purpose, fields and types, required/optional status, relationships,
ownership, and who may Create, Read, Update, and Delete. Avoid duplicated facts
and fields we do not need for version one.
```

## Review data permissions

```text
Do not change permissions yet. Audit every table for anonymous visitors, regular
users, and admins. Show a CRUD matrix and flag any path where a user could read
or change someone else's private data. Recommend least-privilege rules and a
cross-user test plan. Wait for approval before applying changes.
```

## Public form, private records

```text
Configure [TABLE] so anonymous visitors may Create a record but may never Read,
Update, or Delete records. Only admins may Read, Update, or Delete them. Keep
internal-only fields out of every public response and page. Show the exact CRUD
matrix and test it as a visitor and admin.
```

## User-owned records

```text
For [TABLE], require sign-in and let each user Create records and Read, Update,
or Delete only records they own. Admin access should be explicit. Explain which
field/rule establishes ownership and test with User A, User B, and Admin.
```

## Improve a form

```text
Improve [FORM] on [PAGE] without changing the overall design.

- Label required and optional fields clearly.
- Validate [RULES] inline.
- Preserve entries after a failed save.
- Disable repeated submission while saving.
- Show clear loading, success, and retryable error states.
- Make keyboard and mobile use comfortable.

Done means [HAPPY-PATH TEST], [INVALID TEST], and [DUPLICATE-CLICK TEST] pass.
```

## Build a dashboard

```text
Create a [PURPOSE] dashboard for [ROLE]. Show [KEY METRICS] first, followed by
[LIST/CHART]. Add filters for [FIELDS] and search across [FIELDS]. Define loading,
empty, no-results, permission-denied, and failure states. Every number must come
from real app data, use a consistent time range, and link to the records behind it.
```

## Add role-based navigation

```text
Adjust navigation so [ROLE A] sees [ITEMS] and [ROLE B] sees [ITEMS]. Hiding a
link is not authorization: enforce the same rules on routes and underlying data.
Direct navigation to a forbidden route must not reveal its content or records.
Test signed out, Role A, and Role B.
```

## Add search and filters

```text
On [PAGE], add search across [FIELDS] and filters for [FIELDS]. Search should be
case-insensitive, filters should combine predictably, Clear should reset all
controls, and no-results should differ from no-data. Preserve filter state after
opening and updating a record. Do not load more records than the page needs.
```

## Add email safely

```text
When [TRIGGER], send [RECIPIENT] an email containing [SAFE CONTENT]. Do not send
[PRIVATE CONTENT]. If delivery fails, keep the underlying record, log a safe
failure, and provide [ROLE] a retry path. Prevent duplicates when the trigger or
retry runs twice. Test success, failure, and repeated trigger.
```

## Add an external API

```text
Connect [FEATURE] to [PROVIDER]. First explain whether a built-in integration,
connector, custom integration, or backend function is the simplest safe option.

Keep credentials in Secrets and never expose them to the browser. Validate input
server-side, authorize [ROLE], handle timeouts/rate limits/provider errors, make
retries idempotent, and log only safe metadata. Show the request flow and tests
before implementation.
```

## Add a scheduled automation

```text
At [TIME] in [TIMEZONE] on [SCHEDULE], find [QUALIFYING RECORDS] and [ACTION].
Handle no matching records without unnecessary notifications. Make duplicate
runs safe. Update the record only after the external action succeeds, and log
counts/outcomes without sensitive content. Add a manual test mode.
```

## Prepare a payment feature

```text
Do not implement yet. Plan [ONE-TIME/SUBSCRIPTION] payments for [PRODUCT]. Cover
provider/region support, test mode, server-side confirmation, duplicate events,
success/failure/cancellation, access grant and revocation, receipts, refunds,
disputes, permissions, and reconciliation. List unresolved business/legal
decisions and current Base44 plan/integration requirements.
```

## Diagnose a bug

```text
Do not change the app yet.

Page: [PAGE]
Role: [ROLE]
Starting state: [STATE]
Action: [ACTION]
Expected: [EXPECTED]
Actual: [ACTUAL]
Error/log excerpt: [REDACTED DETAILS]
Frequency: [FREQUENCY]
Recent relevant change: [CHANGE]

Rank likely causes by evidence, tell me what would confirm each, and propose the
smallest fix plus a regression test.
```

## Fix without collateral changes

```text
Fix [SPECIFIC PROBLEM] on [PAGE/FLOW]. Preserve [WORKING BEHAVIOR], [DATA MODEL],
[PERMISSIONS], and [VISUAL AREA]. Do not refactor unrelated code. Done means
[ORIGINAL FAILURE] no longer occurs and [REGRESSION TESTS] still pass.
```

## Add complete UI states

```text
For [FEATURE], add distinct loading, empty, no-results, success, validation,
permission-denied, offline/failed-request, and retry states where relevant.
Preserve user input on recoverable failure. Each message should explain what
happened and the next available action.
```

## Mobile review

```text
Review [PAGE/FLOW] at 360px, 768px, and desktop widths. Fix horizontal overflow,
crowded touch targets, unreadable text, hidden actions, awkward tables, and
content that relies on hover. Preserve the desktop hierarchy. Report what you
tested rather than saying only that it is responsive.
```

## Accessibility review

```text
Review [FLOW] for keyboard navigation, visible focus, semantic headings, form
labels, error association, contrast, image alternatives, reduced motion, and
meaning conveyed only by color. Fix launch-blocking issues without redesigning
the brand. Provide a keyboard-only test script.
```

## Performance review

```text
Do not optimize blindly. Inspect [SLOW PAGE/FLOW] and identify measured or
observable bottlenecks: excessive records, repeated requests, large media,
unnecessary rerenders, or slow integrations. Rank fixes by user impact and risk.
Implement the smallest high-impact fix and compare before/after behavior.
```

## Launch review

```text
Do not change the app. Audit launch readiness for [TARGET USER] completing
[PRIMARY FLOW]. Review product gaps, mobile/accessibility, permissions, secrets,
data recovery, integrations, duplicate actions, analytics, privacy touchpoints,
and support. Return blockers, important improvements, optional polish, and a
role-by-role manual test script.
```

## Create tests

```text
Create end-to-end test scenarios for [FLOW]. Include one happy path, validation
failures, duplicate action, service failure/retry, permission denial, and a
cross-user data-access test. Each scenario must state starting data, role, steps,
and observable results. Do not claim a test passed unless it actually ran.
```

## Explain the existing app

```text
Do not change anything. Explain how [FEATURE] currently works from user action to
stored data and side effects. Name the pages, components, tables, permissions,
functions, integrations, and automations involved. Separate confirmed behavior
from assumptions and point out the safest places to make [DESIRED CHANGE].
```

## Reduce scope

```text
This plan is too large for version one. Reduce it to the smallest release that
lets [PRIMARY USER] complete [PRIMARY JOB] and lets us measure [SUCCESS SIGNAL].
Keep only essential pages, tables, and integrations. Put everything else into a
ranked not-now list and explain which risks the smaller scope removes.
```

Return to the [prompt playbook](../docs/02-prompt-playbook.md) to learn when and why to use each pattern.
