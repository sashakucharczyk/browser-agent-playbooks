# Field Report: Figma Design-File Workflow

## Summary

- Site: `figma.com`
- Playbook path: `sites/tools/figma.com/site.md`
- Workflow: create a design file, add a frame, and locate share/export controls
- Verified at: `2026-05-19`
- Runtime: Codex Desktop Chrome plugin controlling a signed-in Chrome session
- Result: `partial`
- Scope: one signed-in account, Figma file browser and new design editor

## What Worked

- The signed-in file browser loaded at `https://www.figma.com/files/...`.
- The file browser exposed `New file`, `New Design file`, and `New FigJam file`.
- Direct navigation to `https://www.figma.com/design/new` created a new Untitled design and opened the editor.
- The editor exposed `Share`, `Design`, `Prototype`, `Frame`, and frame preset landmarks.
- `Export` was observed before frame-preset mode and is expected to be object-selection dependent.

## What Did Not Complete

- Frame creation was not completed because a first-run terms/continue gate remained visible.
- The agent stopped before clicking `Continue` because it would accept or confirm a one-time account-level prompt.

## UI Anchors Observed

- `New file`
- `New Design file`
- `New FigJam file`
- `/design/<file-id>/Untitled...`
- `Share`
- `Design`
- `Prototype`
- `Frame`
- device preset landmarks such as `iPhone`, `Android`, `Tablet`, `Desktop`, `Paper`, and `Social media`
- first-run copy including `By continuing you agree` and `Continue`

## Completion Signals

- New design file existed in the browser editor.
- Frame tool controls were visible.
- Share/export route was visible enough to locate, but export was not executed.
- No share, invite, publish, export, download, team-setting, or terms-acceptance action was taken.

## Repo Update Recommendation

- Add a partial Figma playbook.
- Mark first-run terms/profile gates as a stop-and-ask condition.
- Mention `https://www.figma.com/design/new` as a fallback when `New Design file` does not respond from the file browser.
