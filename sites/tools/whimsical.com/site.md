# Whimsical Site Playbook

## Metadata

- Site: `whimsical.com`
- Category: `tools`
- Primary entry point: `https://whimsical.com/`
- Last verified: `2026-05-20`
- Verified with: Codex Desktop Chrome plugin controlling a signed-in Chrome session
- Verification depth: Workspace dashboard, new board creation, basic flowchart-object creation attempt, board menu, share panel, export/embed controls, and public-access toggles were tested.
- Evidence level: `tested`, `account-specific`

## What This Playbook Helps With

Use this playbook when an agent needs to create a simple Whimsical board or flowchart and locate export/share settings without enabling public access, inviting people, exporting, printing, or publishing.

This playbook is intentionally narrow. Whimsical board tools rely heavily on canvas interactions and icons; accessible text can be limited. Treat the live UI as source of truth and verify visually when possible.

## Common Workflows

### Create A Board And Locate Export/Share Settings

Goal:

- Create a simple board/flowchart artifact and locate export/share/embed controls.

Entry state:

- Signed in at a Whimsical dashboard or workspace.

Steps:

1. Open `https://whimsical.com/`.
2. From the workspace dashboard, click `+ New Board` or `Create new board`.
3. Close any introductory overlay such as `Learn all the basics...` if it blocks the board.
4. Use visible board tools or keyboard shortcuts to create a simple flowchart element. The tested board exposed flowchart rectangle icons and common board tools.
5. Optionally add harmless labels such as `Start` and `End`.
6. Confirm the board header shows the board title, `Present`, `Comments`, `Search`, and `Share`.
7. Open the board `More` menu if needed to inspect non-share actions such as `Get board info`, `Move to...`, `Copy to...`, `Save as template`, and `Delete board`.
8. Click `Share`.
9. Confirm the share panel exposes `Share`, `Export`, `Embed`, `Print`, public-access toggles, and embed code or related controls.
10. Stop before enabling public access, exporting, printing, inviting users, copying public links, or deleting/moving the board.

Completion signals:

- A new board opens in the workspace.
- The canvas/editor toolbar is visible.
- A simple board/flowchart object is present or the board tools are active.
- The top bar includes `Share`.
- The Share panel shows `Share`, `Export`, `Embed`, `Print`, and public-access toggles.

Expected output location:

- A private board in the signed-in user's Whimsical workspace.

## Useful UI Anchors

| Area | Anchor | Notes |
| --- | --- | --- |
| Dashboard | `+ New Board` | Creates a blank board. |
| Dashboard | `Create new board` | Alternate entry point. |
| Intro overlay | `Learn all the basics...`, `Close`, `Watch video` | Close only if it blocks the task. |
| Board header | Board title such as `untitled` | Confirms the new board opened. |
| Header controls | `Present`, `Comments`, `Search`, `Share` | Stable top-bar landmarks. |
| Board menu | `More` | Opens board actions. |
| Board menu items | `Get board info`, `Move to...`, `Copy to...`, `Save as template` | Useful orientation; avoid destructive actions. |
| Share panel | `Share`, `Export`, `Embed`, `Print` | Tested share/export/embed controls. |
| Public access | `Enable public access` or switch controls | Do not enable without explicit approval. |
| Embed code | iframe embed snippet | Do not copy/distribute unless explicitly requested. |

## Known States And Interruptions

| State | How it appears | Suggested handling |
| --- | --- | --- |
| Login required | Marketing page or login route instead of workspace. | Stop and ask the user to sign in. |
| Desktop app prompt | `Download the app` appears in the sidebar. | Ignore unless it blocks the workflow. |
| Intro overlay | `Learn all the basics to go from a blank canvas...` | Close if it blocks canvas controls. |
| Canvas text not visible in DOM | Created shapes/text may not appear as normal accessible text. | Use visible canvas state or screenshot if needed; do not overclaim from DOM alone. |
| Public access disabled | Share panel warns only workspace members can see the board. | Do not enable public access unless approved. |
| Destructive board actions visible | `Delete board`, `Move to...`, or `Copy to...` appear. | Do not use them unless requested. |

## Boundaries

Require explicit user confirmation before:

- Enabling public access, copying/distributing links, sharing, inviting, exporting, printing, or embedding publicly.
- Deleting, moving, copying, or templating existing boards.
- Creating teams, changing workspace settings, upgrading, or changing billing.
- Uploading files or adding sensitive/private content.

## Notes

- The tested path used workspace dashboard -> `+ New Board` -> close intro overlay -> basic flowchart creation attempt -> `Share` -> observed `Share`, `Export`, `Embed`, `Print`, and public-access controls.
- Do not include workspace names, private board URLs, embed codes, screenshots, or account details in reusable reports unless explicitly approved and sanitized.
