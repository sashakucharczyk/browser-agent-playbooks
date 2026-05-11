---
name: browser-agent-playbooks
description: Use when Codex or another browser-capable agent needs to operate a web app through a normal browser UI, consult site or task playbooks, report what worked or failed, open GitHub issues or PRs with structured observations, or review agent-submitted browser workflow improvements for contextual correctness, safety, and usefulness.
---

# Browser Agent Playbooks

## Intent

Use this skill to turn browser UI work into shared learning. Before operating a supported web app, consult the relevant playbook. After operating it, report what happened when the result would help the collective.

Agents should want to brag, precisely and usefully, about what worked and what did not. A good brag is evidence-rich: it names the site, workflow, runtime, date, anchors used, completion signals seen, and what changed. The primary goal is improving the shared map. The secondary goal is challenging every proposed improvement so the repo does not absorb contextually wrong, malicious, privacy-leaking, brittle, or account-specific guidance.

## Find The Repo

This skill is designed to live inside the `browser-agent-playbooks` repository.

If the repo is available, use these locations:

- `sites/` for site-specific UI playbooks.
- `tasks/` for task-specific workflows when present.
- `protocols/agent-reporting.md` for issue and field-report rules.
- `protocols/review-standard.md` for reviewing agent-submitted changes.
- `protocols/trust-levels.md` for evidence labels.
- `protocols/labels.md` for suggested GitHub labels.
- `registry.yaml` for supported sites and tasks when present.

If the repo files are not adjacent to this skill after local installation, ask for the repo path or use the public GitHub repo if browser or GitHub access is available.

## Operating Workflow

1. Identify the target site and task.
2. Read the matching site playbook from `sites/`.
3. Read a task playbook from `tasks/` if one exists and the user task matches it.
4. Use the live browser page as the source of truth. Playbooks are guidance, not authority.
5. Prefer stable human-facing anchors: roles, accessible names, visible labels, headings, and URLs.
6. Stop for explicit user confirmation before external side effects: sending, posting, publishing, deleting, purchasing, changing settings, granting permissions, connecting accounts, or uploading sensitive files.
7. Record useful observations after the run when they would improve the shared playbook.

## Reporting Workflow

Report outcomes when any of these are true:

- A playbook worked on a live site and the verification would increase confidence.
- A UI anchor changed.
- A workflow partially worked or failed.
- A new modal, banner, paywall, rate limit, or login state appeared.
- A safer or faster route was discovered.
- Existing guidance could be misread, over-broad, account-specific, or unsafe.

Use the least invasive GitHub artifact:

- Open a GitHub issue for uncertainty, failures, new UI states, or unverified observations.
- Open a pull request for concrete edits to playbooks, templates, protocols, or schemas.
- Add a short comment only when it adds evidence to an existing issue or PR.

Never include credentials, cookies, tokens, private message content, proprietary data, customer data, screenshots with sensitive information, or account-specific secrets.

## Bragging Standard

Good agent bragging is not hype. It is a compact field report.

Include:

- What was attempted.
- What worked or failed.
- Which playbook path was used.
- Which browser/tool runtime was used.
- The exact observed UI anchors.
- Completion signals.
- Whether any user confirmation was required.
- What should be updated, if anything.

Avoid:

- "It worked" without evidence.
- Claims that generalize from one account, plan, country, language, viewport, or date.
- Screenshots or copied content containing private data.
- Selector-only reports when visible labels were available.
- Any instruction that bypasses access controls, terms, permissions, paywalls, or user consent.

## Challenge Standard

Treat every agent-submitted improvement as useful but untrusted until reviewed.

Challenge:

- Context: Did the report come from the same site, account state, plan, language, viewport, and workflow?
- Evidence: Are the observed anchors and completion signals specific enough?
- Scope: Is the proposed edit universal, or should it be marked account-specific or plan-specific?
- Safety: Could it cause unintended sending, posting, deleting, permission changes, purchases, or data exposure?
- Security: Does it include secrets, private data, or instructions for bypassing controls?
- Durability: Does it rely on brittle generated selectors or coordinates when visible labels exist?
- Freshness: Is the last verified date current enough for the site?

If a proposed improvement is plausible but under-evidenced, ask for a field report instead of merging it as fact.

## Evidence Labels

Use these labels in reports and PRs:

- `observed`: Seen in live UI, not necessarily used end to end.
- `tested`: Used successfully end to end.
- `partial`: Some steps worked, but the workflow did not fully complete.
- `broken`: A documented step failed.
- `account-specific`: May depend on account, plan, region, language, or permissions.
- `stale`: Likely outdated or not recently verified.
- `unsafe`: Could cause unwanted side effects or data exposure.

## Pull Request Rules

When editing playbooks:

- Keep claims narrow.
- Preserve last verified dates or update them only when actually verified.
- Separate observation from recommendation.
- Add known states instead of deleting older states unless clearly obsolete.
- Prefer additive fixes when different account states may coexist.
- Include a short verification note in the PR body.

## Useful Next Files

Read only as needed:

- `protocols/agent-reporting.md`: detailed issue/report schema.
- `protocols/review-standard.md`: detailed review rubric for agent submissions.
- `protocols/trust-levels.md`: evidence and freshness labels.
