# Zoom Site Playbook

## Metadata

- Site: `zoom.us`
- Category: `tools`
- Primary entry point: `https://us04web.zoom.us/myhome`
- Last verified: `2026-05-19`
- Verified with: Codex Desktop Chrome plugin controlling a signed-in Chrome session
- Verification depth: Home page, schedule-meeting route, unsaved topic draft, security controls, passcode control, waiting-room control, invitees field, save/cancel controls were tested.
- Evidence level: `tested`, `account-specific`

## What This Playbook Helps With

Use this playbook when an agent needs to draft a Zoom meeting setup and identify meeting security controls without inviting attendees, saving a meeting, starting a meeting, or changing global account settings.

This playbook is intentionally narrow. Zoom UI can vary by account plan, region, account type, date/time defaults, side navigation state, and promotional overlays.

## Common Workflows

### Draft A Meeting And Locate Security Settings

Goal:

- Reach the schedule-meeting form, fill a harmless unsaved topic if needed, identify passcode and waiting-room controls, and stop before saving or inviting anyone.

Entry state:

- Signed in at Zoom home.

Steps:

1. Open `https://us04web.zoom.us/myhome`.
2. Use the visible `Schedule` link, or navigate directly to `https://us04web.zoom.us/meeting/schedule`.
3. Confirm the page title or header shows `Schedule a Meeting` / `Schedule Meeting`.
4. Use the `Topic` field for a harmless draft name if the test requires a filled draft.
5. Do not add invitees. The `Invitees` field is a useful landmark.
6. Locate the `Security` section.
7. Confirm `Passcode` is visible. Do not copy or report the generated passcode value.
8. Confirm `Waiting Room` is visible with explanatory copy such as `Only users admitted by the host can join the meeting`.
9. Confirm `Save` and `Cancel` are available.
10. Click `Cancel` or navigate away to discard the draft if the task does not require saving.

Completion signals:

- The schedule page is open at `/meeting/schedule`.
- The `Topic` field can be edited.
- The `Security` section is visible.
- `Passcode` and `Waiting Room` controls are visible.
- `Save` and `Cancel` controls are visible.
- The run stops without saving, inviting attendees, starting a meeting, or changing account settings.

Expected output location:

- No saved meeting, unless the user explicitly approves saving one.

## Useful UI Anchors

| Area | Anchor | Notes |
| --- | --- | --- |
| Home quick action | `Schedule` | Opens the schedule form. |
| Direct route | `https://us04web.zoom.us/meeting/schedule` | Tested route to the schedule form. |
| Form title | `Schedule Meeting` | Confirms the correct workflow. |
| Topic field | `Topic` | Safe draft field; tested with a dummy title. |
| Invite field | `Invitees` | Do not fill unless explicitly approved. |
| Security section | `Security` | Container for meeting-level security controls. |
| Security control | `Passcode` | Do not log or expose the generated value. |
| Security control | `Waiting Room` | Safe to observe; changing it should require task-specific approval. |
| Form controls | `Save` and `Cancel` | Stop before Save unless the user approved creating the meeting. |

## Known States And Interruptions

| State | How it appears | Suggested handling |
| --- | --- | --- |
| Promotional banners | Copy like `Upgrade to Pro`, free trials, or product promotions. | Ignore unless they block the schedule form. Do not start trials or upgrade. |
| Quick tour dialogs | Device management or onboarding tours may appear. | Dismiss only if clearly non-account-altering; otherwise stop and ask. |
| Host menu opens | `Host` can reveal `With Video On`, `With Video Off`, or `Screen Share Only`. | Avoid these options because they can start meetings. |
| Cookie/privacy controls | OneTrust or privacy dialogs may appear. | Do not change privacy preferences unless explicitly asked. |
| Hidden form fields | Zoom pages include hidden tokens and metadata. | Do not dump hidden inputs into reports or logs. |

## Boundaries

Require explicit user confirmation before:

- Saving or starting a meeting.
- Adding invitees, sending invitations, copying/joining links, or connecting calendars.
- Changing billing, plan, privacy preferences, global settings, or account-wide meeting defaults.
- Reporting passcode values, meeting links, personal meeting IDs, account names, or hidden tokens.

## Notes

- The tested path used `Home` -> `Schedule` or `/meeting/schedule` -> `Topic` -> `Security` -> `Passcode` and `Waiting Room` -> `Cancel`.
- Do not include meeting passcodes, personal meeting IDs, hidden form fields, CSRF tokens, account names, screenshots, or invitee information in reusable reports.
