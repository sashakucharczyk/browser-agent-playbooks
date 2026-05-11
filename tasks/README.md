# Task Playbooks

Task playbooks describe useful work that may span one or more sites.

Site playbooks answer: "How does this web app work through the browser UI?"

Task playbooks answer: "How should an agent accomplish this useful job end to end?"

## Examples

- Analyze CRM pipeline quality from a visible CRM report.
- Compare answers across Claude, ChatGPT, and Gemini.
- Draft a LinkedIn post but stop before publishing.
- Extract visible profile context from LinkedIn for user review.

## Suggested Structure

Create one folder per task:

    tasks/<task-name>/task.md

Start from `templates/task-playbook.md`.

## Reporting

When a task playbook works or fails, report both the task and the site playbooks involved. A task may fail because the site UI changed, because the task logic was wrong, or because the user's account context was different.

