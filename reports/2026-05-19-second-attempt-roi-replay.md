# Field Report: Second-Attempt ROI Replay

```yaml
result: "+1 worked with narrow updates"
verified_at: 2026-05-19
runtime: Codex Desktop Chrome plugin controlling signed-in Chrome
repo_commit_used: 438f575
private_data_included: false
runs:
  - site: notion.so
    playbook_path: sites/tools/notion.so/site.md
    workflow: create_private_database_page_with_filtered_table_view
    result: worked
    anchors_used:
      - https://www.notion.so/new
      - Database
      - Empty database
      - Settings
      - Filter
      - Add advanced filter
      - Name
      - Contains
      - Value
    completion_signals:
      - Private page appeared in the Private section.
      - Empty database loaded with Table view.
      - Filter panel showed one rule using Name contains Keep.
    scope_notes: Filter was not directly visible on the toolbar; it was under Settings/View settings.
  - site: canva.com
    playbook_path: sites/tools/canva.com/site.md
    workflow: create_template_poster_and_locate_pdf_export
    result: worked
    anchors_used:
      - Templates
      - Poster
      - Preview poster template
      - Customize this template
      - All changes saved
      - Share
      - Download
      - File type
      - PDF
    completion_signals:
      - Template-based poster editor opened.
      - Share menu and Download panel opened.
      - PDF option exposed PDF settings and the final Download button.
    scope_notes: Stopped before downloading, sharing, publishing, printing, or buying.
  - site: figma.com
    playbook_path: sites/tools/figma.com/site.md
    workflow: create_design_file_and_confirm_frame_share_export_controls
    result: worked
    anchors_used:
      - https://www.figma.com/files/
      - https://www.figma.com/design/new
      - Frame
      - Desktop
      - Desktop 1440 x 1024
      - Share
      - Export
    completion_signals:
      - New Untitled design file opened.
      - Desktop - 1 frame-backed layer appeared in the left sidebar.
      - Share and Export controls were visible.
    scope_notes: First-run setup did not appear on this second attempt; frame creation used the editor preset route.
  - site: dropbox.com
    playbook_path: sites/tools/dropbox.com/site.md
    workflow: create_only_me_dummy_folder_and_open_file_request_dialog
    result: worked
    anchors_used:
      - https://www.dropbox.com/home
      - New folder
      - Folder name input
      - Only me
      - Create
      - File requests
      - Request files
      - Cancel
    completion_signals:
      - Dummy folder appeared/opened with Only me selected.
      - Create new request dialog showed Title, Description, Folder for uploaded files, Change Folder, Cancel, and Create.
    scope_notes: Stopped before uploading files, creating or sending requests, sharing links, inviting anyone, or broadening permissions.
  - site: zoom.us
    playbook_path: sites/tools/zoom.us/site.md
    workflow: open_schedule_meeting_form_and_locate_security_controls
    result: worked
    anchors_used:
      - https://us04web.zoom.us/myhome
      - https://us04web.zoom.us/meeting/schedule
      - Topic
      - Security
      - Passcode
      - Waiting Room
      - Save
      - Cancel
    completion_signals:
      - Schedule Meeting form opened.
      - Security, Passcode, Waiting Room, Save, and Cancel controls were visible.
      - Cancel discarded the unsaved draft.
    scope_notes: Stopped before saving or starting a meeting, adding invitees, exposing passcodes or links, connecting calendars, or changing settings.
```
