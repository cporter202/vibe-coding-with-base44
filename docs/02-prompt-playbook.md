# Prompt playbook

Good vibe coding is not about discovering a magic sentence. It is about giving the builder enough context, limiting the blast radius, and defining evidence that a change is complete.

## The six-part prompt

Use this structure for meaningful changes:

```text
CONTEXT
This app is for [USER] who needs to [JOB].

OUTCOME
When [TRIGGER], the app should [OBSERVABLE RESULT].

SCOPE
Change [PAGES / COMPONENTS / DATA]. Keep [PROTECTED AREAS] unchanged.

RULES
- [BUSINESS RULE]
- [PERMISSION RULE]
- [EDGE CASE]

EXPERIENCE
Show [LOADING / EMPTY / SUCCESS / ERROR] states. On mobile, [REQUIREMENT].

DONE WHEN
- [TESTABLE ACCEPTANCE CRITERION]
- [TESTABLE ACCEPTANCE CRITERION]
- [NEGATIVE TEST: WHAT MUST NEVER HAPPEN]
```

Not every edit needs all six sections. A button-label change can be one sentence. Use more structure as the risk and scope increase.

## Describe behavior, not implementation

As a beginner, you usually get better results by describing the user-visible contract:

Weak:

```text
Use a hook to fix the form state.
```

Better:

```text
If submission fails, keep everything the visitor typed, explain what happened,
and let them retry. Prevent duplicate submissions while the request is saving.
```

Implementation details are useful when you know a project constraint. Otherwise, let the builder propose them and judge the behavior.

## One outcome per prompt

Large batches make it hard to know which request caused a regression. Prefer this sequence:

1. Add the data and permissions.
2. Add the simplest interface for the happy path.
3. Add validation and failure states.
4. Add filters or secondary workflows.
5. Polish visuals.
6. Test and fix.

This is usually more credit-efficient than repeatedly rebuilding a broad feature that was not clearly specified.

## Tell Base44 what not to change

Generated changes can be wider than expected. Add guardrails:

```text
Keep the existing navigation, authentication flow, data field names, and mobile
layout unchanged. Do not add packages or create a second table for the same data.
```

Only protect things you truly care about. A giant “do not change” list can prevent the correct fix.

## Use acceptance criteria

Replace subjective completion language with observations.

| Vague                 | Testable                                                                                                                                       |
| --------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| Make it user friendly | A first-time visitor can submit without an account, required fields explain errors inline, and keyboard focus moves to the first invalid field |
| Make it responsive    | At 360px width, no horizontal scrolling appears and the primary action remains visible and tappable                                            |
| Secure the dashboard  | Anonymous users and regular users cannot load the page or query its records; admins can read and update them                                   |
| Fix search            | Search ignores letter case, matches name and email, handles no results, and clears without reloading the page                                  |
| Make it fast          | Do not fetch the full table when only the newest 20 rows are displayed; show a loading state while data is requested                           |

## Include unhappy paths

For each feature, ask what happens when:

- The list is empty
- Data is still loading
- The request fails
- The user is unauthorized
- The input is invalid
- The user clicks twice
- The result is very long
- The device is narrow
- The network is slow

You do not need all of them every time. Pick the ones that could harm the user or corrupt data.

## Ask for an explanation before a risky change

Switch to Discuss mode and use:

```text
Do not change the app. Explain how [FEATURE] currently works, which pages,
entities, permissions, functions, and integrations it touches, and the safest
small change to achieve [OUTCOME]. Identify data-migration or security risks and
give me a test plan. Ask me to confirm unresolved product decisions.
```

Then switch back to Default mode for implementation.

## Debug with evidence

“It doesn't work” forces the AI to guess. Provide:

- Page and user role
- Exact action
- Expected result
- Actual result
- Error message
- Whether it happens every time
- Recent change that preceded it
- Relevant log or activity details, with secrets removed

Debugging template:

```text
On [PAGE], signed in as [ROLE], I [ACTION].

Expected: [RESULT]
Actual: [RESULT]
Message/log: [SAFE EXCERPT]
Frequency: [ALWAYS / SOMETIMES / ONCE]
Last known working state: [DETAIL]

First diagnose the most likely cause without changing the app. Tell me what
evidence supports it and the smallest safe fix. Then propose a regression test.
```

## Correct course without starting over

If a change missed the mark:

```text
The last change achieved [WHAT WORKED], but it also caused [REGRESSION]. Keep the
working part. Restore [BROKEN BEHAVIOR] to [EXPECTED STATE] without changing
[PROTECTED AREA]. Done means [TESTS].
```

If the change is too tangled, use the Revert control for the prompt and try a smaller request. Reverting early is often cheaper than stacking repair prompts onto a bad direction.

## Prompt smells

Rewrite a prompt when it includes:

- “Make it better” with no audience or outcome
- “Like [famous app]” with no explanation of which characteristic
- Ten unrelated features
- A request to “make it secure” without roles and rules
- A payment flow with no failure/refund/access behavior
- A destructive data request with no backup or mapping
- A visual overhaul mixed with a database migration
- “Fix everything”

## A reusable review prompt

```text
Do not change the app yet. Review [FLOW] from the perspective of [USER].

Evaluate:
- whether the user can complete the intended job,
- missing loading, empty, success, and error states,
- accessibility and mobile usability,
- data integrity and duplicate-action risks,
- authentication and authorization,
- privacy or secret-exposure risks,
- the three highest-value improvements.

Separate confirmed observations from assumptions. Give me a prioritized plan,
then wait for me to choose what to implement.
```

For copy-ready examples, visit the [prompt library](../prompts/README.md).

Official reference: [Writing effective prompts in Base44](https://docs.base44.com/Getting-Started/Prompt-guide).
