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

## Scope

This repository contains only the shareable click-through demo. Project Mia source,
ALM scripts and environment inventory are intentionally not included here.
