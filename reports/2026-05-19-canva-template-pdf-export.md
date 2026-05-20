# Field Report: Canva Template PDF Export

```yaml
site: canva.com
playbook_path: sites/tools/canva.com/site.md
workflow: create_template_based_design_and_locate_pdf_export
result: worked
verified_at: 2026-05-19
runtime: Codex Desktop Chrome plugin
account_context:
  plan: unknown
  language: English
  region: Canada or United States account context unknown
  viewport: desktop
evidence_level: tested
ui_anchors_observed:
  - role: link
    label: Templates
    purpose: open the template gallery
  - role: text
    label: Poster
    purpose: choose a simple design category
  - role: button
    label: Preview, <template name>, template
    purpose: open a template preview
  - role: link
    label: Customize this template
    purpose: create a design from the selected template
  - role: menuitem
    label: Share
    purpose: open share/export options in the editor
  - role: button
    label: Download
    purpose: open the export/download panel
  - role: combobox
    label: File type
    purpose: choose the export format
  - role: option
    label: PDF
    purpose: select PDF export
completion_signals:
  - A Canva editor tab opened at a /design/.../edit URL.
  - The editor showed the template-derived design title and All changes saved.
  - The Share menu showed Download among share/export options.
  - The Download panel showed File type.
  - Selecting PDF revealed Presets, Digital, Print, Compress PDF, Flatten PDF, and the final Download button.
changed_or_failed_anchors: []
private_data_included: false
user_confirmation_required: []
notes: The run stopped before final download, sharing, publishing, print ordering, collaborator invite, public-link creation, or paid/trial action. The report omits account/team details and screenshots.
```
