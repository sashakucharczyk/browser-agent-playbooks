# Field Report: Dropbox Folder And File Request Workflow

## Summary

- Site: `dropbox.com`
- Playbook path: `sites/tools/dropbox.com/site.md`
- Workflow: create a dummy folder and locate the file-request workflow
- Verified at: `2026-05-19`
- Runtime: Codex Desktop Chrome plugin controlling a signed-in Chrome session
- Result: `tested`
- Scope: one signed-in Dropbox account, empty/free-plan-style home state

## What Worked

- Dropbox home loaded at `https://www.dropbox.com/home`.
- The page exposed `All files`, `File requests`, `Upload`, `New folder`, and empty-state `Create a folder`.
- The empty-state `Create a folder` action opened a folder creation dialog.
- `Folder name input` accepted a dummy folder name.
- Leaving access as `Only me` and clicking `Create` created the folder.
- `File requests` opened the request page.
- `Request files` opened the `Create new request` dialog.
- `Cancel` closed the dialog before a request or link was created.

## UI Anchors Observed

- `Create a folder`
- `New folder`
- `Folder name input`
- `Only me`
- `Create`
- `File requests`
- `Request file`
- `Request files`
- `Create new request`
- `Title`
- `Description (optional)`
- `Folder for uploaded files`
- `Change Folder`
- `Cancel`

## Completion Signals

- Dummy folder opened at a Dropbox `/home/<folder-name>` URL.
- Request dialog displayed fields needed to create a file request.
- The run stopped before request creation.
- No upload, file share, request send, link creation, permission change, or app connection was performed.

## Repo Update Recommendation

- Add a tested Dropbox playbook for dummy folder creation plus file-request discovery.
- Emphasize canceling at the request dialog when the user has not approved request creation.
