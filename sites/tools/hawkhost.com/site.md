# Hawk Host Site Playbook

## Metadata

- Site: `hawkhost.com`
- Category: `tools`
- Primary entry point: Hawk Host Client Area, then authenticated cPanel File Manager
- Last verified: `2026-05-11`
- Verified with: Codex Desktop Chrome plugin controlling the user's authenticated Chrome session
- Verification depth: Active hosting service navigation, one-click cPanel entry, File Manager, `public_html`, `index.html` editing, save, and cache-busted public-page verification were tested in one account.
- Evidence level: `tested`, `account-specific`

## What This Playbook Helps With

Use this playbook when an agent needs to navigate Hawk Host's authenticated client area into cPanel File Manager for a user-approved static website file edit. This is not a general cPanel playbook yet; the evidence came from one Hawk Host shared-hosting account and should stay scoped to that context until reproduced elsewhere.

## Common Workflows

### Edit A Static Homepage File

1. Confirm the exact file, replacement content, and live-site effect with the user.
2. Open the Hawk Host Client Area in the user's signed-in Chrome profile.
3. From the active hosting service, use `View Details`.
4. Find the `One Click Login` area.
5. Open `File Manager`.
6. In cPanel File Manager, open `public_html`.
7. Select the target file, such as `index.html`.
8. Click toolbar link `Edit`.
9. If cPanel shows an encoding or editor confirmation modal, click modal button `Edit`.
10. Apply the approved change in the editor.
11. Stop for final user confirmation before saving the live file.
12. Click `Save Changes`.
13. Verify the public site through a normal rendered reload, preferably with a cache-busting query string when stale cache is plausible.

Completion signals:

- cPanel editor shows a saving state for the edited file.
- The rendered public site shows the approved change after reload.
- The verified public page matches the user's approved copy or expected content.

Expected output location:

- The live public website served from the edited file.

## Useful UI Anchors

| Area | Anchor | Notes |
| --- | --- | --- |
| Hosting service | button `View Details` | Opens the active service detail page from Hawk Host Client Area. |
| cPanel entry | section/link group `One Click Login` | Contains one-click login routes for hosting tools. |
| File manager | link `File Manager` | Opens cPanel File Manager without re-entering credentials in the observed account. |
| Web root | directory row `public_html` | Common public web root for static site files. |
| Homepage file | file row `index.html` | Select before editing. Other files may be present. |
| Edit toolbar | toolbar link `Edit` | Opens cPanel editor for the selected file. |
| Encoding modal | modal button `Edit` | Confirms opening the editor after cPanel's pre-edit prompt. |
| Editor mode | link `Use legacy editor` / `Use latest editor` | Switch modes if extraction or paste behavior is brittle. |
| Save action | button `Save Changes` | Writes the live file. Requires explicit confirmation. |

## Known States And Interruptions

| State | How it appears | Suggested handling |
| --- | --- | --- |
| Login required | Hawk Host sign-in page, cPanel login, or expired session. | Stop and ask the user to sign in. |
| Direct cPanel URL blocked | Browser cannot use a guessed Fileman/API URL. | Navigate through Client Area -> active service -> `View Details` -> `One Click Login` -> `File Manager`. |
| ACE editor virtualizes text | Direct textarea extraction or paste is unreliable in the modern editor. | Try the legacy editor/frame path, then verify visually or with rendered-page output. |
| Public cache stale | Saved file does not immediately appear on the public site. | Reload with a cache-busting query string before assuming save failed. |
| Sensitive session details visible | cPanel session URLs, server hostnames, account names, or email addresses appear. | Do not copy these into reports or reusable playbooks. |

## Boundaries

Require explicit user confirmation before:

- Saving any live website file.
- Uploading, deleting, renaming, moving, changing permissions on, or replacing files.
- Editing server, DNS, database, email, cron, backup, SSL, billing, or account settings.
- Publishing private content, credentials, customer data, proprietary code, or account-identifying details.

## Efficiency Notes For Agents

- Use the normal Hawk Host and cPanel UI route rather than probing direct cPanel endpoints.
- Keep file changes local or staged until the user approves the exact visible content.
- Do not publish cPanel session URLs, hostnames, account names, email addresses, or screenshots with account details.
- Treat the `public_html` and `index.html` path as observed in one account, not guaranteed for every site.
- Verify the live result as a rendered public page, not only editor text.
