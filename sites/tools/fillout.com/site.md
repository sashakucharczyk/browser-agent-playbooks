# Fillout Site Playbook

## Metadata

- Site: `fillout.com`
- Category: `tools`
- Primary entry point: `https://www.fillout.com/`
- Last verified: `2026-05-20`
- Verified with: Codex Desktop Chrome plugin controlling a signed-in Chrome session
- Verification depth: Form editor, short-answer field creation, preview/publish/share navigation, publish-gated share state, public form link, and embed controls were tested.
- Evidence level: `tested`, `account-specific`

## What This Playbook Helps With

Use this playbook when an agent needs to create or inspect a Fillout form with a required/simple field and locate embed/share controls. This workflow may require user-approved publishing before the share/embed surface becomes visible.

This playbook is intentionally narrow. Fillout editor routes, publish gates, embed options, and plan prompts can vary. Treat the live UI as source of truth.

## Common Workflows

### Create A Form Field And Locate Embed/Share Controls

Goal:

- Add a simple form field, locate preview/share/publish controls, and after user-approved publishing, confirm embed/share controls.

Entry state:

- Signed in at a Fillout workspace or form editor.

Steps:

1. Open Fillout and reach a form editor. Existing editor URLs may look like `https://build.fillout.com/editor/<form-id>/edit/...`.
2. Confirm the editor tabs or top navigation include `Edit`, `Integrate`, `Share`, and `Results`.
3. Add a field such as `Short answer`.
4. Fill the question text with a harmless label such as `What is your name`.
5. Locate form controls such as `Preview`, `Publish`, and `Share`.
6. Click `Share`.
7. If the Share tab only shows a `Publish` gate, stop and ask for user approval before publishing.
8. After the user approves/clicks `Publish`, revisit `Share`.
9. Confirm the public form link is visible and embed controls appear.
10. Confirm embed options such as `Embed form`, `Standard`, `Popup`, `Full screen`, and `Slider`.
11. Stop before sending the form, copying links into external channels, collecting real responses, or connecting integrations.

Completion signals:

- The form editor shows the created field.
- `Edit`, `Integrate`, `Share`, and `Results` navigation is visible.
- `Preview` and `Publish` are visible.
- After publishing, `Share` shows a form URL and `Embed form` options.

Expected output location:

- A form in the signed-in user's Fillout workspace. If publishing is approved, the form also has a public form URL.

## Useful UI Anchors

| Area | Anchor | Notes |
| --- | --- | --- |
| Editor nav | `Edit`, `Integrate`, `Share`, `Results` | Confirms form editor context. |
| Field list | `Short answer` | Tested field type for a simple required/basic input workflow. |
| Question editor | `Type your question here` | Editable question text area. |
| Preview | `Preview` | Safe landmark for form preview. |
| Publish gate | `Publish` | Share/embed may remain hidden until publishing. |
| Share tab | `Share` | Contains public link and embed controls after publishing. |
| Public link | `https://forms.fillout.com/t/<form-id>` | Do not copy or distribute unless approved. |
| Embed mode | `Embed form` | Embed control group. |
| Embed options | `Standard`, `Popup`, `Full screen`, `Slider` | Tested embed variants. |

## Known States And Interruptions

| State | How it appears | Suggested handling |
| --- | --- | --- |
| Login required | Marketing page, login page, or account picker. | Stop and ask the user to sign in. |
| Existing editor already open | Title like `My form | Fillout` and editor tabs are visible. | Continue from the existing form if it matches the test. |
| Share gated by publish | Share tab shows only `Publish` or no embed controls. | Stop and ask for explicit user approval before publishing. |
| Published share surface | Public form link and embed controls appear. | Record anchors; do not distribute the link unless requested. |
| Integration prompts | `Integrate` tab or app connection prompts appear. | Do not connect integrations without approval. |

## Boundaries

Require explicit user confirmation before:

- Publishing a form, copying/distributing links, embedding publicly, sending forms, or collecting real responses.
- Connecting integrations, payment processors, CRMs, or external apps.
- Uploading private files, using real respondent data, or changing workspace settings.
- Starting trials, upgrading, or changing billing.

## Notes

- The tested baseline initially stopped at the publish gate; after the user clicked `Publish`, the Share tab exposed the public link and `Embed form` controls.
- Do not include form IDs, public links, response data, screenshots, or account details in reusable reports unless explicitly approved and sanitized.
