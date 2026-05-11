# Review Standard For Agent Reports

Agent reports are helpful but not automatically trustworthy. Reviewers should assume each submission might be correct in its local context and wrong elsewhere.

## Review Goals

1. Preserve useful live evidence.
2. Prevent context-specific observations from becoming universal claims.
3. Block malicious, unsafe, privacy-leaking, or brittle instructions.
4. Improve the playbook without making it harder for future agents to use.

## Challenge Checklist

Ask these questions before accepting an issue claim or merging a PR.

### Context

- Which account plan, region, language, and viewport was used?
- Was the user signed in?
- Was the workflow read-only or did it change external state?
- Could another UI state coexist with the submitted one?

### Evidence

- Are exact visible labels, roles, headings, URLs, or completion signals included?
- Was the workflow actually tested end to end, or merely observed?
- Are screenshots or logs redacted if present?
- Is the last verified date credible?

### Scope

- Is the proposed wording too broad?
- Should it be marked `account-specific`, `plan-specific`, `region-specific`, or `stale`?
- Does it delete an older state that may still apply to other users?

### Safety

- Could the instruction cause posting, sending, deleting, purchasing, uploading, changing permissions, or connecting accounts without confirmation?
- Does it expose private or proprietary data?
- Does it encourage bypassing access controls, paywalls, rate limits, or terms?

### Durability

- Does it rely on brittle generated selectors, coordinates, or hidden implementation details?
- Could a visible role/name/label be used instead?
- Does it describe completion signals instead of scraping too early?

## Merge Guidance

Prefer:

- Additive notes for alternate UI states.
- Narrow claims with evidence labels.
- Human-facing anchors over implementation selectors.
- Clear confirmation boundaries.
- Small PRs focused on one site or workflow.

Avoid:

- Broad rewrites based on one account.
- Removing old guidance without explaining why it is obsolete.
- Merging reports that contain sensitive data.
- Instructions that automate externally consequential actions without confirmation.

## Disposition Labels

Use these labels or equivalents:

- `verified`: reviewed and supported by enough evidence.
- `needs-human-review`: useful but not yet mergeable.
- `needs-repro`: plausible but needs another run.
- `context-specific`: true only under stated account/UI conditions.
- `blocked-safety`: rejected or paused for privacy, security, or consent risk.

