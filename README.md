# Vibe Coding with Base44

![Vibe Coding with Base44 — From idea to app, no coding experience required](assets/vibe-coding-with-base44-hero.png)

**The practical, zero-to-launch Base44 course I wish existed when I started.** Learn by building a real app—not by reading a feature list.

> **Affiliate disclosure:** The Base44 links marked “Start free” are affiliate links. If you create or upgrade an account through one, I may earn a commission at no extra cost to you. The guide is independently written, and you can always visit [Base44 directly](https://base44.com/). [Full disclosure](AFFILIATE-DISCLOSURE.md).

[![Level: Beginner](https://img.shields.io/badge/LEVEL-BEGINNER-7C5CFC?style=for-the-badge)](docs/00-start-here.md)
[![Start: Free](https://img.shields.io/badge/START-FREE-00BFA6?style=for-the-badge)](https://base44.pxf.io/c/6763812/2049275/25619?subId1=github&trafcat=base)
[![Docs Quality](https://img.shields.io/github/actions/workflow/status/cporter202/vibe-coding-with-base44/docs-quality.yml?branch=main&style=for-the-badge&label=DOCS)](https://github.com/cporter202/vibe-coding-with-base44/actions/workflows/docs-quality.yml)
[![License: MIT](https://img.shields.io/badge/LICENSE-MIT-1F6FEB?style=for-the-badge)](LICENSE)

## Start in 60 seconds

1. Open the [15-minute Start Here lesson](docs/00-start-here.md).
2. Write one sentence describing your user and their problem.
3. Paste the provided planning prompt into Base44's **Plan mode**.
4. Follow the [lead-tracker build-along](docs/01-build-your-first-app.md).
5. Use the [launch checklist](docs/06-launch-checklist.md) before sharing your app.

**No code, database experience, or technical vocabulary required.**

[![Start building free with Base44](https://img.shields.io/badge/START_BUILDING_WITH_BASE44-→-FF6B6B?style=for-the-badge)](https://base44.pxf.io/c/6763812/2049275/25619?subId1=github&trafcat=base)

## Choose your path

| You are...               | Recommended path                                                                                                                                                                                                                                         |      Time |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------: |
| Completely new           | [Start Here](docs/00-start-here.md) → [First App](docs/01-build-your-first-app.md) → [Prompts](docs/02-prompt-playbook.md) → [Security](docs/03-data-auth-security.md) → [Testing](docs/05-testing-debugging.md) → [Launch](docs/06-launch-checklist.md) | 2–3 hours |
| Already building         | [Prompt Playbook](docs/02-prompt-playbook.md) → [Testing](docs/05-testing-debugging.md) → [Troubleshooting](docs/troubleshooting.md)                                                                                                                     | 45–60 min |
| Adding advanced features | [Security](docs/03-data-auth-security.md) → [Integrations](docs/04-integrations-workflows.md) → [Developer Path](docs/07-developer-path.md)                                                                                                              | 60–90 min |
| Fixing one problem       | Go directly to [Troubleshooting](docs/troubleshooting.md) or the [Prompt Library](prompts/README.md)                                                                                                                                                     |  5–15 min |

[View the complete course map →](docs/README.md)

## What you will build

The guided project is a polished lead tracker for a small service business:

```mermaid
flowchart LR
    A["Visitor opens public page"] --> B["Submits an inquiry"]
    B --> C["Lead is stored safely"]
    C --> D["Admin reviews the lead"]
    D --> E["Status and follow-up updated"]
    E --> F["App tested and published"]
```

Along the way, you learn the same patterns used in client portals, booking tools, internal dashboards, directories, support systems, and lightweight SaaS products.

## The complete guide

|     # | Lesson                                                        | You will finish with                              |      Time |
| ----: | ------------------------------------------------------------- | ------------------------------------------------- | --------: |
|     1 | [Start Here](docs/00-start-here.md)                           | A clear, buildable version-one plan               |    15 min |
|     2 | [Build Your First App](docs/01-build-your-first-app.md)       | A working public form and private admin dashboard | 45–60 min |
|     3 | [Prompt Playbook](docs/02-prompt-playbook.md)                 | A repeatable system for precise changes           |    20 min |
|     4 | [Data, Auth & Security](docs/03-data-auth-security.md)        | A safe data model and permission matrix           |    25 min |
|     5 | [Integrations & Workflows](docs/04-integrations-workflows.md) | A plan for email, APIs, automations, and payments |    20 min |
|     6 | [Testing & Debugging](docs/05-testing-debugging.md)           | Role-based tests and a reliable debugging loop    |    20 min |
|     7 | [Launch Checklist](docs/06-launch-checklist.md)               | A responsibly tested release                      |    20 min |
| Bonus | [Developer Path](docs/07-developer-path.md)                   | A map for GitHub, local code, SDK, and CLI        |    20 min |

Also included:

- [20+ production-quality prompts](prompts/README.md)
- [Fast troubleshooting guide](docs/troubleshooting.md)
- [Curated official resources](docs/resources.md)
- [Printable progress checklist](docs/course-checklist.md)

## Why this guide is different

- **Outcome-first:** every chapter tells you what you will accomplish and how long it should take.
- **Beginner-safe:** technical terms are translated into plain language.
- **Copy-ready:** prompts include scope, permissions, failure states, and acceptance criteria.
- **Security-aware:** authentication is never confused with authorization.
- **Honest about limits:** plan requirements, beta features, and platform constraints are called out.
- **Maintained:** automated Markdown and link checks help catch quality regressions.
- **Independent:** commercial links are disclosed clearly and official documentation is linked for changing facts.

## The prompt pattern you will use

```text
On [PAGE], when [USER] does [ACTION], change [CURRENT BEHAVIOR] so that
[EXPECTED BEHAVIOR].

Keep [THINGS THAT MUST NOT CHANGE] unchanged.

Done means:
- [OBSERVABLE RESULT]
- [IMPORTANT FAILURE OR EDGE CASE]
- [WHAT MUST NEVER HAPPEN]
```

That small structure is the difference between “make it better” and a change you can review, test, and trust.

## Base44 in plain English

Base44 is an AI app builder. You describe what you want, and it can create the interface, data tables, authentication, logic, and hosted app. The productive workflow is:

The working loop is: **Plan → Build small → Review → Test → Secure → Publish → Learn.**

You remain the product owner. The AI can build quickly, but you decide who the app is for, what data it may expose, and what evidence proves it works.

## Current plan notes

Plans change, so verify details in [Base44's official billing documentation](https://docs.base44.com/Account-and-billing/Billing-and-plans) before purchasing. As of **July 27, 2026**:

- Free includes core building, authentication, database functionality, analytics, up to 5 apps, up to 25 monthly message credits with a current daily cap, and 100 monthly integration credits.
- Starter adds unlimited apps and in-app code edits.
- Builder is the first listed plan with backend functions, custom domains, GitHub integration, and manual model selection.
- New private apps require a paid plan.
- Plan and workspace changes are rolling out, so some accounts may differ.

Start free. Upgrade when a required capability—not impatience—justifies it.

## Safety before speed

Do not use a first project to store highly sensitive medical, financial, identity, children's, legal, or employment data. Never publish real API keys. Test every private workflow as two different users and an admin. Run Base44's security scan before launch.

Read [Data, Auth & Security](docs/03-data-auth-security.md) before collecting real user information.

## Contributing and support

- Found outdated information? [Report a documentation issue](https://github.com/cporter202/vibe-coding-with-base44/issues/new?template=documentation.yml).
- Have an improvement? Read [CONTRIBUTING.md](CONTRIBUTING.md).
- Need help with this guide? See [SUPPORT.md](SUPPORT.md).
- Need private account, billing, or platform help? Use [Base44 Support](https://docs.base44.com/Community-and-support/Contacting-support).

This is an independent community project—not official Base44 documentation and not affiliated with or endorsed by Base44 or Wix.

---

**Ready to turn your idea into something real?**

[![Start free with Base44](https://img.shields.io/badge/START_FREE_WITH_BASE44-→-FF6B6B?style=for-the-badge)](https://base44.pxf.io/c/6763812/2049275/25619?subId1=github&trafcat=base)

Then open [Start Here](docs/00-start-here.md) and build the smallest useful version first.
