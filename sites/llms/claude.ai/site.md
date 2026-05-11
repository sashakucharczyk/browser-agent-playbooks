# Claude.ai Site Playbook

## Metadata

- Site: `claude.ai`
- Category: `llms`
- Primary entry point: `https://claude.ai/new`
- Last verified: `2026-05-11`
- Verified with: Codex Chrome plugin controlling a signed-in Chrome session
- Verification depth: New chat page, model picker, add-files menu, and prompt/response completion behavior were observed.

## What This Playbook Helps With

Use this playbook when an agent needs to operate Claude through the normal web UI: start a new chat, send a user-approved prompt, choose or inspect model mode, attach approved files, or extract the latest Claude reply.

## Fast Path: Send A Prompt And Read The Reply

1. Open `https://claude.ai/new`.
2. If a product notice blocks the page, dismiss it only when it has a visible `Dismiss` button.
3. Find the composer with role `textbox` and accessible name `Write your prompt to Claude`.
4. Fill the composer with the approved prompt.
5. Click the `Send message` button after it appears.
6. Wait for generation to finish. Observed completion text: `Claude finished the response`.
7. Extract the latest assistant response from the main conversation transcript, usually near text like `Claude responded:`.

## Important UI Anchors

| Area | Anchor | Purpose |
| --- | --- | --- |
| New chat | link `New chat` | Opens a fresh chat from the sidebar. |
| Search | link `Search` | Searches existing Claude chats. |
| Recent chats | sidebar section `Recents` | Lists previous conversations. |
| Composer | textbox `Write your prompt to Claude` | Main prompt input. |
| Submit | button `Send message` | Sends the prompt once text is present. |
| Attach/tools | button `Add files, connectors, and more` | Opens upload, connector, style, screenshot, and web-search controls. |
| Model/mode | button like `Model: Sonnet 4.6 Adaptive` | Opens model and thinking-mode picker. |
| Voice | button `Use voice mode` | Starts voice interaction. Do not use unless explicitly requested. |
| Incognito | button `Use incognito` | Starts an incognito Claude chat. |

## Add Files / Connectors Menu

Open with button `Add files, connectors, and more`.

Observed menu items:

| Item | Purpose | Agent handling |
| --- | --- | --- |
| `Add files or photos` / `Ctrl+U` | Uploads local files or images. | Requires explicit user approval for each file. |
| `Take a screenshot` | Adds a screenshot to the chat. | Requires confirmation if the screenshot may contain private information. |
| `Add to project` | Adds context/project material. | Requires confirmation because it changes context scope. |
| `Skills` | Opens Claude skills. | Inspect-only unless user asks to enable/use a skill. |
| `Connectors` | Opens connected data sources. | Requires confirmation before connecting or querying private sources. |
| `Web search` | Toggle for web search. Observed checked. | Safe to inspect; changing search mode should be user-directed. |
| `Use style` | Applies a writing style. | Safe only if the user asked for a style. |

## Model Picker

Open with the model button, observed as `Model: Sonnet 4.6 Adaptive`.

Observed options:

| Item | Meaning |
| --- | --- |
| `Opus 4.7` | Upgrade-gated, most capable option in observed account. |
| `Sonnet 4.6` | Checked default in observed account. |
| `Haiku 4.5` | Faster option. |
| `Adaptive thinking` | Switch observed checked. |
| `More models` | Opens additional model choices. |

Do not change model or thinking mode unless the user requested a model choice or the task clearly requires it.

## Completion Signals

Strong signals:

- Visible text `Claude finished the response`.
- The send control returns and no stop-generation control is visible.
- The latest assistant message is stable for at least one short polling interval.

Weak signals:

- Network idle alone. Claude may still be rendering.
- Body text contains the user prompt. That confirms submission, not completion.

## Known States And Interruptions

| State | How it appears | Suggested handling |
| --- | --- | --- |
| Login required | Redirects to sign-in or shows account buttons. | Stop and ask the user to sign in. |
| Product notice | Dialog or banner with `Dismiss`. | Dismiss only if it blocks the composer. |
| Free-plan / upgrade prompt | `Free plan`, `Upgrade`, or upgrade-gated model options. | Do not upgrade. Continue with available model or ask user. |
| File upload picker | Native file chooser or menu item. | Use only for approved files. |
| Connector access | Connector menu or permission flow. | Stop before granting permissions or querying private stores. |

## Boundaries

Require explicit user confirmation before:

- Sending private, proprietary, or personal data to Claude.
- Uploading any file, image, screenshot, or document.
- Connecting external accounts or data sources.
- Changing model/mode if cost, privacy, or capability tradeoffs matter.
- Using incognito mode if the user expects chat history to persist.

## Efficiency Notes For Agents

- Prefer role/name anchors over layout coordinates: `textbox` named `Write your prompt to Claude`, `button` named `Send message`, and the model button beginning with `Model:`.
- If the prompt is already visible in the composer, fill/replace instead of typing character by character.
- Poll for explicit completion text before extracting the answer.
- Keep the sidebar open only if you need chat history; otherwise work from the main region.

