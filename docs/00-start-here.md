# Start here: your first 15 minutes

> **Lesson 1 of 7 · 15 minutes · Beginner**
>
> **Outcome:** a focused version-one plan you can confidently send to Base44.

[← Course map](README.md) · [Next: Build your first app →](01-build-your-first-app.md)

This chapter gets you from “I have an idea” to a sensible first build without wasting credits on an overstuffed prompt.

> **Affiliate disclosure:** The “start Base44” link below is an affiliate link. I may earn a commission if you purchase through it, at no extra cost to you.

## 1. Write the idea in one sentence

Use this formula:

> A **[type of product]** for **[specific user]** that helps them **[complete one valuable job]** without **[current frustration]**.

Examples:

- A lead tracker for solo home-service businesses that helps them follow up with inquiries without losing requests in text messages.
- A study planner for college students that turns assignments into a weekly schedule without maintaining a complicated spreadsheet.
- A client portal for freelance designers that lets clients review milestones and files without long email threads.

If the sentence contains three different audiences or several unrelated jobs, narrow it.

## 2. Define “version one”

Write down:

- **One primary user:** Who gets value first?
- **One main action:** What must they complete?
- **One success signal:** What observable result proves the app helped?
- **Three must-have features:** What makes that one journey possible?
- **A not-now list:** What tempting features can wait?

Example:

| Decision       | Lead-tracker answer                                      |
| -------------- | -------------------------------------------------------- |
| Primary user   | Solo service-business owner                              |
| Main action    | Review and update a new inquiry                          |
| Success signal | Every inquiry has a next step and follow-up date         |
| Must haves     | Public form, private lead list, status/follow-up editing |
| Not now        | Payments, team permissions, SMS, AI lead scoring         |

## 3. Start in Plan mode

[Create a Base44 account and begin a project](https://base44.pxf.io/c/6763812/2049275/25619?subId1=github&trafcat=base), open the mode menu in the first-prompt box, and choose **Plan**.

Paste this:

```text
Help me plan version one of this app before building it:

[PASTE YOUR ONE-SENTENCE IDEA]

The first release should support one complete user journey, not every possible
feature. Ask me questions about the target user, the main flow, the minimum data
we need to store, who can see or edit each kind of data, and the visual tone.

At the end, give me:
1. the primary user journey,
2. the pages,
3. the data tables and important fields,
4. roles and permissions,
5. acceptance criteria,
6. a clearly labeled "not in version one" list.
```

Plan mode is especially useful because it lets you fix misunderstandings before a build touches many files and features. Review the plan; do not accept it just because it sounds polished.

## 4. Check the plan before building

Do not click **Start building** until you can answer yes to these questions:

- Is there one clearly named primary user?
- Can I trace the main journey from start to finish?
- Does every page help that journey?
- Are data tables described in ordinary language?
- Does every private table say who can read, create, update, and delete records?
- Is the not-now list explicit?
- Can I test success without guessing?

If not, keep talking in Plan mode.

## 5. Build, then pause

After the first build:

1. Click through every page before prompting again.
2. Try the main action with realistic data.
3. Write down what is missing or wrong.
4. Separate **functional issues** from **visual preferences**.
5. Fix the first broken step in the main journey.

Do not immediately send a ten-item redesign prompt. You need to learn what exists before asking for changes.

## 6. Use the right mode

| Mode    | Use it for                                         | Changes the app? |
| ------- | -------------------------------------------------- | ---------------- |
| Default | A specific feature or functional change            | Yes              |
| Discuss | Planning, tradeoffs, explanations, debugging ideas | No               |
| Edit    | Selecting elements and polishing design            | Yes              |

Manual changes in Edit mode do not use message credits. AI-assisted element edits do.

## 7. Make your first refinement

Use this pattern:

```text
On [PAGE], when [USER] does [ACTION], change [CURRENT BEHAVIOR] so that
[EXPECTED BEHAVIOR].

Keep [THINGS THAT SHOULD NOT CHANGE] unchanged.

Done means:
- [OBSERVABLE RESULT 1]
- [OBSERVABLE RESULT 2]
- [IMPORTANT EDGE CASE]
```

Example:

```text
On the public Request Service page, when a visitor submits the form, save the
inquiry and show a friendly confirmation with the expected response time.

Keep the existing page layout and brand colors unchanged.

Done means:
- a valid submission creates exactly one Lead record,
- required fields show clear inline errors,
- the form cannot be submitted twice while it is saving,
- the visitor never sees the private admin dashboard.
```

## Your next step

Follow [Build your first app](01-build-your-first-app.md) for a complete project, or jump to the [Prompt playbook](02-prompt-playbook.md) if you already have an app.

Official references: [starting from your first prompt](https://docs.base44.com/Getting-Started/starting-from-your-first-prompt), [AI chat modes](https://docs.base44.com/Building-your-app/AI-chat-modes), and [writing effective prompts](https://docs.base44.com/Getting-Started/Prompt-guide).

---

[← Course map](README.md) · [Next: Build your first app →](01-build-your-first-app.md)
