# Base44 glossary in plain English

> **The words you will see in Base44, translated for beginners**

[← Course map](README.md) · [Quick reference](quick-reference.md) ·
[Start Here](00-start-here.md)

You do not need to memorize these terms. Use this page whenever a lesson, prompt,
or Base44 screen uses a word you do not recognize.

## Building and editing

### Acceptance criteria

Observable statements that prove a feature is finished. “The form shows a
success message and creates exactly one record” is testable; “the form is good”
is not.

### AI chat

The conversation area where you ask Base44 to plan, explain, build, or change
your app.

### Component

A reusable piece of an interface, such as a button, form, card, header, or table.

### Default mode

The AI chat mode that acts on your request and changes the app.

### Discuss mode

A mode for exploring approaches, reviewing logic, and diagnosing problems
without changing the app.

### Edit mode

The visual editing mode where you select interface elements and adjust design
details directly or with AI assistance.

### Page

One screen or route in an app, such as Home, Submit Request, or Admin Dashboard.

### Plan mode

The pre-build conversation for a new app. Base44 asks about the problem, users,
flows, and design, then produces a structured plan you can approve.

### Preview

The interactive view of the app inside the editor. Preview is for testing while
you build; always test the published URL separately.

### Version History

Saved states of the app that you can restore when a change takes the project in
the wrong direction.

## Data and access

### Authentication (auth)

Proving who someone is, usually by signing in.

### Authorization

Deciding what an authenticated person is allowed to see or do. Signing in does
not automatically make every record safe.

### CRUD

Create, Read, Update, and Delete—the four common actions you can permit or deny
for data.

### Entity or table

A collection of one kind of record. A lead tracker might have `Leads`, `Users`,
and `Notes` tables.

### Field

One named value on a record, such as `email`, `status`, or `created_at`.

### Ownership

The relationship that identifies which user or organization controls a record.
Permission rules often use ownership to prevent cross-user access.

### Permission rule

A rule describing who may create, read, update, or delete particular data.

### Record

One saved item in a table—for example, one lead in the `Leads` table.

### Role

A named access category such as visitor, customer, staff, or admin.

### Row-level security

Rules that decide which individual records a person may access, not merely
whether they may open the table.

### Validation

Checks that reject missing, malformed, or unsafe input before it is accepted.

## Logic and integrations

### Automation

A task that runs on a schedule or recurring rule without a person pressing a
button each time.

### Backend function

Code that runs away from the browser. It is appropriate for protected business
logic, secret credentials, webhooks, and trusted calls to outside services.

### Connector

An OAuth-based connection to an outside tool such as Google Workspace, Slack,
or GitHub. The connected account grants specific permissions.

### Idempotent

Safe to repeat without causing duplicate effects. A retryable payment webhook or
email job should not create two orders or send two messages accidentally.

### Integration

A connection between the app and another capability or service. Base44 supports
built-in integrations, connectors, and custom/backend approaches.

### Rate limit

A provider's cap on how many requests may be made during a period. Good
integrations handle this limit and retry carefully.

### Secret

A private credential such as an API key or token. Secrets belong in protected
server-side storage, never in browser code, prompts, screenshots, or Git commits.

### Webhook

An HTTP request sent by another service when something happens—for example, a
payment provider notifying your app that a payment succeeded.

### Workflow

A sequence of steps triggered by an event, such as saving a lead and then
notifying an administrator.

## Testing, publishing, and development

### CLI (command-line interface)

A text-based developer tool used from a terminal. Base44's CLI/backend path is a
developer feature and is distinct from the visual app-editor workflow.

### Custom domain

Your own web address connected to a published app instead of only the provided
Base44 URL. Current plan requirements apply.

### GitHub sync

The app-editor feature for exporting or synchronizing project code with a GitHub
repository. It requires an eligible plan and should be used with a safe branch
and review workflow.

### Logs

Time-stamped technical records that help explain what happened during requests,
functions, integrations, or failures. Remove private data before sharing them.

### Production or live app

The version real users can reach. A feature working in preview does not prove the
published version works.

### Regression

Something that used to work but broke after a change. A regression test confirms
the nearby working behavior remains intact.

### SDK (software development kit)

Code helpers developers use to work with Base44 data, authentication,
integrations, and functions.

### Staging

A separate pre-production environment available under some current plan models.
Use it to test changes before they affect the live app.

### Test case

A specific role, starting state, series of actions, and observable expected
result.

## Still unclear?

Open Base44's [official documentation](https://docs.base44.com/) for product
definitions, or use Discuss mode and ask:

```text
Explain [TERM OR FEATURE] in plain English for a first-time app builder. Give me
one example from my app, one common mistake, and one check that proves I used it
correctly. Do not change the app.
```

---

[← Course map](README.md) · [Quick reference →](quick-reference.md)
