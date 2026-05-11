# Contributing

This repo is for practical playbooks that help browser-based agents use web apps through the same UI a signed-in user sees.

## What Makes A Good Playbook

- Names the site, category, and last verified date
- Describes common workflows in operator-friendly language
- Uses durable visible labels, roles, and page landmarks where possible
- Notes plan, account, region, or UI-state assumptions
- Separates read-only workflows from actions that change external state
- Documents completion signals and common interruption states

## What To Avoid

- Credentials, cookies, tokens, private data, or screenshots containing sensitive information
- Brittle selectors when a stable visible label works
- Claims that a workflow is guaranteed to work across all accounts or plans
- Instructions for bypassing access controls, permissions, paywalls, or terms of service

## Suggested File Layout

Use one folder per site under the relevant category:

    sites/<category>/<site-domain>/site.md
    sites/<category>/<site-domain>/workflows.yaml
    sites/<category>/<site-domain>/known-states.md

Start from templates/site-playbook.md when adding a new site.
