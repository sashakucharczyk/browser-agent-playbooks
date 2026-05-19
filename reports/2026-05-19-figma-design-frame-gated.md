# Field Report: Figma Design-File Workflow

## Summary

- Site: `figma.com`
- Playbook path: `sites/tools/figma.com/site.md`
- Workflow: create a design file, complete first-run setup, add starter frames, and locate share/export controls
- Verified at: `2026-05-19`
- Runtime: Codex Desktop Chrome plugin controlling a signed-in Chrome session
- Result: `tested`
- Scope: one signed-in account, Figma file browser and new design editor

## What Worked

- The signed-in file browser loaded at `https://www.figma.com/files/...`.
- The file browser exposed `New file`, `New Design file`, and `New FigJam file`.
- Direct navigation to `https://www.figma.com/design/new` created a new Untitled design and opened the editor.
- First-run setup was completed after user follow-up approval. Optional email subscription remained unchecked.
- The free `Starter` plan was selected.
- The collaborator invite step was skipped.
- The editor prompt `What do you want to make today?` exposed `Website`, `Mobile app`, and `Desktop app`.
- Clicking `Desktop app` created frame-backed starter layers in the left sidebar.
- The editor exposed `Share`, `Design`, `Prototype`, `Frame`, and `Export`.

## What Required Care

- The first pass stopped at onboarding because it included account-level setup choices.
- The completion pass only proceeded after the user asked to finish the Figma run.
- Paid plans were avoided by selecting `Starter`.
- Invite controls were avoided by using `Skip`.

## UI Anchors Observed

- `New file`
- `New Design file`
- `New FigJam file`
- `/design/<file-id>/Untitled...`
- `How do you plan to use Figma?`
- `Will anyone else be joining you?`
- `Skip`
- `Which plan would you like?`
- `Starter`
- `Finish`
- `What do you want to make today?`
- `Desktop app`
- starter layer names including `Music`, `Chat`, `List`, `Auth`, and `Dashboard`
- `Share`
- `Design`
- `Prototype`
- `Frame`
- `Export`

## Completion Signals

- New design file existed in the browser editor.
- Starter frame-backed layers were visible in the left sidebar.
- The selected item state read `Figma Design, 1 item selected`.
- `Share` was visible in the top-right area.
- `Export` was visible in the right sidebar.
- No share, invite, publish, export, download, paid plan, or team-setting action was taken.

## Repo Update Recommendation

- Mark the Figma playbook as tested for this account state.
- Keep onboarding as a confirmation-sensitive workflow: optional subscription off, skip invites, free `Starter` only.
- Mention `https://www.figma.com/design/new` as a fallback when `New Design file` does not respond from the file browser.
- Add `Desktop app` as a tested starter-frame route.
