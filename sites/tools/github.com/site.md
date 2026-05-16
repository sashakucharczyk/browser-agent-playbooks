# GitHub Site Playbook

## Metadata

- Site: `github.com`
- Category: `tools`
- Primary entry point: `https://github.com/`
- Last verified: `2026-05-15`
- Verified with: Codex Desktop Chrome plugin controlling a signed-in Chrome session, plus local PowerShell/Git fallback
- Verification depth: Public repository creation, empty-repo quick setup, repository metadata editing, topic entry, local push verification, repository file visibility, pull request creation from a pushed branch, and draft conversion were partially tested.
- Evidence level: `partial`, `account-specific`

## What This Playbook Helps With

Use this playbook when an agent needs to operate GitHub through the normal web UI for account-bound repository setup, metadata inspection, issue/PR review, or verification of repository state when a GitHub connector or CLI path is unavailable or insufficient.

For bulk file creation, edits, commits, and pushes, prefer local files plus Git when the user has approved the repository changes. Use the browser UI for authenticated account actions, final verification, and UI-only settings.

## Common Workflows

### Create A Public Repository Shell

1. Confirm the user wants a new public repository and understands that the repo name, description, README, topics, and pushed content may become visible publicly.
2. Open GitHub's new repository flow.
3. Use the textbox with accessible name `Repository name *` for the repo name.
4. Fill the repository `Description` if the user supplied one.
5. Select `Public` only when the user has explicitly asked for a public repo.
6. Click `Create repository`.
7. Wait for the empty repository page or `Quick setup` section.
8. Capture the remote URL from `Quick setup` if a local repository will be pushed.

Completion signals:

- The browser navigates to the new repository under `/<owner>/<repo>`.
- The empty repo page shows `Quick setup`.
- A remote URL is visible for pushing an existing repository.

Expected output location:

- The new repository page at `https://github.com/<owner>/<repo>`.

### Update Repository Metadata

1. Open the repository page as a signed-in owner or maintainer.
2. Use `Edit repository metadata` from the About panel.
3. Update the description, website, or topics only as approved by the user.
4. For topics, focus the combobox labeled `Topics (separate with spaces)`.
5. If paste/fill fails in the topics field, type topic names character by character into the focused combobox.
6. Press Escape if suggestions or dropdown state blocks the save control.
7. Click `Save changes`.

Completion signals:

- The About panel reflects the expected description and topics.
- Topics appear as separate pills rather than one combined string.

### Open A Pull Request From A Pushed Branch

1. Confirm the branch has already been pushed to GitHub.
2. Prefer the GitHub connector or CLI for PR creation when it has write permission.
3. If connector PR creation fails with a permission error such as `Resource not accessible by integration`, use the signed-in browser UI.
4. Open the compare URL:
   `https://github.com/<owner>/<repo>/compare/<base>...<branch>?quick_pull=1`
5. Confirm the page says `Open a pull request`, shows the expected base and compare branches, and reports that the branches can be merged.
6. Fill the title textbox `Add a title *`.
7. Fill the description under `Add a description`. If the body textbox has no useful accessible name, scope carefully to the pull request body textarea rather than clicking arbitrary textboxes.
8. Click `Create pull request`.
9. If the PR should be a draft but the creation page only creates a normal PR, use the `Still in progress?` area:
   - click `Convert to draft`
   - wait for dialog `Convert this pull request to draft?`
   - click the dialog's `Convert to draft` button

Completion signals:

- The browser navigates to `/pull/<number>`.
- The PR page shows the expected title, base branch, compare branch, commit count, and changed file count.
- For a draft PR, the page shows `Draft`, `Not ready`, or `Ready for review`, and `Ready to merge` is no longer the main state.

## Useful UI Anchors

| Area | Anchor | Notes |
| --- | --- | --- |
| New repository | page heading `New repository` | Entry point for repo creation. |
| Repository name | textbox `Repository name *` | Prefer this exact textbox role/name. `Repository name` alone may be ambiguous. |
| Description | textbox `Description` | Optional public repo metadata. |
| Visibility | control `Public` | Requires explicit confirmation before selecting for a public repo. |
| Create action | button `Create repository` | Externally visible side effect. Confirm before use. |
| Empty repo | section `Quick setup` | Confirms creation and exposes remote setup commands/URL. |
| Metadata | button `Edit repository metadata` | Opens About panel editing. |
| Topics | combobox `Topics (separate with spaces)` | Topic entry may be brittle with browser automation clipboard support. |
| Save metadata | button `Save changes` | Commits About panel metadata changes. |
| PR compare | page heading `Open a pull request` | Appears at the compare URL for a pushed branch. |
| PR title | textbox `Add a title *` | Pull request title field. |
| PR body | heading `Add a description` | The body field may need careful scoping when no accessible textbox name is exposed. |
| PR create | button `Create pull request` | Opens the PR. Requires confirmation or an explicit user request. |
| Draft conversion | area `Still in progress?` and button `Convert to draft` | Opens a confirmation dialog before changing PR state. |
| Draft confirmation | dialog `Convert this pull request to draft?` | Confirm with the dialog's `Convert to draft` button. |

## Known States And Interruptions

| State | How it appears | Suggested handling |
| --- | --- | --- |
| Login required | Sign-in page or account picker. | Stop and ask the user to sign in. |
| Ambiguous repo-name label | `Repository name` matches both a textbox and a suggested-name button. | Use role `textbox` with name `Repository name *`. |
| Empty repo quick setup | `Quick setup` appears after repo creation. | Use it to copy the remote URL for local push. |
| Topic entry clipboard failure | Browser automation reports that virtual clipboard is unavailable. | Focus the topics combobox and type topics character by character. |
| Topic suggestions block saving | Suggestions/dropdown remain open after typing. | Press Escape, then click `Save changes`. |
| Save changes timeout | Save appears to stall or click times out. | Re-check whether metadata already updated; if not, close suggestions and retry deliberately. |
| Connector can read but not write | GitHub connector can search or read issues but PR creation returns `Resource not accessible by integration`. | Keep read operations connector-first, then use signed-in Chrome for the blocked write action. |
| PR created as ready instead of draft | Compare page creates a normal open PR even when draft was intended. | Use `Convert to draft` and confirm the modal; verify `Draft` or `Not ready` appears. |
| Body textarea lacks stable name | The PR body field appears under `Add a description` but exposes no useful accessible textbox name. | Use the visible heading for orientation and a narrow textarea fallback only after confirming there are just the expected title/body fields. |
| Local Git dubious ownership | Git reports `detected dubious ownership` for the working copy. | Use a narrow safe.directory override for that repo path instead of broad global trust. |

## Boundaries

Require explicit user confirmation before:

- Creating a repository, especially a public repository.
- Pushing local content to GitHub.
- Changing repository visibility, topics, description, website, settings, collaborators, branch protection, secrets, webhooks, or integrations.
- Opening, closing, editing, or deleting issues, PRs, comments, releases, packages, branches, or repository files.
- Creating or changing PR state, including converting a PR to draft or ready for review.
- Uploading private, proprietary, customer, or credential-bearing files.

## Efficiency Notes For Agents

- Use the GitHub connector or CLI for structured issue, PR, commit, and file operations when available.
- Use Chrome for account-bound UI actions such as metadata controls that are awkward or unavailable through the connector.
- If a branch is already pushed, the compare URL with `?quick_pull=1` is the fastest browser route to the PR form.
- Use local Git for bulk repository content after user approval; it is cleaner than typing large docs into the browser.
- Verify public state by loading the repo page and checking file/folder visibility, README rendering, license recognition, commit SHA, and About panel metadata.
- Treat all GitHub UI observations here as account- and date-specific until reproduced.
