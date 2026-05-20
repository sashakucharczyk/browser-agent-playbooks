# Pitch Site Playbook

## Metadata

- Site: `pitch.com`
- Category: `tools`
- Primary entry point: `https://app.pitch.com/`
- Last verified: `2026-05-20`
- Verified with: Codex Desktop Chrome plugin controlling a signed-in Chrome session
- Verification depth: Template chooser, template-based deck creation, editor load, share panel, export panel, and PDF export options were tested.
- Evidence level: `tested`, `account-specific`

## What This Playbook Helps With

Use this playbook when an agent needs to create a Pitch deck from a template and locate export/share settings without exporting, sharing, inviting collaborators, or publishing externally.

This playbook is intentionally narrow. Pitch dashboards, template galleries, workspace names, and export settings vary by account and plan. Treat the live UI as source of truth.

## Common Workflows

### Create A Template Deck And Locate Export Settings

Goal:

- Create a presentation from a template, open the sharing surface, and confirm export options are available.

Entry state:

- Signed in at a Pitch dashboard or the new-presentation template chooser.

Steps:

1. Open `https://app.pitch.com/`.
2. If a dashboard appears, choose the create/new presentation route.
3. In the new-presentation template chooser, select a template and click `Create presentation`.
4. Wait for the editor to load.
5. Confirm editor controls such as `Text`, `Media`, `Shape`, `Chart`, `Table`, `Play`, `Share`, and `Add slide`.
6. Click `Share`.
7. In the share dialog, use the `Export` tab.
8. Confirm export options such as `PDF - compressed`, `PDF - high quality`, and `Export presentation`.
9. Stop before clicking `Export presentation`, sending invites, sharing externally, or publishing.

Completion signals:

- A template-based deck opens in the Pitch editor.
- The editor shows slide/template content and top-level controls.
- The `Share` dialog contains `Invite to collaborate`, `Share externally`, and `Export`.
- The `Export` tab shows PDF options and an `Export presentation` button.

Expected output location:

- A private presentation in the signed-in user's Pitch workspace.

## Useful UI Anchors

| Area | Anchor | Notes |
| --- | --- | --- |
| Template chooser | `All templates`, `Library templates`, `Private` | Useful landmarks on the new-presentation screen. |
| Blank route | `Start from blank` | Alternate to template creation; not used in the tested workflow. |
| AI route | `Start with AI` | Avoid unless explicitly requested. |
| Template action | `Create presentation` | Creates a deck from the selected template. |
| Editor controls | `Text`, `Media`, `Shape`, `Chart`, `Table` | Confirm editor loaded. |
| Presentation mode | `Play` | Useful editor landmark; do not present unless requested. |
| Sharing entry | `Share` | Opens collaboration/share/export dialog. |
| Share dialog | `Invite to collaborate`, `Share externally`, `Export` | Dialog tabs or sections. |
| Export options | `PDF - compressed`, `PDF - high quality` | Confirm export settings are available. |
| Final export | `Export presentation` | Stop before clicking unless explicitly approved. |

## Known States And Interruptions

| State | How it appears | Suggested handling |
| --- | --- | --- |
| Login required | Marketing page, account picker, or login route. | Stop and ask the user to sign in. |
| Template chooser already open | URL includes `/new-presentation` and multiple `Create presentation` buttons. | Pick a visible template and click its `Create presentation` button. |
| Search/action palette remains focused | `Search & actions` may remain visible after editor load. | Use Escape or click another editor control before opening Share. |
| Invite field visible | `Enter email address...` and disabled `Invite` button appear. | Do not enter emails or invite collaborators without approval. |
| External share options visible | `Share externally` appears in the Share dialog. | Do not enable sharing or copy links without approval. |

## Boundaries

Require explicit user confirmation before:

- Exporting/downloading a presentation.
- Sharing externally, copying public links, inviting collaborators, or publishing.
- Using AI features, importing files, connecting integrations, or changing workspace settings.
- Starting paid features, upgrading, or changing billing.

## Notes

- The tested path used the template chooser -> `Create presentation` -> editor -> `Share` -> `Export` -> observed PDF options and `Export presentation`.
- Do not include workspace IDs, private deck contents, private links, screenshots, or account details in reusable reports.
