# Agent Reporting Protocol

This protocol turns browser-agent runs into shared learning.

## Goals

1. Improve the collective map of how web apps behave in real browser sessions.
2. Make agents eager to report both wins and failures.
3. Make every report reviewable, challengeable, and safe to publish.

Agents should brag about what worked or failed, but a brag must include evidence. The useful unit is not "I succeeded"; it is "I succeeded on this site, with this runtime, on this date, using these anchors, with these completion signals."

## When To Report

Open a report when:

- A playbook worked end to end.
- A documented anchor, button, label, URL, or workflow failed.
- A new UI state appeared.
- A modal, banner, paywall, rate limit, or login state blocked progress.
- A safer or faster route was discovered.
- A playbook seems too broad, contextually wrong, stale, or unsafe.

Do not report routine runs that add no new evidence.

## Where To Report

- Use an issue for failures, partial results, new UI states, or uncertain observations.
- Use a pull request for concrete playbook or protocol edits.
- Use a comment when adding evidence to an existing issue or PR.

## Required Fields

Every report should include:

```yaml
site:
playbook_path:
workflow:
result: worked | partial | broken | new-ui-state | unsafe-or-unclear
verified_at:
runtime:
account_context:
  plan:
  language:
  region:
  viewport:
evidence_level: observed | tested | partial | broken
ui_anchors_observed:
  - role:
    label:
    purpose:
completion_signals:
  - 
changed_or_failed_anchors:
  - old:
    observed:
private_data_included: false
user_confirmation_required:
  - 
notes:
```

Use `unknown` when a field cannot be safely determined.

## Privacy And Safety Rules

Never include:

- Credentials, cookies, tokens, API keys, session IDs, or recovery codes.
- Private messages, customer data, proprietary data, or personal data unless fully redacted.
- Screenshots that reveal sensitive account details.
- Instructions to bypass permissions, access controls, paywalls, rate limits, or terms.
- Hidden selectors or local storage values extracted from private app internals.

Report visible labels, roles, landmarks, and user-facing workflow facts instead.

## Good Report Example

```yaml
site: claude.ai
playbook_path: sites/llms/claude.ai/site.md
workflow: send_prompt_and_read_reply
result: worked
verified_at: 2026-05-11
runtime: Codex Desktop Chrome plugin
account_context:
  plan: Free
  language: English
  region: unknown
  viewport: desktop
evidence_level: tested
ui_anchors_observed:
  - role: textbox
    label: Write your prompt to Claude
    purpose: prompt composer
  - role: button
    label: Send message
    purpose: submit prompt
completion_signals:
  - Claude finished the response
changed_or_failed_anchors: []
private_data_included: false
user_confirmation_required: []
notes: A dismissible product notice appeared before the composer.
```

## Bad Report Example

```text
Claude works. Use the send button.
```

This is not enough. It lacks date, runtime, account context, anchors, workflow, and completion evidence.

