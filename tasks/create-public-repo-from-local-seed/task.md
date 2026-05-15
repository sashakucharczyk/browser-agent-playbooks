# Task Playbook: Create Public Repo From Local Seed

## Purpose

Help an agent turn an approved local folder into a public GitHub repository while keeping account-bound UI steps, local Git work, and public-sharing confirmation boundaries clear.

## Scope

- Task: Create a public GitHub repository from a local seed folder
- Primary users: Users who want a local artifact packaged as a shareable public GitHub repo
- Sites involved: `github.com`
- Required playbooks: `sites/tools/github.com/site.md`
- Last verified: `2026-05-12`
- Evidence level: `partial`, `account-specific`

## Inputs

- Desired repository owner and name.
- One-sentence public description.
- Whether the repository should be public or private.
- Local seed folder path.
- Files that should be included or excluded.
- License choice, if any.
- Topics/tags to apply.
- User confirmation that the resulting repository and pushed content may be publicly visible.

## Output

- A GitHub repository URL.
- A short summary of what was pushed.
- Verification notes covering README rendering, expected files/folders, license detection, commit/branch state, and visible About metadata.
- Any unresolved setup items, such as missing topics, branch protection, or follow-up docs.

## Workflow

1. Inspect the local seed folder and identify private files, credentials, drafts, generated clutter, or account-specific artifacts that should not be published.
2. Confirm public/private visibility, repo name, description, license, and included file scope with the user.
3. Use `sites/tools/github.com/site.md` to create the repository shell in GitHub when browser-authenticated creation is needed.
4. Capture the remote URL from the `Quick setup` section.
5. Initialize or reuse the local Git repository.
6. Add the GitHub remote.
7. Commit only the approved files.
8. Push the selected branch to GitHub.
9. Use GitHub's repository page to verify README rendering, expected file tree, license recognition, and latest commit.
10. Update repository metadata and topics if the user approved them.
11. Return the public URL and verification notes.

## Site-Specific Steps

| Site | Playbook | Use |
| --- | --- | --- |
| `github.com` | `sites/tools/github.com/site.md` | Create repository shell, update metadata/topics, and verify public repo state. |
| Local Git | none | Stage, commit, push, and inspect local history. |

## Confirmation Boundaries

- Creating a repository.
- Making a repository public.
- Pushing local content to GitHub.
- Adding a license or metadata that makes public claims.
- Publishing generated artifacts, personal data, private notes, credentials, customer data, or account-specific screenshots.
- Changing repository settings, collaborators, visibility, branch protection, secrets, webhooks, or integrations.

## Failure Modes

| Failure mode | How it appears | Suggested handling |
| --- | --- | --- |
| Repository name anchor ambiguity | Browser automation sees both a repository-name textbox and suggested-name button. | Use role `textbox` with accessible name `Repository name *`. |
| Bulk content awkward in browser | Docs or nested folders would need large manual UI entry. | Use local files plus Git push after user approval. |
| Topic entry clipboard failure | Browser automation cannot paste because virtual clipboard support is unavailable. | Focus the topics combobox and type character by character. |
| Topic save stalls | `Save changes` times out or suggestions remain open. | Press Escape to close suggestions, then retry the save and verify About metadata. |
| Git dubious ownership | Git refuses local commands with `detected dubious ownership`. | Use a narrow safe.directory override for the target repo path. |
| Remote already exists | `origin` is already set or points elsewhere. | Inspect remotes and confirm before replacing or adding another remote. |
| Public repo shows no files | Empty repo page remains after push attempt. | Check branch name, remote URL, push output, and whether local branch tracks `origin/main`. |

## Reporting Notes

When reporting this workflow, include:

- Repository owner/name, unless the user asks to keep it private.
- Whether the repo was public or private.
- Runtime used for GitHub UI actions.
- Local Git environment and any safe.directory handling.
- Exact GitHub UI anchors used.
- Completion signals from both Git and the rendered GitHub repo page.
- Whether the user confirmed creation, visibility, and push.

Do not include tokens, credential helpers, session URLs, private file contents, or non-public repository data.
