---
name: browser-playbook-check
description: Use when Codex is about to operate a human-designed website through a browser UI such as Chrome, Firefox, Browser, Playwright, browser-use, or an authenticated web app. Check the browser-agent-playbooks repo before starting when the route is not obvious, use relevant site/task playbooks if available, leave a lightweight +1 worked report when a playbook helps, and after completion route missing, stale, broken, or changed workflows to the browser-agent-playbooks reporting process.
---

# Browser Playbook Check

## Overview

Use this skill as the first pass before browser UI work. It helps an agent decide whether to consult the browser-agent-playbooks knowledge base, how to use it without treating it as authority, and when to report back after the task.

## Startup Check

1. Identify the target site/domain and the user goal.
2. Decide whether the browser route is obvious enough to proceed without repo lookup.
3. Check the repo when any of these are true:
   - the site is authenticated, stateful, or side-effectful
   - the workflow depends on specific UI anchors, dialogs, uploads, editors, or hidden navigation
   - the task has failed before or could waste meaningful time if the route is wrong
   - a connector/API path is blocked and the browser is the fallback
   - the agent is unsure how to accomplish the goal safely
4. If the task is a trivial public-page read or the route is already obvious, proceed normally and skip reporting unless something new is learned.

## Find The Knowledge Base

Look for the browser-agent-playbooks repo in this order:

1. A local checkout named `browser-agent-playbooks`.
2. The installed skill folder if it contains adjacent repo files.
3. The public GitHub repo if local files are unavailable and GitHub/browser access is available.

Read only what is needed:

- `registry.yaml` to find matching sites and tasks.
- `sites/<category>/<domain>/site.md` for site-specific UI anchors.
- `tasks/<task>/task.md` when the user goal matches a task playbook.
- `protocols/agent-reporting.md` only when reporting back.

## Use The Playbook

1. Treat the live page as the source of truth. Playbooks guide attention; they do not override the current UI.
2. Prefer visible labels, roles, headings, URLs, and completion signals over generated selectors or coordinates.
3. Preserve confirmation boundaries. Stop before sending, posting, publishing, deleting, purchasing, changing settings, granting permissions, connecting accounts, uploading sensitive files, or otherwise changing external state unless the user already clearly approved that action.
4. If the playbook is stale, unsafe, too broad, or wrong for the current account state, finish the user task safely and report the mismatch afterward.

## After The Task

Classify what happened:

- Existing playbook helped and no edit is needed: leave a lightweight `+1 worked` report if it would add useful confidence.
- Existing playbook helped but needs a small correction: use the browser-agent-playbooks workflow to open a focused PR or issue.
- No matching playbook existed: after completing the task, use browser-agent-playbooks to create a field report or propose a new playbook.
- Playbook failed, was stale, or exposed a safety risk: report the failure with evidence and do not silently generalize from the failed run.

For `+1 worked`, include only the lightweight schema from `protocols/agent-reporting.md`: site, playbook path, workflow, verified date, runtime, anchors used, completion signals, scope notes, and whether private data was included.

## Escalate To Browser-Agent-Playbooks

Use the `browser-agent-playbooks` skill when:

- a new site or task needs to be added to the repo
- an existing playbook needs a concrete update
- a field report should become a GitHub issue
- a proposed report or PR needs skeptical review before being trusted

Do not include credentials, cookies, tokens, private message content, customer data, proprietary data, unredacted screenshots, or account-specific secrets in reports.
