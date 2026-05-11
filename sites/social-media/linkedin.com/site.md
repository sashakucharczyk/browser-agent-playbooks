# LinkedIn Site Playbook

## Metadata

- Site: `linkedin.com`
- Category: `social-media`
- Primary entry point: `https://www.linkedin.com/feed/`
- Last verified: `2026-05-11`
- Verified with: Codex Chrome plugin controlling a signed-in Chrome session
- Verification depth: Feed page, global navigation, search box, feed controls, sort menu, and account menu were observed. No posts, messages, reactions, or profile changes were submitted.

## What This Playbook Helps With

Use this playbook when an agent needs to navigate LinkedIn through a signed-in browser session: read visible feed/profile/job context, search for people or companies, open profile pages, inspect messaging/notification areas, or prepare drafts for user review.

## Global Navigation Anchors

| Area | Anchor | Purpose |
| --- | --- | --- |
| Search | textbox `Search` | Searches LinkedIn. Use for people, companies, jobs, posts, and hashtags. |
| Home | button/link `Home` | Opens feed. May include notification count. |
| My Network | link `My Network` | Opens invitations and connection graph. |
| Jobs | link `Jobs` | Opens job search and saved jobs. |
| Messaging | link `Messaging` | Opens LinkedIn messages. Sending requires confirmation. |
| Notifications | link `Notifications` | Opens notifications. |
| Account | button `Me` | Opens profile/account menu. |
| Business menu | button `For Business` | Opens business/admin/product surfaces. |
| Premium upsell | link/button `Retry Premium` or similar | Upgrade path. Do not use unless requested. |

## Account Menu

Open with button `Me`.

Observed menu items:

| Item | Purpose | Agent handling |
| --- | --- | --- |
| Profile link / identity card | Opens the signed-in user's profile. | Safe for read-only profile review. |
| `View profile` | Opens the signed-in user's profile. | Safe for read-only profile review. |
| `Settings & Privacy` | Account settings. | Do not change settings without explicit request. |
| `Help` | Help center. | Safe to open if troubleshooting. |
| `Language` | Language settings. | Do not change without request. |
| `Posts & Activity` | User's posts and activity. | Read-only review is okay; editing/deleting requires confirmation. |
| `Job Posting Account` | Hiring/admin area. | Do not enter unless requested. |
| `Sign out` | Ends session. | Never click unless explicitly requested. |

## Feed Anchors

| Area | Anchor | Purpose |
| --- | --- | --- |
| Start composer | button `Start a post` | Opens posting workflow. Requires confirmation before entering/publishing content. |
| Video post | button `Video` | Starts media posting flow. Requires confirmation. |
| Photo post | button `Photo` | Starts image posting flow. Requires confirmation. |
| Article editor | link `Write article` | Opens article editor. Requires confirmation. |
| Feed sort | button like `Sort by: Top` | Opens sort menu. |
| Sort options | menu items `Top`, `Recent` | Changes feed ordering. Safe if user asks. |
| Post container | heading `Feed post` | Marks individual feed items. |
| Post menu | button `Open control menu for post by ...` | Opens controls such as report/hide/save. Use carefully. |
| Hide post | button `Hide post by ...` | Changes feed state. Requires confirmation. |
| Reaction | button `Reaction button state: no reaction` | Like/react flow. Requires confirmation. |
| Reaction menu | button `Open reactions menu` | Opens reaction choices. Requires confirmation. |
| Comment | button `Comment` | Opens comment composer. Requires confirmation before typing/submitting. |
| Repost | button `Repost` | Starts repost flow. Requires confirmation. |
| Send/share | link/button `Send` | Opens message/share flow. Requires confirmation. |
| Follow/connect | buttons/links like `Follow ...` or `Invite ... to connect` | Relationship-changing actions. Requires confirmation. |

## Common Workflows

### Read The Feed

1. Open `https://www.linkedin.com/feed/`.
2. Wait for global navigation and at least one `Feed post` heading.
3. If feed order matters, inspect `Sort by: Top`; switch to `Recent` only if requested.
4. For each visible post, capture the author/profile link, author headline if visible, post text, link preview, and visible engagement counts.
5. Do not click reaction, comment, repost, send, follow, connect, hide, or post menu controls unless requested.

### Search LinkedIn

1. Focus textbox `Search`.
2. Enter the user-approved query.
3. Submit the search.
4. Use visible filters/results to narrow to people, companies, jobs, posts, or groups.
5. Treat profile opening as read-only unless the user asks to connect, follow, message, or save.

### Review A Profile

1. Open a visible profile link, usually a URL containing `/in/`.
2. Extract only visible information: name, headline, location, about, experience, education, posts, mutual context, and public/contact buttons.
3. Do not click `Connect`, `Follow`, `Message`, `More`, endorsement, recommendation, contact-info, or edit controls unless requested.

### Prepare A Post Draft

1. Confirm that the user wants a LinkedIn post draft prepared in LinkedIn, not just drafted locally.
2. Click `Start a post` only after confirmation.
3. Enter content only after the user has approved the draft text.
4. Stop before clicking any publish/post button and ask for final confirmation.

## Known States And Interruptions

| State | How it appears | Suggested handling |
| --- | --- | --- |
| Login required | Sign-in wall or redirect from feed/profile pages. | Stop and ask the user to sign in. |
| Premium upsell | `Retry Premium`, `Claim Premium free trial`, or other premium link. | Ignore unless requested. |
| Notification counts | Labels like `0 new notifications` or `1 new notification`. | Useful context, not an action request. |
| Feed changes while reading | Posts reorder or refresh. | Capture URLs/profile links as soon as relevant. |
| External link warning | LinkedIn safety/go redirect. | Do not continue off-site unless requested. |
| Messaging composer | Messaging page or send/share modal. | Stop before sending text or attachments. |

## Boundaries

Require explicit user confirmation before:

- Posting, commenting, reacting, reposting, following, connecting, messaging, or sending.
- Editing profile, experience, settings, privacy, language, job postings, or company/admin pages.
- Opening external links from LinkedIn.
- Uploading photos, videos, documents, or other media.
- Hiding, reporting, unfollowing, deleting, or changing feed preferences.

## Efficiency Notes For Agents

- The global `Search` textbox and top navigation labels are stronger anchors than feed layout.
- Feed items are noisy. Start from `Feed post` headings, then gather the nearest author link and post text.
- LinkedIn exposes many buttons with action-specific names. Treat any verb that changes social state as confirmation-gated.
- Use `Me` -> `View profile` for the signed-in user's profile rather than relying on a personalized sidebar card.
- Avoid using profile viewer, post impression, and premium widgets as navigation anchors; counts and upsells change frequently.

