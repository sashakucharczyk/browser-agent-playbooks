# browser-agent-playbooks

Open playbooks for effective browser-based AI agents navigating web apps through their UIs.

## What This Is

This repository collects practical, app-specific notes for agents that operate normal web apps through a browser session. Think of it as an operating map for UI-based workflows: where to start, what controls matter, what visible labels are useful, where results appear, and what states commonly interrupt the flow.

The goal is to make browser-based agent work more effective and easier to inspect, especially when an official API, plugin, connector, or MCP server is unavailable, limited, expensive, or unnecessary for a user-directed task.

## Initial Areas

- Social media: LinkedIn, Instagram, Facebook, X / Twitter, Reddit, TikTok
- LLM web apps: ChatGPT, Claude, Gemini, Perplexity, Grok
- Tools: CRMs, support desks, project management apps, messaging tools, admin dashboards, analytics tools

## What A Playbook Should Capture

- Common workflows
- Entry states
- Durable UI anchors such as visible labels, roles, and landmarks
- Completion signals
- Result locations
- Known modals, banners, login states, plan limits, and interruptions
- Boundaries where user confirmation should be required

## Repository Layout

    sites/
      social-media/
      llms/
      tools/
    templates/
      site-playbook.md
    CONTRIBUTING.md
    LICENSE

## Starting A New Site Playbook

Copy `templates/site-playbook.md` into the relevant category folder, preferably under a folder named for the site domain.

Example:

    sites/llms/claude.ai/site.md

## Notes

These playbooks are descriptive guides, not guarantees. Web apps change often, account states differ, and browser agents should still inspect the live page before acting.

Do not include credentials, cookies, tokens, private data, or instructions for bypassing access controls.
