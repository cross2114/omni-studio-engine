# Deployment Guide

## Pre-Deploy Checklist

- Confirm the latest user request is implemented.
- Run available checks: lint, typecheck, build, CSS syntax, `git diff --check`.
- Inspect `git status --short` and understand every changed file.
- Confirm no unrelated user changes are reverted.
- Confirm unused assets are intentionally removed and new assets are committed.

## Git Workflow

- Commit with a concise message that describes the delivery.
- Push the active branch only after checking the remote.
- If push is rejected because remote has new commits, use `git pull --rebase origin <branch>`, resolve conflicts, then push.
- Do not force-push unless the user explicitly approves.

## GitHub Pages

- Confirm Pages settings with `gh api repos/<owner>/<repo>/pages` when GitHub CLI is available.
- Confirm workflow status with `gh run list --limit 5`.
- Public URL commonly follows `https://<owner>.github.io/<repo>/`.

## Netlify or Vercel

- Use the configured provider if the repo already has one.
- For Netlify, use the Netlify deploy skill or CLI flow when available.
- For Vercel, use existing project configuration or CLI if already authenticated.
- Confirm the final production URL and deployment status.

## Final Response

- Provide the public URL.
- Mention the commit hash or deployment id.
- Mention checks that passed.
- Mention any residual risk or tool limitation briefly.
