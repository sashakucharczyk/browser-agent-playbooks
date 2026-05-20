# Field Report: Notion Private Database Filter

```yaml
site: notion.so
playbook_path: sites/tools/notion.so/site.md
workflow: create_private_database_page_with_filtered_table_view
result: worked
verified_at: 2026-05-19
runtime: Codex Desktop Chrome plugin
account_context:
  plan: unknown
  language: English
  region: unknown
  viewport: desktop
evidence_level: tested
ui_anchors_observed:
  - role: route
    label: https://www.notion.so/new
    purpose: create a fresh private page
  - role: textbox
    label: New page
    purpose: page title field
  - role: text
    label: Private
    purpose: confirm the page was in the private workspace area
  - role: button
    label: Database
    purpose: choose the database starter
  - role: button
    label: Empty database
    purpose: create a simple database without a template
  - role: button
    label: Filter
    purpose: open table-view filter controls
  - role: button
    label: Add advanced filter
    purpose: create the first visible filter rule
  - role: button
    label: Name
    purpose: default database title property in the rule
  - role: button
    label: Contains
    purpose: default text operator in the rule
  - role: input
    label: Value
    purpose: filter value field
completion_signals:
  - A private Notion page was created with the requested test title.
  - Choosing Database then Empty database created a page URL with a database view parameter.
  - The database page showed the default Table view.
  - The filter UI showed one rule with Name, Contains, and a filled value.
changed_or_failed_anchors: []
private_data_included: false
user_confirmation_required: []
notes: The run deliberately stopped before sharing, publishing, inviting users, connecting integrations, or editing unrelated workspace content. The report omits workspace name, private page contents, and screenshots.
```
