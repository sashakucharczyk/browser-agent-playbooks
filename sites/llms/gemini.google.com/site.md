# Gemini Site Playbook

## Metadata

- Site: `gemini.google.com`
- Category: `llms`
- Primary entry point: `https://gemini.google.com/app`
- Last verified: `2026-05-11`
- Verified with: Codex Chrome plugin controlling a signed-in Chrome session
- Verification depth: New chat page, side navigation, composer, tools menu, mode picker, and upload menu were observed. No prompt was submitted during this verification pass.

## What This Playbook Helps With

Use this playbook when an agent needs to operate Gemini through the normal web UI: start a new chat, prepare a prompt, inspect tool/mode settings, attach approved files, or extract a model reply after a user-approved send.

## Fast Path: Prepare And Send A Prompt

1. Open `https://gemini.google.com/app`.
2. Handle any blocking modal before using the composer. Observed modal: `Bring your memories with you` with buttons `Not now` and `Get started`.
3. Find the composer with role `textbox` and accessible name `Enter a prompt for Gemini`.
4. Fill the prompt. The placeholder/visible text may read `Ask Gemini`.
5. Confirm the `Send message` button becomes enabled.
6. Click `Send message` only after the user-approved prompt is final.
7. Wait until generation controls disappear and the answer text is stable before extracting the latest response.

## Important UI Anchors

| Area | Anchor | Purpose |
| --- | --- | --- |
| Main menu | button `Main menu` | Opens/closes the side navigation. |
| New chat | link `New chat` in side navigation | Starts a new Gemini chat. |
| Temporary chat | button `Temporary chat` | Starts a non-persistent chat mode. Use only if requested. |
| Upgrade | link `Upgrade to Google AI Plus` | Upgrade path. Do not use unless requested. |
| Composer | textbox `Enter a prompt for Gemini` | Main prompt input. |
| Upload | button `Open upload file menu` | Opens file, Drive, and Photos attachment options. |
| Tools | button `Tools` | Opens optional tool modes. |
| Mode picker | button `Open mode picker` | Opens speed/reasoning/model options. |
| Voice | button `Microphone` | Voice input. Do not use unless requested. |
| Submit | button `Send message` | Disabled until prompt text is present. |

## Suggested Prompt Chips

Observed quick-start chips:

- `Create image`
- `Create music`
- `Help me learn`
- `Write anything`
- `Boost my day`

Treat these as convenience shortcuts, not stable workflow dependencies.

## Tools Menu

Open with button `Tools`.

Observed menu items:

| Item | Purpose | Agent handling |
| --- | --- | --- |
| `Create image` | Image generation mode. | Use only if the user asks for image generation. |
| `Canvas` | Canvas/workspace mode. | Use only when a persistent editable workspace is useful. |
| `Deep research` | Research mode. | Use for research tasks only with user intent. |
| `Create music` | Music generation mode. | Use only if requested. |
| `Guided learning` | Tutoring/learning mode. | Use only for learning workflows. |

## Mode Picker

Open with button `Open mode picker`.

Observed options:

| Item | Meaning |
| --- | --- |
| `Fast` | Faster answers. |
| `Thinking` | Selected in observed account; meant for more complex problems. |
| `Pro` | Advanced math/code option with upgrade messaging. |
| `Upgrade` | Upgrade path for more access. |

Do not change mode unless the user asks or the task explicitly calls for speed versus deeper reasoning.

## Upload Menu

Open with button `Open upload file menu`.

Observed items:

| Item | Purpose | Agent handling |
| --- | --- | --- |
| `Upload files` | Uploads documents, data, or code files from local disk. | Requires explicit file-level approval. |
| `Add from Drive` | Adds Google Drive files such as Sheets, Docs, or Slides. | Requires approval and target-file confirmation. |
| `Google Photos` | Adds images from Google Photos. | Requires approval; likely personal data. |

## Known States And Interruptions

| State | How it appears | Suggested handling |
| --- | --- | --- |
| Login required | Google sign-in or account chooser. | Stop and ask the user to sign in/select account. |
| Memory import modal | Heading `Bring your memories with you`; buttons `Not now`, `Get started`. | Prefer `Not now` unless the user explicitly wants migration. |
| Upgrade prompt | `Upgrade to Google AI Plus`, `Upgrade`, or gated Pro option. | Do not upgrade. Continue with available mode or ask. |
| Disabled send | `Send message` button disabled. | Fill the composer first; do not click disabled controls. |
| File/Drive/Photos picker | Upload menu or Google picker. | Stop unless user approved the source and file. |

## Boundaries

Require explicit user confirmation before:

- Sending private, proprietary, or personal data to Gemini.
- Uploading local files, Drive files, or Google Photos.
- Turning on tools like Deep research, Canvas, image, music, or guided learning if they change output type or persistence.
- Using Temporary chat if the user expects chat history.
- Selecting upgrade-gated modes or paid features.

## Efficiency Notes For Agents

- Use `textbox` named `Enter a prompt for Gemini` and `button` named `Send message` rather than coordinate clicks.
- The upload and tools menus expose clear text labels; inspect those menus before assuming a feature is unavailable.
- The mode picker gives a compact speed/depth switch. Check it only when model choice matters.
- Treat quick-start chips as optional; direct composer entry is the stable workflow.

