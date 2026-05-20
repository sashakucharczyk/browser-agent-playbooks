# Tally Site Playbook

## Metadata

- Site: `tally.so`
- Category: `tools`
- Primary entry point: `https://tally.so/dashboard`
- Last verified: `2026-05-20`
- Verified with: Codex Desktop Chrome plugin controlling a signed-in Chrome session
- Verification depth: Dashboard entry, form creation, block insertion, conditional logic block, preview/publish controls were tested.
- Evidence level: `tested`, `account-specific`

## What This Playbook Helps With

Use this playbook when an agent needs to create a simple Tally form, add conditional logic, and locate preview/share-adjacent controls without publishing broadly, collecting responses, or connecting integrations.

This playbook is intentionally narrow. Tally workspaces, form editor state, block menus, and publishing requirements can vary. Treat the live UI as source of truth.

## Common Workflows

### Create A Form With Conditional Logic

Goal:

- Create a form with a question, add a multiple-choice block, add a conditional logic rule, and find preview/publish controls.

Entry state:

- Signed in at the Tally dashboard or workspace dashboard.

Steps:

1. Open `https://tally.so/dashboard`.
2. Click `New form`, or navigate directly to `https://tally.so/forms/create`.
3. Fill the `Form title` field with a harmless test title.
4. Use `Press Enter to start from scratch` or the blank editor body to add the first block.
5. Add a simple text prompt such as `Your name`.
6. Use `Insert block below` to open the block selection modal.
7. Search for `multiple choice`, click `Insert`, and fill a question plus options such as `Yes` and `No`.
8. Use `Insert block below` again, search for `conditional logic`, and click `Insert`.
9. Configure the visible rule fields, for example: question `Do you want follow up`, operator `Is`, option `Yes`, action `Show blocks`, then select a target block.
10. Confirm `Preview` and `Publish` controls are visible.
11. Stop before publishing broadly, collecting real responses, or connecting integrations unless the user explicitly approves.

Completion signals:

- The form title appears in the editor and sidebar.
- A multiple-choice question with options is visible.
- A conditional logic rule appears with visible fields such as question, `Is`, selected option, `Show blocks`, and selected block.
- `Preview` and `Publish` controls are visible.

Expected output location:

- A draft form in the signed-in user's Tally workspace.

## Useful UI Anchors

| Area | Anchor | Notes |
| --- | --- | --- |
| Dashboard | `New form` | Opens a blank form editor. |
| Direct route | `https://tally.so/forms/create` | Tested route when clicking `New form` did not visibly navigate. |
| Title | `Form title` | Contenteditable field for the form title. |
| Blank start | `Press Enter to start from scratch` | Starts the first block in a blank form. |
| Block insertion | `Insert block below` | Opens the block selection modal. |
| Block search | `Find questions, input fields and layout options...` | Search field for form blocks. |
| Choice block | `multiple choice` / `Insert` | Adds a multiple-choice question group. |
| Logic block | `conditional logic` / `Insert` | Adds a conditional logic rule block. |
| Logic action | `Show blocks` | Tested action for a rule. |
| Controls | `Preview` and `Publish` | Confirm the form can be previewed or prepared for publication. |

## Known States And Interruptions

| State | How it appears | Suggested handling |
| --- | --- | --- |
| Login required | Marketing page or login prompt instead of dashboard. | Stop and ask the user to sign in. |
| Click does not navigate | `New form` remains visible and the page stays on dashboard. | Use `https://tally.so/forms/create`. |
| Block modal is sparse | Only a search field appears at first. | Type the block name and wait for an `Insert` button. |
| Integrations tab opens | Buttons like `Connect` appear for external tools. | Do not connect integrations unless explicitly approved. |
| Publish needed for public URL | `Publish` is visible, but public sharing is not complete. | Stop unless publishing is part of the user-approved task. |

## Boundaries

Require explicit user confirmation before:

- Publishing broadly, copying public links, embedding publicly, or sending the form.
- Collecting real responses or using real respondent data.
- Connecting integrations, payment blocks, hidden fields with private data, or external services.
- Uploading files, changing workspace settings, upgrading, or changing billing.

## Notes

- The tested path used dashboard -> `/forms/create` -> title -> text block -> multiple choice -> conditional logic -> Preview/Publish controls.
- Do not include workspace IDs, private form URLs, response data, screenshots, or account details in reusable reports.
