# MIA Dev RAG Demo

Single-file, fully offline click-through demo of the MIA Console, hosted on Azure Static Web Apps.

- `index.html` - the standalone demo. No backend, login, Azure subscription, Dataverse environment or Fabric workspace required.
- `screenshots/` - reference screenshots of the demo screens.

## Run locally

Open `index.html` in Edge or Chrome, or serve the folder:

```bash
npx serve .
```

## Presenter shortcuts

- `Ctrl+Alt+Shift+R` - reset the seeded finance story between runs.
- `Ctrl+Alt+Shift+B` - toggle the Power Apps host command-bar frame for clean captures.

## Deployment

Pushes to `main` are published to Azure Static Web Apps by the workflow in `.github/workflows/`.

- Live URL: https://mango-desert-0f88f590f.7.azurestaticapps.net
- Azure resource group: `rg-mia-rag-demo-swa` (eastus2)
- Static Web App: `mia-dev-rag-demo` (Free tier)
- Azure identity: `ragnar@axsolutionsarchitecture.com`, tenant `979fd422-22c4-4a36-bea6-1cf87b6502dd`

Note: the Free tier has no built-in authentication, so the site itself is publicly
reachable even though this repository is private.

## Repository access

This repository is **private** and owned by the personal GitHub account **RagnarPitla**.
You must be signed in to github.com as `RagnarPitla` to see it - browsing while signed in
as the Microsoft EMU account (`ragnarpitla_microsoft`) returns a 404. The EMU account
cannot be added as a collaborator: GitHub rejects the invite with *"Enterprise Managed
Users cannot be invited to this repository because this Enterprise uses personal accounts."*

From the CLI:

```bash
GH_TOKEN=$(gh auth token -u RagnarPitla) gh repo view RagnarPitla/mia-dev-rag-demo
```

## Scope

This repository contains only the shareable click-through demo. Project Mia source,
ALM scripts and environment inventory are intentionally not included here.

## Source of truth - read before rebuilding

`index.html` is the built single-file bundle **and it has been hand-edited since it was
last generated**, so it no longer matches the console source tree in
`Project-Kazuki/.ragnar/00MIA-Dev-RAG-Demo-Complete/SOURCE/`. Regenerating the bundle with
`npm run build:mock` and copying it over `index.html` would destroy that work.

Edit `index.html` directly, or reconcile the bundle back into the source tree first.
The stale source tree is also why `.mock/smoke.mjs` no longer passes against this bundle -
that failure is pre-existing and unrelated to any styling change.

## UI conventions

Corner radii follow a fixed 4 / 8 / 12 / 16 / 20 px scale (plus `50%` for avatars and
`999px` for pills). The tokens `--radius-xs|sm|md|lg` and `--glass-radius*` are aligned to
that same scale - keep new values on it rather than introducing intermediate radii.

Transitions use `cubic-bezier(.2,0,0,1)` and stay at or below 0.2s. Avoid `transition: all`
- it animates layout properties and forces reflow; name the properties instead.
