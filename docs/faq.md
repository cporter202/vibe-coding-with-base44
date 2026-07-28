# Base44 beginner FAQ

> **Short answers, honest caveats, and official sources · Last verified July 27, 2026**

[← Repository home](../README.md) · [Course map](README.md) ·
[Official resources](resources.md)

Base44 changes quickly. Treat plan names, prices, credits, beta features, and UI
labels as time-sensitive and verify the linked official page before making a
purchase or production decision.

## Do I need to know how to code?

No. You can plan, build, refine, test, and publish through natural-language
prompts and visual tools. Knowing code can help with advanced customization, but
it is not required for this course or the starter projects.

Source: [Building an app](https://docs.base44.com/Getting-Started/Quick-start-guide)

## What can I build?

Base44 is designed for websites and web apps such as forms, dashboards, booking
systems, client portals, surveys, internal tools, CRMs, communities, and
prototypes. The best first project has one user, one important journey, and a
small data model.

Source: [Building an app](https://docs.base44.com/Getting-Started/Quick-start-guide)

## Is there a free plan?

Yes. The current Free plan includes a limited number of apps and credits plus
core features such as building, authentication, database functionality, and
analytics. Limits and plan models are changing, so verify the current billing
page rather than relying on a screenshot or old review.

Source: [Billing and plans](https://docs.base44.com/Account-and-billing/Billing-and-plans)

## What uses credits?

Message credits cover AI building work; integration credits cover supported
integration activity. Planning, building, fixes, and external capabilities can
have different credit behavior. Plan mode before the first build currently does
not use credits, Discuss mode is intended as a lower-credit thinking mode, and
manual visual edits do not use message credits.

Sources: [Credits](https://docs.base44.com/Account-and-billing/Credits) ·
[AI chat modes](https://docs.base44.com/Building-your-app/AI-chat-modes)

## Can I make a private app?

Creating a new private app currently requires a paid plan. A public app can
still require sign-in and enforce user-owned data, but app visibility,
authentication, and data authorization are separate decisions. Verify the
current plan rules before choosing an architecture.

Sources: [Billing and plans](https://docs.base44.com/Account-and-billing/Billing-and-plans) ·
[Managing access](https://docs.base44.com/Setting-up-your-app/Managing-access)

## Will the app work on mobile?

Base44 automatically creates responsive web apps, and the editor includes mobile
preview options. That is a starting point, not proof: test the main journey on a
real phone, check keyboard and touch behavior, and test the published URL.

Source: [Building an app](https://docs.base44.com/Getting-Started/Quick-start-guide)

## Can I publish to an app store?

Base44 documents a mobile app-store submission path. Store policies, developer
accounts, review requirements, and the product's current mobile packaging
capabilities apply. Finish and validate the web version before adding this
complexity.

Source: [Submitting to app stores](https://docs.base44.com/documentation/building-your-app/uploading-to-app-stores)

## Can I use my own domain?

Yes, on an eligible plan. You can connect an existing external domain, and some
annual paid plans may include a domain benefit. Domain and plan details vary, so
verify eligibility before buying elsewhere.

Sources: [Domains overview](https://docs.base44.com/Setting-up-your-app/Setting-up-your-custom-domain) ·
[Billing and plans](https://docs.base44.com/Account-and-billing/Billing-and-plans)

## Can I export the code or use GitHub?

Yes, on an eligible plan. Base44 currently documents ZIP export and GitHub
integration from the app editor. Exporting creates technical ownership and
maintenance work, so use a branch, review the diff, test locally, and never
commit secrets.

Sources: [Building an app](https://docs.base44.com/Getting-Started/Quick-start-guide) ·
[GitHub integration](https://docs.base44.com/developers/app-code/local-development/github)

## Can Base44 connect to other tools?

Yes. The platform supports built-in integrations, OAuth connectors, custom
workspace integrations, and backend functions for external APIs. Availability
and plan requirements differ. Each connection needs permission review, failure
handling, retries, and safe credential storage.

Sources: [Using integrations](https://docs.base44.com/Integrations/Using-integrations) ·
[Connectors](https://docs.base44.com/Integrations/Connectors)

## Can I accept payments?

Base44 documents payment options, including Base44 Payments in supported regions
and integrations such as Stripe. Payments are not a “just add a button” feature:
you need test mode, server-side confirmation, duplicate-event handling, refunds,
cancellations, reconciliation, and appropriate legal information.

Source: [Setting up Base44 Payments](https://docs.base44.com/Setting-up-your-app/setting-up-wix-payments)

## Is my app automatically secure?

Base44 supplies authentication, permission controls, secrets, security scans,
and other protections, but you remain responsible for configuring and testing
your app correctly. Review Create, Read, Update, and Delete access for every
table; test multiple users; inspect security findings; and avoid highly sensitive
data in a first project. Base44's documentation notes that app data is not
end-to-end encrypted.

Sources: [Security overview](https://docs.base44.com/Setting-up-your-app/security-overview) ·
[Run a security scan](https://docs.base44.com/Setting-up-your-app/running-a-security-scan)

## What is the difference between the app editor and the CLI?

The app editor is the visual, prompt-driven workflow used throughout this guide.
The Base44 CLI and backend service are a developer-oriented beta path for
defining and deploying entities, functions, connectors, auth, and sites from
local files. CLI-created projects are not currently integrated into the app
editor, although some standalone CLI commands can target editor apps by app ID.

Source: [CLI overview](https://docs.base44.com/developers/references/cli/get-started/overview)

## What should I build first?

Choose the smallest project that solves a real recurring problem without
requiring sensitive data, payment, or a complicated integration. Good options:

- [Lead Tracker](../starter-kits/lead-tracker.md)
- [Client Portal](../starter-kits/client-portal.md)
- [Booking Request Manager](../starter-kits/booking-manager.md)

If you are completely new, begin with the [15-minute Start Here lesson](00-start-here.md).

---

[← Course map](README.md) · [Choose a starter kit →](../starter-kits/README.md)
