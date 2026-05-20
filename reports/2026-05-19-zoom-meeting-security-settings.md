# Field Report: Zoom Meeting Security Settings Workflow

## Summary

- Site: `zoom.us`
- Playbook path: `sites/tools/zoom.us/site.md`
- Workflow: draft a meeting and locate security settings
- Verified at: `2026-05-19`
- Runtime: Codex Desktop Chrome plugin controlling a signed-in Chrome session
- Result: `tested`
- Scope: one signed-in Zoom account on a basic-plan-style schedule form

## What Worked

- Zoom home loaded at `https://us04web.zoom.us/myhome`.
- `Schedule` and the direct route `https://us04web.zoom.us/meeting/schedule` reached the schedule form.
- The schedule form exposed `Topic`, date/time/duration controls, `Invitees`, `Security`, `Passcode`, `Waiting Room`, `Save`, and `Cancel`.
- The `Topic` field accepted a harmless unsaved test title.
- The run confirmed `Passcode` and `Waiting Room` under meeting-level security settings.
- `Cancel` exited without saving the meeting.

## UI Anchors Observed

- `Schedule`
- `Schedule Meeting`
- `Topic`
- `Invitees`
- `Security`
- `Passcode`
- `Waiting Room`
- `Save`
- `Cancel`

## Completion Signals

- The schedule form was reached at `/meeting/schedule`.
- Security settings were visible and identifiable.
- The draft topic was unsaved and discarded.
- No invitees were added.
- No meeting was saved or started.
- No billing, calendar, privacy, or account-wide settings were changed.

## Repo Update Recommendation

- Add a tested Zoom playbook for meeting-level security-setting discovery.
- Explicitly warn agents not to dump hidden form fields or report generated passcodes, meeting IDs, links, account names, or tokens.
