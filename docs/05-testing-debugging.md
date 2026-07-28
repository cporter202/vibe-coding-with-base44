# Testing and debugging

> **Lesson 6 of 7 · 20 minutes · Essential**
>
> **Outcome:** role-based test scenarios and a diagnosis-first debugging loop.

[← Integrations](04-integrations-workflows.md) · [Course map](README.md) · [Next: Launch →](06-launch-checklist.md)

“The AI said it works” is not a test. A test has a starting state, an action, and an observable result.

## Test in layers

### 1. Smoke test

Check that pages load, navigation works, the main action is visible, and no obvious error appears.

### 2. Happy path

Complete the primary journey with valid data from start to finish.

### 3. Validation and edge cases

Try missing fields, wrong formats, long content, double clicks, no results, and slow or failed requests.

### 4. Role and permission tests

Repeat relevant actions as:

- Signed-out visitor
- Regular user A
- Regular user B
- Admin

User A must not be able to load User B's private records—even by changing a URL or record ID.

### 5. Device and accessibility checks

Use narrow mobile and desktop widths. Navigate with a keyboard. Confirm focus visibility, labels, readable contrast, useful error text, and no color-only meaning.

## Write test scenarios in plain language

```text
Test name: Visitor submits a valid request

Given the public Request Service page is open
And no user is signed in
When the visitor enters valid required information
And submits once
Then exactly one Lead record is created
And the visitor sees the response-time confirmation
And the form clears
And no private Lead data is displayed
```

Negative test:

```text
Test name: Visitor cannot read lead submissions

Given at least one Lead exists
And no user is signed in
When the visitor attempts to open the admin route or request a Lead by ID
Then no Lead fields are returned
And the visitor is redirected or shown an access-denied state
And the attempt does not modify data
```

## Base44 Testing Agent

Base44 documents a browser-based Testing Agent that can generate or run end-to-end scenarios in a separate environment. It is currently rolling out, so it may not appear in every account. Current docs say it is available on all plans but uses credits.

Use it for flows such as:

- Submit a form
- Navigate and filter
- Add an item to a cart and check out in test mode
- Update a record
- Verify a role-specific workflow after the agent is authenticated

Current documented limitation: it can begin signed in, but cannot test the login process itself, including OTP or email-verification steps. Test those manually.

## Debugging order

When something fails, do not randomly reprompt. Narrow the layer:

1. **Reproduce:** Can you make it happen reliably?
2. **Scope:** Which page, user role, record, and device?
3. **Observe:** What exact message and state do you see?
4. **Inspect activity/logs:** Did the request run? Was it denied? Did a function or integration fail?
5. **Compare permissions:** Can the role perform the requested data action?
6. **Find the recent change:** What last touched this flow?
7. **Propose one cause:** Ask for evidence, not a broad rewrite.
8. **Make the smallest fix:** Preserve unrelated behavior.
9. **Add a regression test:** Prove the bug stays fixed.

## Diagnostic prompt

```text
Do not modify the app yet.

Problem:
- Page: [PAGE]
- Role: [ROLE]
- Starting data: [STATE]
- Action: [ACTION]
- Expected: [EXPECTED]
- Actual: [ACTUAL]
- Visible error: [MESSAGE]
- Reproduction rate: [RATE]
- Last relevant change: [CHANGE]

Inspect the request/activity path, data rules, and relevant logs. Give me the
three most likely causes ranked by evidence, what would confirm each one, and the
smallest safe fix for the top cause. Do not expose secrets in your response.
```

## Frequent causes

| Symptom                       | Likely place to inspect                                          |
| ----------------------------- | ---------------------------------------------------------------- |
| Data exists but list is empty | Filters, field names/types, permissions, current user ownership  |
| Save button does nothing      | Validation, loading state, click handler, permission denial      |
| Duplicate records             | Double submission, retry behavior, repeated automation/webhook   |
| Works as admin only           | User CRUD rules, ownership field, route guard                    |
| Integration suddenly fails    | Expired OAuth, secret, rate limit, provider status, function log |
| Import created duplicates     | Imports append instead of overwriting                            |
| UI broke after a broad prompt | Revert and split the change into smaller outcomes                |
| Old value returns             | Competing state sources, failed save, stale query/cache          |

## Definition of done

A feature is done when:

- The happy path passes
- Important invalid and failure paths pass
- Role/permission tests pass
- Mobile and keyboard use are acceptable
- Logs contain enough safe detail to diagnose failure
- The acceptance criteria are observable
- A regression test exists for any bug fixed

Official references: [Testing Agent](https://docs.base44.com/documentation/managing-app-data/testing-agent), [test data](https://docs.base44.com/documentation/managing-app-data/testing-your-data), [app logs](https://docs.base44.com/Building-your-app/exploring-app-logs), and [Activity Monitor](https://docs.base44.com/developers/app-code/editor/activity-monitor).

---

[← Integrations](04-integrations-workflows.md) · [Course map](README.md) · [Next: Launch →](06-launch-checklist.md)
