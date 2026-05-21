# Field Report: Canva Custom-Size One-Pagers

```yaml
site: canva.com
playbook_path: sites/tools/canva.com/site.md
workflow: create_custom_size_one_pager_design_from_local_pngs
result: worked
verified_at: 2026-05-21
runtime: Codex Desktop Chrome plugin
account_context:
  plan: unknown
  language: English
  region: Canada inferred from CAD trial banner
  viewport: desktop
evidence_level: tested
ui_anchors_observed:
  - role: button
    label: Create a design
    purpose: open the creation dialog
  - role: button
    label: Custom size
    purpose: create a design with explicit pixel dimensions
  - role: spinbutton
    label: Width
    purpose: set the custom design width
  - role: spinbutton
    label: Height
    purpose: set the custom design height
  - role: button
    label: Create new design
    purpose: open the custom-size design editor
  - role: application
    label: Canvas content
    purpose: focus the page before pasting a clipboard image
  - role: menuitem
    label: Set image as background
    purpose: fit a pasted one-pager image to the page
  - role: button
    label: Add page
    purpose: add additional one-pager pages
  - role: textbox
    label: Design title
    purpose: name the Canva design
  - role: button
    label: Grid view
    purpose: verify all expected pages are present
completion_signals:
  - The editor opened at a /design/.../edit URL.
  - Canva showed All changes saved after edits.
  - The design title updated successfully.
  - Grid view showed the expected three page thumbnails.
changed_or_failed_anchors:
  - old: Upload files
    observed: The file chooser opened, but setting a local PDF failed with Not allowed.
    suggested_handling: Use clipboard image paste as a fallback, or ask the user to enable local-file access for the Codex Chrome Extension before retrying direct upload.
private_data_included: false
user_confirmation_required: []
notes: The run created a private Canva design from locally generated one-pager PNGs. The report omits account names, design contents beyond generic workflow labels, screenshots, and private file contents. Direct upload was not completed because local-file access was blocked, but clipboard paste plus Set image as background worked end to end.
```
