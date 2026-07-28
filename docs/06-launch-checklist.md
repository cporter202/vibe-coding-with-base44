# Launch checklist

> **Lesson 7 of 7 · 20 minutes · Essential**
>
> **Outcome:** a responsibly tested release and a first-week operating plan.

[← Testing](05-testing-debugging.md) · [Course map](README.md) · [Bonus: Developer Path →](07-developer-path.md)

Publishing is easy. Launching responsibly means verifying that the app is useful, safe, understandable, and recoverable.

## Before you invite anyone

### Product

- [ ] One target user and primary job are clear
- [ ] The main journey works from start to finish
- [ ] Navigation labels make sense to a first-time user
- [ ] Empty states explain what to do next
- [ ] Errors preserve user work and suggest recovery
- [ ] Demo/sample content is clearly labeled or removed
- [ ] Support/contact path exists

### Data and security

- [ ] App visibility is intentional: public, workspace, or private
- [ ] Login and registration settings match the product
- [ ] CRUD permissions were reviewed for every table
- [ ] Different roles were tested with separate accounts
- [ ] User A cannot see User B's private records
- [ ] Public forms allow Create without exposing Read
- [ ] Admin routes and underlying data are protected
- [ ] Secrets are stored in Base44 Secrets, not frontend code
- [ ] Base44 security scan was run and findings resolved
- [ ] Test data contains no real sensitive information

### Reliability

- [ ] Main happy-path tests pass
- [ ] Validation, failure, and retry states pass
- [ ] Double-clicks do not create duplicate side effects
- [ ] Integrations handle expired authorization and provider failure
- [ ] Automations are safe if triggered twice
- [ ] Important data has an export/backup plan
- [ ] Logs reveal outcomes without leaking secrets or personal data

### Experience

- [ ] Usable at narrow mobile and desktop widths
- [ ] No horizontal scrolling on common mobile widths
- [ ] Keyboard navigation and visible focus work
- [ ] Form fields have labels and useful errors
- [ ] Color contrast is readable
- [ ] Meaning is not conveyed only by color
- [ ] Loading states prevent confusing repeated actions

### Business and legal

- [ ] Pricing and product promises are accurate
- [ ] Privacy notice matches the data actually collected
- [ ] Terms/refund/cancellation language fits the product
- [ ] Cookie/analytics consent is handled where required
- [ ] Email/SMS workflows have appropriate consent and opt-out behavior
- [ ] Payment flow uses test mode before live money
- [ ] You have rights to all text, images, logos, and imported designs

This guide is educational, not legal advice. Rules depend on users, location, industry, and data.

## Run a small beta

Invite 3–10 people who resemble the target user. Give them a goal, not instructions:

> “Submit a request and then find out what happens next.”

Observe where they hesitate. Ask:

- What did you expect to happen?
- What was confusing?
- What would stop you from using this again?
- What did you think the app was for?

Fix blockers before adding features. A new feature rarely solves unclear navigation or broken trust.

## Publish and verify again

After publishing, use the live URL in a private/incognito browser and on a phone. Verify:

1. Public visibility and login behavior
2. Primary user journey
3. Email or integration delivery
4. Role restrictions
5. Metadata/title and social sharing appearance
6. Custom domain and HTTPS, if used
7. Analytics events that matter

Publishing a Base44 change makes it live; it does not prove the deployed experience matches preview.

## First-week operating rhythm

- Review errors and failed integrations daily
- Check new records for data quality and duplicates
- Respond to user confusion personally
- Track completion of the main journey, not vanity traffic
- Keep a short backlog ranked by user impact
- Export important data before major schema changes
- Publish small changes and retest the affected flow

## Sensible launch metrics

Choose a small set:

- Visitors who start the main flow
- People who complete it
- Time to complete
- Validation or error rate
- Return usage relevant to the product
- Support requests by category
- Integration/function failure rate

Do not collect personal data merely because analytics can.

## Launch prompt

```text
Do not change the app yet. Perform a launch-readiness review for [TARGET USER]
completing [PRIMARY JOURNEY].

Review product completeness, mobile/accessibility, all data permissions, secret
handling, empty/error states, integrations, duplicate-action risks, and the live
publishing path. Separate confirmed findings from items I must test manually.

Return:
1. launch blockers,
2. important improvements,
3. optional polish,
4. a role-by-role manual test script,
5. the exact security and backup checks I must complete.
```

Official references: [publishing in the quick start](https://docs.base44.com/Getting-Started/Quick-start-guide), [security scan](https://docs.base44.com/Setting-up-your-app/running-a-security-scan), [performance](https://docs.base44.com/Performance-and-SEO/App-performance), and [SEO/search visibility](https://docs.base44.com/Performance-and-SEO/SEO-and-search-visibility).

---

[← Testing](05-testing-debugging.md) · [Course map](README.md) · [Bonus: Developer Path →](07-developer-path.md)
