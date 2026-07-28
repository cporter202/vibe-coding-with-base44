# Developer path: code, GitHub, SDK, and CLI

> **Bonus lesson · 20 minutes · Intermediate**
>
> **Outcome:** a clear map of editor GitHub sync versus the Base44 developer backend platform.

[← Launch](06-launch-checklist.md) · [Course map](README.md) · [Prompt Library →](../prompts/README.md)

You do not need this chapter to build your first app. Use it when the visual builder no longer gives you enough control, or when you want version control and a local workflow.

## First understand the two paths

Base44's current documentation describes two related but distinct development paths:

1. **App editor + GitHub sync:** Connect an app created in Base44's editor to a GitHub repository, edit locally, and sync changes through the `main` branch.
2. **Developer backend platform:** Use the Base44 CLI, SDK, local resource files, and managed backend. The CLI overview currently labels this beta and says CLI-created backend projects are not integrated with the app editor.

Read the current official docs before choosing. Do not assume a command from the backend/CLI path applies to an editor-created app.

## When GitHub helps

GitHub adds:

- A reviewable history of changes
- Branches and pull requests
- Easier collaboration
- Local editor and developer tooling
- Recovery from code regressions

GitHub does not replace Base44's database backup, permission review, live testing, or secret management.

## App editor GitHub sync

Current official notes include:

- GitHub two-way sync requires Builder or higher.
- Only the app owner can make the initial connection.
- Base44 automatically syncs app changes to the connected repository.
- Local changes become visible to Base44 after merging to a branch named `main`; other default branch names are not currently supported.
- You still click Publish in Base44 to make synced changes live.
- Connecting and disconnecting have important version-history/reconnection limitations; read the current GitHub integration page before proceeding.

Typical local setup after connecting:

```bash
git clone YOUR_REPOSITORY_URL
cd YOUR_REPOSITORY
npm install
```

The official docs currently list these local environment values for editor-exported apps:

```dotenv
VITE_BASE44_APP_ID=your_app_id
VITE_BASE44_APP_BASE_URL=your_backend_url
```

Put real values in `.env.local` and ensure that file is ignored by Git. Values prefixed `VITE_` are exposed to frontend code; never place a private provider secret there.

Run the repository's documented development command, commonly:

```bash
npm run dev
```

## A safe Git workflow

```bash
git switch -c feature/clear-description

# make and test one coherent change
git status
git diff
git add path/to/intended-file
git commit -m "Add clear description"
git push -u origin feature/clear-description
```

Open a pull request, review the diff, test the branch according to your setup, and merge only when ready. Keep secrets and `.env.local` out of commits.

## Base44 developer backend

Base44 documents a CLI and JavaScript SDK for managed backend projects. Current CLI setup requires Node.js 20.19 or newer and can be installed or invoked with:

```bash
npm install -g base44@latest
base44 login
```

Or:

```bash
npx base44@latest --help
```

The developer platform includes entities, auth configuration, Deno/TypeScript backend functions, automations, connectors, AI agents, hosting, and the JavaScript SDK. Always use current `--help` output and official docs because the CLI is beta.

## SDK mental model

The SDK can work with:

- `auth` for the current user and sessions
- `entities` for data operations
- `functions` for custom backend calls
- `integrations` for built-in/custom integrations
- `connectors` for connected external accounts

Treat client-side SDK calls as user-context calls. Sensitive operations still need strong entity permissions or server-side authorization.

## Backend-function safety

- Create the client from the incoming request so user context is available.
- Check role/ownership in the backend, not just the UI.
- Use service-role access only where genuinely required.
- Validate all input server-side.
- Store provider credentials with Secrets.
- Make webhooks and retries idempotent.
- Return safe errors; log identifiers, not credentials.
- Test direct HTTP endpoints as unauthenticated requests.

## Do not commit

```gitignore
.env
.env.*
!.env.example
node_modules/
dist/
```

If a secret enters Git history, remove it from the code and rotate/revoke it. Merely deleting the latest line does not invalidate the old secret.

Official references: [GitHub integration](https://docs.base44.com/developers/app-code/local-development/github), [developer platform](https://docs.base44.com/developers/home), [CLI overview](https://docs.base44.com/developers/references/cli/get-started/overview), [SDK overview](https://docs.base44.com/developers/references/sdk/getting-started/overview), and [backend functions](https://docs.base44.com/developers/backend/resources/backend-functions/overview).

---

[← Launch](06-launch-checklist.md) · [Course map](README.md) · [Prompt Library →](../prompts/README.md)
