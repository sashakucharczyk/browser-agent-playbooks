# Task Playbook: Open Pull Request From Pushed Branch

## Purpose

Help an agent open a GitHub pull request from an already-pushed branch when the connector or CLI path is unavailable, blocked, or insufficient.

## Scope

- Task: Open a GitHub pull request from a pushed branch
- Primary users: Agents publishing repo updates for human review
- Sites involved: `github.com`
- Required playbooks: `sites/tools/github.com/site.md`
- Last verified: `2026-05-15`
- Evidence level: `partial`, `account-specific`

## Inputs

- Repository owner/name.
- Base branch.
- Head branch.
- PR title.
- PR body.
- Whether the PR should be draft or ready for review.
- User confirmation that opening the PR is intended.

## Output

- Pull request URL.
- PR number.
- Draft/open state.
- Mergeability signal if visible.
- Any permission fallback used, such as connector read success but connector PR creation failure.

## Workflow

1. Verify the branch has already been pushed to GitHub.
2. Try the structured GitHub connector or CLI first when it has the necessary write permission.
3. If PR creation is blocked by connector permissions, open GitHub in the signed-in browser.
4. Navigate to `https://github.com/<owner>/<repo>/compare/<base>...<head>?quick_pull=1`.
5. Confirm the compare page shows `Open a pull request`, the intended base/head branches, and a mergeability message.
6. Fill `Add a title *` with the approved PR title.
7. Fill the body under `Add a description` with the approved PR body.
8. Click `Create pull request`.
9. If the PR must be draft and the page created it as normal open PR, use `Convert to draft` in the `Still in progress?` area and confirm the dialog.
10. Verify the PR page shows the expected title, number, branch direction, commit count, file count, and draft/ready state.

## Site-Specific Steps

| Site | Playbook | Use |
| --- | --- | --- |
| `github.com` | `sites/tools/github.com/site.md` | Use the compare URL, PR form anchors, and draft-conversion flow. |
| Local Git | none | Confirm current branch, latest commit, and pushed tracking branch before opening the PR. |

## Confirmation Boundaries

- Opening a PR.
- Closing, reopening, merging, converting draft state, marking ready for review, or retargeting branches.
- Adding closing keywords that will close issues on merge.
- Requesting reviews, assigning users, adding labels, or linking projects.

## Failure Modes

| Failure mode | How it appears | Suggested handling |
| --- | --- | --- |
| Connector write forbidden | API returns `Resource not accessible by integration` while reads still work. | Use signed-in Chrome for PR creation and note the fallback in the report. |
| Branch not pushed | Compare page cannot find the head branch or shows no diff. | Push the branch first, then reload the compare URL. |
| Wrong branch direction | Compare page shows unexpected base/head branches. | Stop and correct the compare URL before creating the PR. |
| Body field has weak accessible name | Only the title textbox has a clear role/name. | Use the `Add a description` heading for orientation and a narrow PR-body textarea fallback. |
| Draft unavailable on create form | `Create pull request` creates a normal PR. | Convert after creation with `Convert to draft` and confirm the modal. |
| Draft conversion not confirmed | The dialog `Convert this pull request to draft?` remains open. | Click the dialog's own `Convert to draft` button, then verify `Draft` or `Not ready`. |

## Reporting Notes

When reporting this workflow, include:

- Repository owner/name and PR number if public or approved.
- Base and head branch names.
- Whether connector, CLI, or browser UI created the PR.
- Exact PR form anchors used.
- Whether draft conversion was required.
- Completion signals from the final PR page.

Do not include credentials, token output, private repository data, session URLs, or unapproved issue/PR body content.
