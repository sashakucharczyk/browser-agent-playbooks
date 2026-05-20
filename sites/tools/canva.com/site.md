# Canva Site Playbook

## Metadata

- Site: `canva.com`
- Category: `tools`
- Primary entry point: `https://www.canva.com/`
- Last verified: `2026-05-19`
- Verified with: Codex Desktop Chrome plugin controlling a signed-in Chrome session
- Verification depth: Template gallery navigation, template customization, editor load, share menu, download panel, and PDF file-type selection were tested.
- Evidence level: `tested`, `account-specific`

## What This Playbook Helps With

Use this playbook when an agent needs to operate Canva through the normal browser UI to create a simple design from a template and locate export/download controls without publishing or sharing the design.

This playbook is intentionally narrow. Canva surfaces plan prompts, print upsells, templates, and editor controls that may vary by account, region, and design type. Treat the live UI as source of truth.

## Common Workflows

### Create A Template-Based Poster And Locate PDF Export

Goal:

- Create a simple design from a template, then find the PDF export controls without downloading, sharing, publishing, printing, or buying anything.

Entry state:

- Signed in at Canva home.

Steps:

1. Open `https://www.canva.com/`.
2. Click `Templates`.
3. Choose `Poster` from the template categories.
4. Wait for template preview cards to load. The cards may expose labels like `Preview, <template name>, template`.
5. Open a template preview.
6. Click `Customize this template`.
7. Wait for the Canva editor to load in a new tab or window.
8. Confirm the editor shows `All changes saved` and the design title.
9. Click `Share`.
10. Click `Download`.
11. Open the `File type` combobox.
12. Choose `PDF`.
13. Stop once the panel shows PDF options such as `Presets`, `Digital`, `Print`, `Compress PDF`, `Flatten PDF`, or the `Download` button.

Completion signals:

- A design editor tab opens at a `/design/<id>/.../edit` URL.
- The editor shows the template-derived design title and `All changes saved`.
- The Share menu contains `Download`.
- The Download panel contains `File type`.
- Selecting `PDF` reveals PDF-specific options and the Download button.

Expected output location:

- A Canva design in the signed-in user's Canva account.

## Useful UI Anchors

| Area | Anchor | Notes |
| --- | --- | --- |
| Home navigation | `Templates` | Top-level route to the template gallery. |
| Template category | `Poster` | Tested category for a simple template-based design. |
| Blank option | `Create a blank Poster (Portrait 3:4)` | Useful landmark but not the template path. |
| Template card | `Preview, <template name>, template` | Opens a template detail/preview surface. |
| Template action | `Customize this template` | Creates a design from the selected template, usually in a new tab/window. |
| Editor saved state | `All changes saved` | Confirms the created design has loaded and saved. |
| Export entry | `Share` | Opens sharing, link, download, print, and publish options. |
| Download entry | `Download` | Opens the export panel; do not click the final Download button unless explicitly approved. |
| Export format | `File type` | Combobox for PNG, JPG, PDF, and other formats. |
| PDF option | `PDF` | Selecting this exposes PDF presets and settings. |

## Known States And Interruptions

| State | How it appears | Suggested handling |
| --- | --- | --- |
| Login required | Marketing page or account picker instead of `Home - Canva`. | Stop and ask the user to sign in. |
| Trial prompt | `Start your trial for $0 CAD` appears in the header. | Ignore unless it blocks the task; do not start a trial. |
| Print upsell | `Print with Canva` appears in template preview or download panel. | Avoid print controls unless explicitly requested. |
| Template gallery lazy load | Page text is sparse but image cards and preview labels exist after a delay. | Wait briefly and search for `Preview, ..., template` controls. |
| New tab/window | `Customize this template` opens the design editor in a new tab or window. | Switch to the newly opened design tab before continuing. |
| Download panel defaults to PNG | File type initially shows `PNG Suggested`. | Open `File type`, choose `PDF`, then stop before final download. |

## Boundaries

Require explicit user confirmation before:

- Downloading, sharing, publishing, presenting, printing, copying a public link, or creating a template link.
- Inviting collaborators or changing access.
- Starting a trial, buying paid assets, using paid print products, or purchasing anything.
- Uploading private files or connecting external apps.
- Editing existing user designs beyond the requested test design.

## Notes

- The tested path used `Templates` -> `Poster` -> a template preview -> `Customize this template` -> editor -> `Share` -> `Download` -> `File type` -> `PDF`.
- Do not include account names, team names, screenshots, private design contents, or downloaded files in reusable reports.
