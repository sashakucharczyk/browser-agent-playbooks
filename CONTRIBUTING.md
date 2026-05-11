# Contributing

This repo is for practical playbooks that help browser-based agents use web apps through the same UI a signed-in user sees.

## What Makes A Good Playbook

- Names the site, category, and last verified date
- Describes common workflows in operator-friendly language
- Uses durable visible labels, roles, and page landmarks where possible
- Notes plan, account, region, or UI-state assumptions
- Separates read-only workflows from actions that change external state
- Documents completion signals and common interruption states
- Makes evidence level clear: observed, tested, partial, broken, inferred, or stale

## What To Avoid

- Credentials, cookies, tokens, private data, or screenshots containing sensitive information
- Brittle selectors when a stable visible label works
- Claims that a workflow is guaranteed to work across all accounts or plans
- Instructions for bypassing access controls, permissions, paywalls, or terms of service

## Agent Reports

Agents are encouraged to report what worked and what failed. Treat this as useful bragging: compact, evidence-rich, and humble about scope.

Good reports include:

- Site and playbook path
- Workflow attempted
- Runtime and verification date
- Account/UI context such as plan, language, region, and viewport when known
- Exact visible anchors used
- Completion signals
- Whether the run was observed, tested, partial, or broken
- Any confirmation boundaries encountered

Bad reports say only "this worked" or "this broke" without evidence.

## Reviewing Agent Submissions

Challenge every improvement before trusting it. Ask whether it is contextually wrong, too broad, unsafe, malicious, privacy-leaking, or too brittle.

Prefer narrow, additive changes that preserve account-specific alternatives. Do not merge guidance that could cause unintended posting, sending, deleting, purchasing, permission changes, file uploads, or private data exposure.

See `protocols/review-standard.md`.

## Suggested File Layout

Use one folder per site under the relevant category:

    sites/<category>/<site-domain>/site.md
    sites/<category>/<site-domain>/workflows.yaml
    sites/<category>/<site-domain>/known-states.md

Start from templates/site-playbook.md when adding a new site.
