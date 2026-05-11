# Trust Levels

Use trust levels to keep playbooks honest about evidence quality.

## Evidence Levels

| Level | Meaning | Can update playbook? |
| --- | --- | --- |
| `observed` | Seen in the live UI, not used end to end. | Yes, for UI anchors or known states when scoped narrowly. |
| `tested` | Used successfully end to end. | Yes, strongest routine evidence. |
| `partial` | Some steps worked but the workflow did not complete. | Yes, usually as a warning or known state. |
| `broken` | A documented step failed. | Yes, if the failure is specific and reproducible enough. |
| `inferred` | Reasonable conclusion from visible UI, not directly tested. | Maybe, but mark as inference. |
| `stale` | Previously useful, but likely outdated. | Keep only with a warning or remove after review. |

## Context Labels

Use context labels when a report may not generalize:

- `account-specific`
- `plan-specific`
- `region-specific`
- `language-specific`
- `viewport-specific`
- `browser-specific`
- `plugin-specific`

## Freshness Guidance

Fast-changing web apps need recent verification.

- LLM web apps: prefer verification within 30 days for primary workflows.
- Social media apps: prefer verification within 30 days for posting, messaging, search, and feed workflows.
- Enterprise tools: verification freshness depends on app release pace and tenant customization.

If freshness is unknown, do not present guidance as current. Mark it `stale` or ask for a new run.

