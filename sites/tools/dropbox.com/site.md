# Dropbox Site Playbook

## Metadata

- Site: `dropbox.com`
- Category: `tools`
- Primary entry point: `https://www.dropbox.com/home`
- Last verified: `2026-05-19`
- Verified with: Codex Desktop Chrome plugin controlling a signed-in Chrome session
- Verification depth: Home/files page, dummy folder creation, file-request page, and file-request creation dialog were tested.
- Evidence level: `tested`, `account-specific`

## What This Playbook Helps With

Use this playbook when an agent needs to create a dummy Dropbox folder and locate the file-request workflow without uploading files, sharing links, inviting people, or sending a request.

This playbook is intentionally narrow. Dropbox UI can vary by plan, storage state, sidebar width, and whether onboarding or app-install prompts are visible.

## Common Workflows

### Create A Test Folder And Locate File Requests

Goal:

- Create a dummy folder, then reach the file-request creation dialog and stop before creating or sending a request.

Entry state:

- Signed in at Dropbox home or the All files page.

Steps:

1. Open `https://www.dropbox.com/home`.
2. Confirm the page shows file navigation such as `Home`, `All files`, `File requests`, `Upload`, and `New folder`.
3. Use `New folder` or the empty-state `Create a folder` action.
4. In the folder dialog, fill `Folder name input` with a dummy name.
5. Leave access as `Only me` unless the user explicitly requests otherwise.
6. Click `Create`.
7. Confirm the new folder opens or appears in All files.
8. Click `File requests` in the sidebar.
9. Click `Request file` or `Request files`.
10. Stop when the `Create new request` dialog is visible.
11. Click `Cancel` after recording the evidence if no request should be created.

Completion signals:

- The dummy folder appears in Dropbox and opens at a `/home/<folder-name>` URL.
- The file-request page shows `File requests`, `Request file`, or `Request files`.
- The request dialog shows `Create new request`, `Title`, `Description (optional)`, `Folder for uploaded files`, `Change Folder`, `Cancel`, and `Create`.

Expected output location:

- A dummy folder in the signed-in user's Dropbox account.

## Useful UI Anchors

| Area | Anchor | Notes |
| --- | --- | --- |
| Files home | `New folder` | Direct folder creation action. |
| Empty state | `Create a folder` | Alternate folder creation route. |
| Folder dialog | `Folder name input` | Tested input anchor for naming a folder. |
| Access setting | `Only me` | Safe default for dummy folders. |
| Sidebar | `File requests` | Navigates to `https://www.dropbox.com/requests...`. |
| File request page | `Request file` / `Request files` | Opens the request creation dialog. |
| Request dialog | `Create new request` | Safe stopping point before request creation. |
| Request dialog | `Cancel` | Use to exit without creating the request. |

## Known States And Interruptions

| State | How it appears | Suggested handling |
| --- | --- | --- |
| App install prompt | Copy like `Download the app to edit and share files effortlessly`. | Ignore or dismiss only if it blocks the workflow. |
| Upgrade-only controls | Deadline, password, or advanced request controls show `UPGRADE`. | Do not interact unless the user requests paid-plan investigation. |
| Upload affordances | `Upload`, file inputs, or drag-drop areas are visible. | Do not upload files unless explicitly approved. |
| Share folder button | `Share folder` appears after folder creation. | Do not open sharing or change permissions without approval. |

## Boundaries

Require explicit user confirmation before:

- Uploading files, creating share links, sending file requests, inviting people, or changing folder permissions.
- Moving, renaming, deleting, or sharing existing user files.
- Connecting Google Drive, OneDrive, desktop apps, or third-party integrations.
- Starting trials, upgrading, or changing billing.

## Notes

- The tested path used `Home` -> `Create a folder` -> `Folder name input` -> `Create` -> `File requests` -> `Request files` -> `Create new request` -> `Cancel`.
- Use dummy folder names only. Do not include private file names, folder contents, links, screenshots, or user account details in reusable reports.
