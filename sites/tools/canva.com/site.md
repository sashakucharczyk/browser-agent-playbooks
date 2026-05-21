# Canva Site Playbook

## Metadata

- Site: `canva.com`
- Category: `tools`
- Primary entry point: `https://www.canva.com/`
- Last verified: `2026-05-21`
- Verified with: Codex Desktop Chrome plugin controlling a signed-in Chrome session
- Verification depth: Template gallery navigation, template customization, editor load, share menu, download panel, PDF file-type selection, custom-size design creation, clipboard image paste, set-image-as-background, page add, grid-view verification, and design title editing were tested.
- Evidence level: `tested`, `account-specific`

## What This Playbook Helps With

Use this playbook when an agent needs to operate Canva through the normal browser UI to create a simple design from a template, create a custom-size design from prepared local visual assets, or locate export/download controls without publishing or sharing the design.

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

### Create A Custom-Size One-Pager Design From Local PNGs

Goal:

- Create a Canva design from prepared local one-pager PNGs without using Canva's direct file-upload flow, then verify the pages are present.

Entry state:

- Signed in at Canva home or an existing Canva page.
- Local source images have already been generated and reviewed.

Steps:

1. Click `Create a design`.
2. Click `Custom size`.
3. Fill `Width` and `Height` with the intended pixel dimensions.
4. Click `Create new design`.
5. Wait for the editor tab to load and show `All changes saved`.
6. Copy the first local PNG image to the browser clipboard.
7. Focus the Canva canvas and paste with `Ctrl+V`.
8. Right-click the pasted image and choose `Set image as background`.
9. For each additional one-pager, click `Add page`, copy the next PNG to the clipboard, paste it onto the new page, and choose `Set image as background`.
10. Edit the `Design title` if the user supplied a title.
11. Open `Grid view` and verify that the expected number of page thumbnails appears.

Completion signals:

- The editor opens at a `/design/<id>/.../edit` URL.
- The header shows the requested design title and `All changes saved`.
- Each page thumbnail in `Grid view` shows the expected one-pager.
- The page counter matches the expected page count.

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
| Create entry | `Create a design` | Opens the creation dialog from home/templates pages. |
| Custom dimensions | `Custom size` | Opens width, height, and unit controls. |
| Size fields | `Width`, `Height`, `Units` | Use explicit pixel dimensions when the target asset already exists. |
| Blank design action | `Create new design` | Opens the custom-size editor in a new tab/window. |
| Canvas target | `Canvas content` | Focus this area before pasting from the clipboard. |
| Page creation | `Add page` | Adds another page to the current Canva design. |
| Pasted image menu | `Set image as background` | Right-click a pasted image, then use this to fit the page. |
| Title control | `Design title` | Editable header textbox for naming the design. |
| Multi-page check | `Grid view` | Shows thumbnails for quick page-count and content verification. |

## Known States And Interruptions

| State | How it appears | Suggested handling |
| --- | --- | --- |
| Login required | Marketing page or account picker instead of `Home - Canva`. | Stop and ask the user to sign in. |
| Trial prompt | `Start your trial for $0 CAD` appears in the header. | Ignore unless it blocks the task; do not start a trial. |
| Print upsell | `Print with Canva` appears in template preview or download panel. | Avoid print controls unless explicitly requested. |
| Template gallery lazy load | Page text is sparse but image cards and preview labels exist after a delay. | Wait briefly and search for `Preview, ..., template` controls. |
| New tab/window | `Customize this template` opens the design editor in a new tab or window. | Switch to the newly opened design tab before continuing. |
| Download panel defaults to PNG | File type initially shows `PNG Suggested`. | Open `File type`, choose `PDF`, then stop before final download. |
| Local file upload blocked | In Codex Chrome plugin runs, Canva's `Upload files` file chooser can fail with `Not allowed` when setting local files. | Use clipboard image paste as a fallback, or ask the user to enable local-file access for the Codex Chrome Extension before retrying direct upload. |
| Pasted image is not full page | The image appears selected and smaller than the page after `Ctrl+V`. | Right-click the selected image and choose `Set image as background`. |
| Multiple `Canvas content` regions | Multi-page designs expose more than one canvas region. | Select or scroll to the intended page before paste; grid view is useful for final verification. |

## Boundaries

Require explicit user confirmation before:

- Downloading, sharing, publishing, presenting, printing, copying a public link, or creating a template link.
- Inviting collaborators or changing access.
- Starting a trial, buying paid assets, using paid print products, or purchasing anything.
- Uploading private files or connecting external apps.
- Editing existing user designs beyond the requested test design.

## Notes

- The tested path used `Templates` -> `Poster` -> a template preview -> `Customize this template` -> editor -> `Share` -> `Download` -> `File type` -> `PDF`.
- The custom-size one-pager path used `Create a design` -> `Custom size` -> `Create new design` -> clipboard paste -> `Set image as background` -> `Add page` -> `Grid view`.
- Do not include account names, team names, screenshots, private design contents, or downloaded files in reusable reports.
