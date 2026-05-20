# Field Report: Long-Tail Baseline Playbooks

```yaml
segment: C - Less-Known / Long Tail
result: worked-with-one-user-approved-publish-step
verified_at: 2026-05-20
runtime: Codex Desktop Chrome plugin controlling signed-in Chrome
model_context: Codex medium
private_data_included: false
rows_status:
  site: rows.com
  result: dropped
  reason: Rows was no longer available as a sign-up/workspace service for this test.
runs:
  - site: tally.so
    playbook_path: sites/tools/tally.so/site.md
    workflow: create_form_with_conditional_logic
    result: worked
    evidence_level: tested
    account_context:
      plan: unknown
      language: English
      region: unknown
      viewport: desktop
    ui_anchors_observed:
      - role: link
        label: New form
        purpose: create a blank form
      - role: route
        label: https://tally.so/forms/create
        purpose: direct form creation route
      - role: textbox
        label: Form title
        purpose: name the test form
      - role: button
        label: Insert block below
        purpose: open block picker
      - role: input
        label: Find questions, input fields and layout options...
        purpose: search for block types
      - role: button
        label: Insert
        purpose: insert multiple choice and conditional logic blocks
      - role: button
        label: Preview
        purpose: preview control
      - role: button
        label: Publish
        purpose: publish control
    completion_signals:
      - Form title appeared in the editor.
      - Multiple-choice question and options were visible.
      - Conditional logic rule showed question, Is, selected option, Show blocks, and selected block.
      - Preview and Publish controls were visible.
    changed_or_failed_anchors: []
    user_confirmation_required: []
    notes: Stopped before publishing, collecting real responses, or connecting integrations.
  - site: pitch.com
    playbook_path: sites/tools/pitch.com/site.md
    workflow: create_template_deck_and_locate_export_settings
    result: worked
    evidence_level: tested
    account_context:
      plan: unknown
      language: English
      region: unknown
      viewport: desktop
    ui_anchors_observed:
      - role: button
        label: Create presentation
        purpose: create a deck from a template
      - role: button
        label: Share
        purpose: open sharing/export dialog
      - role: button
        label: Export
        purpose: open export tab
      - role: text
        label: PDF - compressed
        purpose: export option
      - role: text
        label: PDF - high quality
        purpose: export option
      - role: button
        label: Export presentation
        purpose: final export action
    completion_signals:
      - Template deck opened in the Pitch editor.
      - Share dialog showed Invite to collaborate, Share externally, and Export.
      - Export tab showed PDF options and Export presentation.
    changed_or_failed_anchors: []
    user_confirmation_required: []
    notes: Stopped before exporting, sharing, inviting, or publishing.
  - site: fillout.com
    playbook_path: sites/tools/fillout.com/site.md
    workflow: create_form_field_and_locate_embed_share_controls
    result: worked
    evidence_level: tested
    account_context:
      plan: unknown
      language: English
      region: unknown
      viewport: desktop
    ui_anchors_observed:
      - role: tab
        label: Edit
        purpose: editor tab
      - role: tab
        label: Integrate
        purpose: integrations tab
      - role: tab
        label: Share
        purpose: share tab
      - role: button
        label: Short answer
        purpose: add a simple form field
      - role: button
        label: Preview
        purpose: preview control
      - role: button
        label: Publish
        purpose: publish gate before share/embed controls
      - role: text
        label: Embed form
        purpose: embed controls after publish
      - role: button
        label: Standard
        purpose: embed option
      - role: button
        label: Popup
        purpose: embed option
      - role: button
        label: Full screen
        purpose: embed option
      - role: button
        label: Slider
        purpose: embed option
    completion_signals:
      - Form editor was open with a short-answer field.
      - Share tab initially showed a Publish gate.
      - After user-approved publish, Share showed a public form link and embed options.
    changed_or_failed_anchors:
      - old: Share expected to expose embed controls immediately.
        observed: Embed/share controls required publishing first.
    user_confirmation_required:
      - User clicked Publish before Codex inspected embed controls.
    notes: No response collection, integration connection, or further distribution action was taken by Codex.
  - site: whimsical.com
    playbook_path: sites/tools/whimsical.com/site.md
    workflow: create_board_and_locate_export_share_settings
    result: worked
    evidence_level: tested
    account_context:
      plan: unknown
      language: English
      region: unknown
      viewport: desktop
    ui_anchors_observed:
      - role: button
        label: + New Board
        purpose: create a blank board
      - role: button
        label: Close
        purpose: close intro overlay
      - role: button
        label: Share
        purpose: open share panel
      - role: button
        label: Export
        purpose: export option
      - role: button
        label: Embed
        purpose: embed option
      - role: button
        label: Print
        purpose: print option
      - role: switch
        label: Enable public access
        purpose: public-access control
    completion_signals:
      - A new board opened.
      - Board toolbar and header controls were visible.
      - Share panel showed Share, Export, Embed, Print, public-access controls, and embed code.
    changed_or_failed_anchors: []
    user_confirmation_required: []
    notes: Stopped before enabling public access, sharing, exporting, printing, or inviting.
```
