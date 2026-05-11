# ChatGPT Site Playbook

## Metadata

- Site: `chatgpt.com`
- Category: `llms`
- Primary entry point: `https://chatgpt.com/`
- Last verified: `2026-05-11`
- Verified with: Codex Chrome plugin controlling a signed-in Chrome session
- Verification depth: Home/new chat page, sidebar, composer, file menu, and mode picker were observed. No prompt was submitted during this verification pass.

## What This Playbook Helps With

Use this playbook when an agent needs to operate ChatGPT through the normal web UI: start a chat, prepare a user-approved prompt, inspect mode/tools, attach approved files, or extract the latest assistant reply.

## Fast Path: Prepare And Send A Prompt

1. Open `https://chatgpt.com/`.
2. If needed, click link `New chat` in the sidebar or use the existing new-chat home page.
3. Find the composer with role `textbox` and accessible name `Chat with ChatGPT`.
4. Fill the composer with the approved prompt. Observed placeholder text: `Ask anything`.
5. Submit deliberately:
   - Prefer pressing Enter from the focused composer when the prompt is final and a single-message send is intended.
   - If using a button, scope the click to the right side of the composer. In the observed DOM, the submit buttons near the composer did not expose stable accessible names before text was entered.
6. Wait until the response is stable, any stop-generation control is gone, and the composer is usable again.
7. Extract the latest assistant message from the main conversation transcript.

## Important UI Anchors

| Area | Anchor | Purpose |
| --- | --- | --- |
| Sidebar | navigation `Sidebar` / `Chat history` | Holds new chat, search, GPTs, projects, and recents. |
| New chat | link `New chat` | Starts a fresh chat. Keyboard hint observed: `Control Shift O`. |
| Search chats | button `Search chats` | Searches chat history. Keyboard hint observed: `Control K`. |
| Codex | link `Codex` | Opens ChatGPT Codex area, not normal chat. |
| GPTs | section/button `GPTs` | Lists custom GPTs. |
| Projects | section/button `Projects` | Lists projects and `New project`. |
| Composer | textbox `Chat with ChatGPT` | Main prompt input. |
| Attach/tools | button `Add files and more` | Opens file attachment menu. |
| Mode picker | button such as `Extended` | Opens model/reasoning options. |
| Voice | buttons `Start dictation` and `Start Voice` | Voice input/session controls. |
| Suggested actions | buttons `Create an image`, `Write or edit`, `Look something up` | Prompt/tool shortcuts. |

## Add Files Menu

Open with button `Add files and more`.

Observed menu items:

| Item | Purpose | Agent handling |
| --- | --- | --- |
| `Add photos & files` / `Ctrl+U` | Upload local files/images. | Requires explicit user approval for each file. |
| `Recent files` | Reuses recent file attachments. | Requires confirmation because file identity may be ambiguous. |

More file or connector options may appear depending on account, workspace, project, or current model.

## Mode Picker

Open with the mode button. Observed label: `Extended`.

Observed menu content:

| Item | Meaning |
| --- | --- |
| `Latest - 5.5` | Current model family/label visible in account. |
| `Instant` | Faster mode. |
| `Thinking - Extended` | Checked in observed account. |
| `Configure..` | Opens configuration/options. |

Labels are account- and rollout-dependent. Agents should inspect the current menu before referring to a specific model.

## Known States And Interruptions

| State | How it appears | Suggested handling |
| --- | --- | --- |
| Login required | Sign-in page or account picker. | Stop and ask the user to sign in. |
| Temporary chat | button/banner `Turn on temporary chat`. | Do not toggle unless requested. |
| Group chat | button `Start a group chat`. | Do not start unless requested. |
| Project/GPT context | Sidebar project or GPT selected. | Verify the intended context before sending. |
| File picker | `Add photos & files`, `Recent files`, or OS picker. | Stop unless the user approved the file/source. |
| Unnamed submit button | Composer-adjacent button has no stable accessible name in observed DOM. | Avoid arbitrary unnamed buttons; use composer Enter or a tightly scoped visual/button check. |

## Boundaries

Require explicit user confirmation before:

- Sending private, proprietary, or personal data to ChatGPT.
- Uploading files or reusing recent files.
- Switching models/modes when cost, speed, or quality tradeoffs matter.
- Entering a custom GPT or project if the task requires a clean chat.
- Starting voice, dictation, temporary chat, group chat, Codex, or project creation.

## Efficiency Notes For Agents

- Start with `textbox` named `Chat with ChatGPT`; it is the most stable page anchor.
- Do not rely on the visible homepage heading, which may be personalized.
- Scope sidebar operations carefully; `Codex`, `GPTs`, `Projects`, and normal chat are different surfaces.
- If extracting the answer, wait for the assistant message to stop changing and for the composer to become usable again.
- Treat mode labels such as `Extended` as current-account observations, not universal constants.

