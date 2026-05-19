# Figma Site Playbook

## Metadata

- Site: `figma.com`
- Category: `tools`
- Primary entry point: `https://www.figma.com/files/`
- Last verified: `2026-05-19`
- Verified with: Codex Desktop Chrome plugin controlling a signed-in Chrome session
- Verification depth: File browser entry, direct new-design route, editor controls, frame tool visibility, share control visibility, and export control visibility were observed. Frame creation was blocked by a first-run terms/continue gate.
- Evidence level: `partial`, `account-specific`

## What This Playbook Helps With

Use this playbook when an agent needs to start a Figma design-file workflow through the normal browser UI and locate creation, frame, share, and export controls without sharing or publishing anything.

This playbook is intentionally narrow. Figma account state, onboarding state, team context, editor layout, and plan can change the visible route. Treat the live page as source of truth.

## Common Workflows

### Create A Design File And Locate Frame/Export Controls

Goal:

- Create a design file or reach a design editor surface, locate the frame tool, locate share/export controls, and stop before sharing, publishing, inviting, or accepting account-level prompts.

Entry state:

- Signed in at the Figma file browser.

Steps:

1. Open `https://www.figma.com/files/`.
2. Look for file-browser controls such as `New file`, `New Design file`, and `New FigJam file`.
3. If the `New Design file` button does not open a file, try the direct route `https://www.figma.com/design/new`.
4. Wait for the editor URL to change to `/design/<file-id>/Untitled...` and the page title to show `Untitled - Figma`.
5. In the editor, confirm visible controls such as `Share`, `Design`, `Prototype`, `Frame`, and, when an object is selected, `Export`.
6. Use the `Frame` tool or frame presets only after dismissing non-sensitive UI that is safe to dismiss.
7. Stop if a first-run gate asks the user to accept terms, confirm account/profile details, or otherwise make a one-time account decision.

Completion signals:

- A Figma design editor opens at a `/design/<file-id>/...` URL.
- The editor shows `Share` in the top-right area.
- The toolbar exposes `Frame`.
- The right sidebar can expose `Export` after the relevant design object is selected.

Expected output location:

- A Figma draft design file in the signed-in user's account if file creation succeeds.

## Useful UI Anchors

| Area | Anchor | Notes |
| --- | --- | --- |
| File browser | `New file` | General creation entry point. |
| File browser | `New Design file` | Preferred visible button when it responds. |
| File browser | `New FigJam file` | Alternate creation route for board-style tasks. |
| Direct route | `https://www.figma.com/design/new` | Tested fallback when the file-browser button did not open a file. |
| Editor URL | `/design/<file-id>/Untitled` | Confirms a design file exists. |
| Editor toolbar | `Frame` | Frame tool anchor; shortcut `F` may expose frame presets. |
| Top-right action | `Share` | Do not invite, copy public links, or change access without approval. |
| Right sidebar | `Export` | Appears when an exportable object is selected; stop before exporting unless approved. |

## Known States And Interruptions

| State | How it appears | Suggested handling |
| --- | --- | --- |
| First-run profile/terms gate | Text like `What is your name?`, `One more thing`, `By continuing you agree`, or `Continue`. | Stop and ask the user to handle it. Do not accept terms or confirm profile/account prompts on the user's behalf. |
| New-design button does nothing | `New Design file` is visible but the page stays on the file browser. | Try `https://www.figma.com/design/new`. |
| Frame presets visible | Right sidebar lists device presets such as `iPhone`, `Android`, `Tablet`, `Desktop`, `Paper`, or `Social media`. | This indicates the frame tool is active, but not that a frame has been created. Confirm the layer or canvas state before claiming success. |
| Export hidden | `Export` is not visible while frame presets are open or no object is selected. | Select the frame/object after creation; do not export without approval. |

## Boundaries

Require explicit user confirmation before:

- Accepting terms of service or completing profile/onboarding prompts.
- Sharing, publishing, inviting collaborators, copying public links, exporting/downloading files, or changing permissions.
- Moving files between teams/projects or changing team settings.
- Using community, paid, AI, or organization-level features that may alter account state.

## Notes

- The tested run created a new Untitled design via `https://www.figma.com/design/new`, but stopped before frame creation because a first-run terms/continue gate remained visible.
- Do not include account names, team names, file IDs, screenshots, or design contents in reusable reports unless the user explicitly approves sanitized evidence.
