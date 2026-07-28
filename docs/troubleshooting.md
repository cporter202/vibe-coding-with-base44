# Troubleshooting

> **Reference guide · Find your symptom and work top to bottom**
>
> **Rule:** diagnose with evidence, make one small fix, and rerun the original test.

[← Course map](README.md) · [Prompt Library](../prompts/README.md) · [Base44 official troubleshooting](https://docs.base44.com/Community-and-support/Troubleshooting)

Start with the symptom. Make one diagnosis-driven change, then retest the original flow.

## The first build is too generic

Likely cause: the prompt named a category but not a user, job, screen, or constraints.

Do this:

1. Switch to Discuss mode.
2. Define the primary user and journey.
3. Describe visible layout and visual tone.
4. List version-one exclusions.
5. Refine one page at a time.

Use the [six-part prompt](02-prompt-playbook.md#the-six-part-prompt).

## A prompt changed too much

- Review exactly what changed.
- If the direction is wrong, revert that prompt.
- Reissue a smaller request with explicit scope and protected areas.
- Do not stack several repair prompts onto a change you already know should be reverted.

## Users cannot see their data

Check:

- Whether the user is signed in
- Read permission for the table
- Whether Creator Only matches how the record was created
- Whether an ownership/assignee field exactly matches the user property
- Filters and field types
- Whether the UI is querying the intended table

Test with two users and an admin.

## Users can see other users' data

Treat this as a launch blocker.

1. Restrict app access if real data is exposed.
2. Inspect the affected table's Permissions page.
3. Remove broad Read access that is not intentional.
4. Apply Creator Only or a verified field/user match.
5. Run the security scan.
6. Test cross-user access through both the UI and direct record URLs/IDs.
7. Review whether exposed users need notification or other response under applicable rules.

## Form submissions duplicate

Ask for:

- Submit disabled while saving
- One visible outcome per submission
- Idempotency/duplicate protection for backend or payment actions
- Automation/webhook deduplication
- A test that double-clicks and retries

## Import created duplicate rows

Base44 imports currently append; they do not overwrite. Export a backup, identify the duplicated batch using reliable fields/timestamps, review the deletion set carefully, remove only confirmed duplicates, and retest a sample import.

## Integration stopped working

Inspect:

- OAuth connection status or expired authorization
- Provider status and rate limits
- Base44 function/integration logs
- Secret name and whether it changed
- User role allowed to invoke the action
- Request format changes
- Duplicate or retry behavior

Never paste a real token into chat or an issue.

## Credits disappear too quickly

- Use Plan mode before the first build.
- Use Discuss mode before wide changes.
- Make manual visual changes in Edit mode when practical.
- Combine tightly related edits, not unrelated features.
- Define acceptance criteria so a change does not need repeated clarification.
- Revert bad directions early.
- Use the Free plan to validate fit; upgrade for a required feature or sustained usage.

Check current credit rules in [official billing documentation](https://docs.base44.com/Account-and-billing/Billing-and-plans) and [credits documentation](https://docs.base44.com/Account-and-billing/Credits).

## Preview works but the live app does not

- Confirm the latest version was published.
- Test the live URL in a private window.
- Verify live app visibility and domain settings.
- Confirm environment/integration credentials are configured for the live path.
- Check live logs and network activity.
- If using GitHub sync, confirm changes reached `main`, synced to Base44, and were published.

## Mobile layout is broken

Specify the viewport and observable issue:

```text
At 360px viewport width on [PAGE], [ELEMENT] causes horizontal scrolling and the
primary action is partly off-screen. Keep the desktop layout unchanged. Adjust
the narrow layout so content fits, text wraps, touch targets remain usable, and
the primary action is visible. Test 360px, 768px, and desktop widths.
```

## Still stuck?

Collect a safe reproduction:

- Page and route
- User role
- Exact steps
- Expected versus actual result
- Screenshot with personal data removed
- Safe error/log excerpt
- Approximate time and timezone
- Last relevant change

Then use Base44 support/community links from the [official documentation](https://docs.base44.com/) or open a guide issue if the problem is with this repository.

---

[← Course map](README.md) · [Prompt Library](../prompts/README.md) · [Get guide support](../SUPPORT.md)
