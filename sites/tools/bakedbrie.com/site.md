# BakedBrie Site Playbook


## Purpose


BakedBrie is a work board where people and AI agents move cards through stages to approval. Workspace, then boards, then columns (the API calls them stages), then cards. Each card has one owner (a person, an agent, or an automation), a brief, comments, a result and a receipt. Agents work cards through rules tied to a column. This playbook covers the browser UI at app.bakedbrie.com, with short notes on the API.


## Metadata


- Category: tools
- Site: bakedbrie.com (app at app.bakedbrie.com)
- Primary entry point: https://app.bakedbrie.com/
- Last verified: 2026-10-03
- Verified with: signed-in cloud browser session, test cards only
- Verification depth: create/open/comment/move/cancel card, manage columns, and notifications check in one account, default viewport, English. API/MCP/Slack/review behavior was not tested.
- Evidence level: partial. Labels marked (seen) were read from the live page. Labels marked (docs) come only from the product docs (https://app.bakedbrie.com/llms.txt) and were not tested.
- Not exercised: Needs you page contents, Agents detail and the New agent flow, Receipts after a Done card, board Filter/List, search, notification categories below the fold, full OpenAPI/MCP reference, Slack, reviews, work folders.


## Common Workflows


### Check workspace and identity first


Goal: act in the right workspace as an identifiable account.


Entry state: signed in; https://app.bakedbrie.com redirects to a workspace after "Opening your workspace".


Steps:


1. An account can belong to several workspaces, and workspace names may be duplicated. Use the workspace switcher at top left.
2. Check the role label under the account name at bottom left and the workspace id in the URL (/w/<workspace>/...).
3. The display name defaults to "New user", so every comment and activity entry shows that name until it is set. There is no agent label. If an agent uses the account, ask the owner before changing the display name to something like "Name (agent)" so activity is attributable.
4. A "What should we call you?" prompt appears until a name is saved.


Completion signals:


- Role label and workspace id match the intended workspace.


### Create a card


Goal: add a card to a board without starting an agent run.


Steps:


1. On the board, click "New card" (top right), or type in the "Add a card, or describe the work" row in To do.
2. In the dialog "What do you want done?", the first line is the title and the rest is the brief.
3. Leave the toggle "Let Research Assistant start on it" OFF unless an agent run is intended.
4. Click "Create card". The button changes to "Creating" for a few seconds.


Completion signals:


- Toast "Saved.", the card appears in To do and the card count goes up.


Notes: the card is owned by whoever created it. It is not assigned to anyone else or to an agent automatically. "Research Assistant" is an example agent name from the observed session; agent names and matching control labels may differ. Keep the start toggle off regardless of the agent name.


### Open a card


Click the card. A side panel opens (URL changes to /cards/<id>) and shows skeleton bars for 2 to 4 seconds. Sections: stage buttons, Owner, Due, Work status, "NEXT STEP" box with "Hand to Research Assistant" and "Mark done", BRIEF (editable, "Edits save as you type. Earlier versions are in history."), RESULT, RECEIPT, ACTIVITY with an "Add a comment" box, "Add comment" and "Send to agent". Top icons: copy link, open full page, "More card actions", Close. Escape closes the panel.


### Comment on a card


Steps:


1. Open the card and scroll to ACTIVITY.
2. Type in "Add a comment" and click "Add comment".
3. Do not click "Send to agent" unless one agent run on the connected AI account is intended.


Completion signals:


- Activity shows "card comment created" and the comment under the author name with a timestamp. A line says "Comments are not sent to agents automatically."


### Move a card


Steps:


1. In the card panel click a stage button, or drag on the board (drag handle label: "Move <title>. Press Space to lift, arrows to pick a stage, Enter to drop").
2. A dialog "Move this card?" shows the consequence, for example "It moves to Doing. Any agent rule on that column starts." Buttons: "Keep here" and "Move to <stage>".
3. Read the consequence text before confirming. If it mentions an agent rule or run, get the owner's explicit approval for that consequence before clicking "Move to <stage>". If approval for that consequence is missing, choose "Keep here". Do not infer safety from the column name.
4. Click "Move to <stage>" only within the owner's authorized scope.


Completion signals:


- The breadcrumb at the top of the panel changes (for example "MY BOARD / DOING") and the card shows in that column.


Boundary: moving into a column with an agent rule triggers that rule, regardless of the column name. Moving into Done affects Receipts. For tests, use only a destination whose consequence text confirms the intended behavior; To do and Doing names alone do not establish safety.


### Manage columns


- Add: "Add column", enter a name in "Column name", click "Add column". New columns go just before Done. Toast: "Column added: <name>".
- Column menu ("<name>, column menu"): Rename, Move left / Move right, Delete column. The first column cannot move left and Done stays last.
- Delete: the dialog "Delete the <name> column?" says the column must be empty and rules using it must be removed first. Read the consequence text and get the owner's explicit approval to delete that column before clicking "Delete column". Removing rules also requires approval.


### Cancel a card (there is no delete in the UI)


Panel menu "More card actions" has Move, Pause and Cancel. Cancel opens "Cancel this card?" with an optional Reason box and "Keep it" / "Cancel card". Work status becomes "Cancelled" and the note says "Work cancelled. History and receipts stay with this card." The card stays on the board in its column. Use clearly marked test cards (for example prefix "[TEST]") because they cannot be deleted.


### Leave a handoff note on a card


1. Confirm the workspace (role label and workspace id in the URL).
2. New card, first line a title with a recognizable prefix such as "[Agent]", brief with what was done and sources. Toggle off.
3. Add a comment with the status. Do not move into a column whose consequence text mentions an agent rule or run without the owner's explicit approval.


Completion signals: card visible in To do, comment shown in ACTIVITY. No notification appeared after creating a card and comment in the observed session; do not assume the person was notified. If the user has authorized a separate chat or Slack handoff, use that route.


## Useful UI Anchors


| Area | Anchor | Notes |
| --- | --- | --- |
| Sidebar | Workspace switcher, Search (Cmd+K), Needs you, Boards, Agents, Receipts, Settings, account menu | (seen) |
| Board header | Board title menu, red "Stop all automatic sends", member avatars, Share, Automate, New card | (seen) |
| Board toolbar | Board / List toggle, Filter, Mine, Search cards, Add column, card count | (seen) |
| Default columns | To do, Doing, Done | A board can also have an agent column, for example "Research Assistant" with a rule "Research Assistant picks up new cards here". Cards there show "Waiting for an AI account" until an AI key is connected. |
| Settings tabs | General, Members, AI accounts, Connections, Apps and API, Notifications, Data | (seen) |
| URLs | /w/<workspace>/boards/<board>, /w/<workspace>/cards/<card>, /my-work (Needs you), /outcomes (Receipts), /agents, /settings, /settings/members, /settings/connections/ai, /settings/connections/services, /settings/api-tokens, /settings/notifications | /settings/connections alone gives "Page not found". |
| Receipts page | "Every Done card and what it took to get there." Counters: Done with an agent, First try, Needed changes, Done by hand | Empty until a card reaches Done. |
| Card receipt | AI account, Read, Sent outside BakedBrie, Accepted by, When, DELIVERIES | A manually worked card shows "None, manual work", "Brief only", "Nothing". |


## Known States And Interruptions


| State | How it appears | Suggested handling |
| --- | --- | --- |
| Login required | Sign-in page; every sign-in asks for a TOTP code. "Sign in again" if sign-in takes too long (docs). | Ask the user to sign in or supply the code through a secure route. |
| Slow load | Skeleton screens for 3 to 12 seconds on boards, panels and Settings. "Loading rules" in Automate takes about 10 seconds. | Wait, then re-read. |
| Needs you page | /my-work stayed on "Opening this page" for 8+ seconds | Contents unverified. |
| Panel covers toolbar | The card side panel covers the top of the board | Close it before using board toolbar buttons. |
| Menu toggling | Clicking a menu button twice closes the menu; Escape closes the card panel as well as menus | Click once, then the item. |
| Wrong workspace | Multiple workspaces may share a display name | Check role label and workspace id in the URL. |
| No agent can run | "Waiting for an AI account" | An AI account (OpenAI or Anthropic key, or a runner on the user's computer) is needed. Do not connect one without the owner's go-ahead. |


## Notifications


- In the one-account session on 2026-10-03, Settings, Notifications (seen) showed in-app notifications for actionable work, timezone, quiet hours (10:00 PM to 8:00 AM), daily digest (9:00 AM), email timing per category (Assignments: Immediate, Reviews and decisions: Immediate, Input requests: Immediate, Actionable blocks: Daily digest, more below the fold). These were per-member settings observed in that account, not verified universal defaults.
- After creating a card and a comment in that session, the notification count stayed at 0. This does not establish whether other members were notified or whether cards, comments or moves generate notifications in other configurations. The observed settings listed actionable categories (assignments, reviews, input requests, blocks).
- No webhook or outbound change feed for ordinary card changes was found in that session or the partial docs read on 2026-10-03; absence was not established across the product. The observed Automate UI included "When a service changes" options for HubSpot, Notion, Stripe, Typeform, Calendly and Shopify; signed events or interval checks were described in the docs only.
- Slack: Settings, Members has "Add to Slack". Per the docs, tagging @BakedBrie in a channel makes a card and approvals can post to Slack. Not tested.


## Browser vs API


API facts (docs only, nothing minted or called): MCP URL https://api.bakedbrie.com/mcp, bearer token (prefix bbk_prd_), expires in 90 days, acts as the member who minted it. Presets: Full control, Read only, Runner, Custom (coming later). Start any session with whoami. A browser session cookie plus a bearer token together gives AMBIGUOUS_AUTHORITY.

REST routes (docs only): base URL https://api.bakedbrie.com; full paths /api/v1/boards, /api/v1/boards/{id}/cards, /api/v1/cards/{id}, /api/v1/boards/{id}/agents. These paths and the base URL were checked against https://app.bakedbrie.com/docs/openapi.json on 2026-10-06; no API operations were called. Other API notes retain the original 2026-10-03 partial docs scope.


Agent-authored comments: a token acts as its minting member, so a comment made through the API shows that member's display name and is indistinguishable from a person unless the display name says it is an agent.


Agents and reviews (docs, not tested): an agent starts as a draft until published, and assignment is not permission. Permissions per agent: read_files, web, email, other_apps, deliver, create_images/audio/video, each off, ask or allowed. Reviews need a work folder (S3/R2 or hosted). The person who made something cannot approve it on a shared board (MAKER_CANNOT_APPROVE).


## Boundaries


Get the owner's go-ahead first for:


- "Stop all automatic sends", pausing rules, and the Automate toggles.
- Connecting an AI key, a service, Slack, or a destination. Adding triggers.
- Sharing or inviting people (Share opens Settings, Members with an invite form).
- "Hand to Research Assistant" (example agent name), "Send to agent", or any move whose consequence text mentions an agent rule or run (starts agent runs on the owner's AI account).
- "Delete column" and removing rules that use a column.
- Creating tokens or runner keys; billing or Data (export or delete workspace).
- Changing the account display name.

Create, comment, edit, move, cancel, or change columns only within the user's authorized scope. A test card or a familiar column name does not grant authorization.

Do not record or publish private workspace names, card titles, briefs, comments, results, workspace/board/card IDs, or screenshots containing private data in playbooks, reports, issues or PRs. Use generic labels and placeholders; checking an ID in the live URL does not authorize recording it.


## Notes


- Cards cannot be deleted in the UI; cancelled cards remain.
- Typing into the New card dialog works through form-input on the "Card title and brief" textbox; Create card then needs a few seconds.
- The owner and due fields in the card panel were not clickable (seen). Ownership changes through "Hand to Research Assistant" or other routes described in the docs.
- Claims are scoped to one account and UI state on 2026-10-03; re-verify before relying on them.
