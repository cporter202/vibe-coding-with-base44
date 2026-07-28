# Base44 starter kits

> **Three complete, beginner-safe build briefs—not vague idea prompts**

Each kit gives you a scoped version one, a Plan mode prompt, minimum data model,
permission matrix, build order, acceptance tests, and upgrade triggers.

[← Repository home](../README.md) · [Course map](../docs/README.md) ·
[Quick reference](../docs/quick-reference.md)

## Pick one

| Starter kit                                   | Best for                               | Core journey                                       | Build time |
| --------------------------------------------- | -------------------------------------- | -------------------------------------------------- | ---------: |
| [Lead Tracker](lead-tracker.md)               | Freelancers and service businesses     | Visitor submits → admin follows up                 |  45–60 min |
| [Client Portal](client-portal.md)             | Agencies, consultants, and freelancers | Client signs in → views and submits their work     |  60–90 min |
| [Booking Request Manager](booking-manager.md) | Coaches, salons, and local services    | Visitor requests time → admin confirms or declines |  60–90 min |

These are learning projects, not audited production systems. Use fictional data
until you have reviewed permissions, tested multiple roles, and completed the
[launch checklist](../docs/06-launch-checklist.md).

## How to use a kit

1. Read the whole kit before building.
2. Replace every bracketed value.
3. Start a new Base44 app with **Plan** turned on.
4. Paste only the Plan mode prompt first.
5. Answer Base44's questions and compare its plan with the kit.
6. Build one stage at a time and test before continuing.
7. Treat the permission matrix and acceptance tests as requirements.
8. Stop at the version-one boundary. The “later” list exists for a reason.

## The rule that saves beginners

Do not confuse a polished interface with a finished app. A starter kit is done
only when:

- the primary user completes the whole journey;
- invalid and repeated actions fail safely;
- User A cannot access User B's private data;
- the administrator workflow works;
- the security scan is reviewed; and
- the published URL passes the same tests as preview.

## Want a different project?

Use this generator in Discuss mode:

```text
I want a beginner-safe starter kit for [APP IDEA] used by [PRIMARY USER]. Do not
build anything. Reduce it to one complete version-one journey and return:

1. The user, problem, and measurable outcome
2. In-scope and explicitly out-of-scope features
3. Minimum pages
4. Minimum tables and fields
5. A visitor/user/admin CRUD permission matrix
6. A five-stage build order
7. Happy-path, validation, duplicate-action, failure, and cross-user tests
8. Upgrade triggers for version two

Flag sensitive data, payment, legal, or integration risks. Ask only questions
that would materially change version one.
```

Then use the [six-part prompt method](../docs/02-prompt-playbook.md) to build it
one stage at a time.

---

[← Course map](../docs/README.md) · [Open the Lead Tracker →](lead-tracker.md)
