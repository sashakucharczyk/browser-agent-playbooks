# Notion Site Playbook

## Metadata

- Site: `notion.so`
- Category: `tools`
- Primary entry point: `https://www.notion.so/`
- Last verified: `2026-05-19`
- Verified with: Codex Desktop Chrome plugin controlling a signed-in Chrome session
- Verification depth: Private page creation, empty database creation, and a basic filtered table view were tested.
- Evidence level: `tested`, `account-specific`

## What This Playbook Helps With

Use this playbook when an agent needs to operate Notion through the normal browser UI for a signed-in workspace, especially to create a private page, create a simple database, or verify the path to database filters.

This playbook is intentionally narrow. Notion workspaces differ by plan, sidebar configuration, templates, AI features, and recent UI experiments. Treat the live UI as source of truth.

## Common Workflows

### Create A Private Database Page With A Filtered Table View

Goal:

- Create a private Notion page with an empty database and add a visible filter rule.

Entry state:

- Signed in at a Notion workspace or any existing Notion page with the left sidebar visible.

Steps:

1. Open `https://www.notion.so/new`.
2. Confirm the new page appears under the `Private` section or otherwise remains private to the current user.
3. Fill the page title in the `New page` title textbox.
4. In the starter options, choose `Database`.
5. Choose `Empty database`.
6. Wait for the database page to load with the default `Table` view.
7. Click `Filter`.
8. Click `Add advanced filter`.
9. Use the default rule shape when available: `Where` -> `Name` -> `Contains` -> `Value`.
10. Fill the filter value.

Alternate filter entry state:

- If `Filter` is not visible on the database toolbar, click `Settings` / `View settings`, choose `Filter`, then click `Add advanced filter`.

Completion signals:

- The page title changes to the chosen test title.
- The URL changes from `/new` to a Notion page/database URL.
- The page shows a default `Table` view.
- The database controls include `Filter`.
- The filter popover shows `1 rule` or a visible rule such as `Where Name Contains <value>`.

Expected output location:

- A private Notion page/database in the signed-in user's workspace.

## Useful UI Anchors

| Area | Anchor | Notes |
| --- | --- | --- |
| New page route | `https://www.notion.so/new` | Fastest observed route to create a new private page. |
| Sidebar privacy area | `Private` | Confirms the page is in the user's private workspace area when visible. |
| Page title | textbox placeholder `New page` | Fill this with the intended test or page title. |
| Starter option | `Database` | Appears in the new-page starter choices. |
| Database template | `Empty database` | Creates a simple database without template-specific fields. |
| View name | `Table` | Default database view after creating an empty database. |
| Filter control | button `Filter` | Opens the filter controls for the current database view. |
| View settings | button `Settings` / text `View settings` | In some account states, `Filter` is inside view settings rather than directly visible on the toolbar. |
| Filter creation | `Add advanced filter` | Creates the first visible rule in the filter popover. |
| Default property | `Name` | Default title property for an empty database. |
| Default operator | `Contains` | Observed default operator for the `Name` text property. |
| Filter value | input placeholder `Value` | Fill to make the rule concrete. |

## Known States And Interruptions

| State | How it appears | Suggested handling |
| --- | --- | --- |
| Login required | Notion marketing page, login page, or account picker appears instead of workspace/sidebar. | Stop and ask the user to sign in with the intended account. |
| Existing page selected | The browser opens the most recent Notion page instead of a dashboard. | Use `https://www.notion.so/new` for a fresh private page. |
| Starter tiles not visible | Page title exists but starter options are hidden below or delayed. | Wait briefly, then use visible text `Database` if present. |
| Filter hidden in toolbar | The database table loads, but only `Settings` is visible near the view controls. | Open `Settings` / `View settings`, then choose `Filter` and `Add advanced filter`. |
| Filter popover already open or stale | `Filter`, `1 rule`, or rule fields appear together. | Re-check visible filter state before clicking again. |
| Workspace-specific sidebar | Sidebar items vary by account, plan, or templates. | Use the route and visible page controls rather than assuming sidebar order. |

## Boundaries

Require explicit user confirmation before:

- Sharing, publishing, inviting users, or changing page permissions.
- Connecting integrations, granting new permissions, or installing Notion apps.
- Editing or deleting existing user content beyond the requested page or database.
- Creating pages that contain private, customer, credential, or proprietary data.
- Sending Notion AI prompts that include sensitive content.

## Notes

- The tested path created a private page titled `A01 Browser ROI Test - 2026-05-19`, selected `Database`, selected `Empty database`, then created a filter rule `Name contains Keep`.
- Do not include workspace names, page contents, private document titles, or screenshots in reusable reports.
