# agent-zym



## What’s in this repo?

- `plugins/`: Marketplace plugins (each plugin ships its own `.claude-plugin/plugin.json` and optional Codex skills).
- `codex/notifier.py`: Optional helper that can send macOS + Slack notifications when a Codex turn completes.

## Plugins

### `linkedin-feed-brief`

Collect and summarize LinkedIn home feed posts using **Playwright MCP** (Extension Mode).

- Docs: `plugins/linkedin-feed-brief/skills/linkedin-feed-brief/README.md`
- Skill instructions: `plugins/linkedin-feed-brief/skills/linkedin-feed-brief/SKILL.md`

### `terminal-notifier-hook`

Sends macOS terminal notifications when Claude Code processes messages. Displays the current working directory, notification type, user input, and assistant output.

- Requires: `terminal-notifier` installed on macOS

### `notebooklm-generator`

Generate study materials (Flashcards, Quiz, Infographic, Slide Deck) from URLs using **Playwright MCP** (Extension Mode).

![NotebookLM Generator Demo](resources/notebook-generator.gif)

- Docs: `plugins/notebooklm-generator/skills/notebooklm-generator/README.md`
- Skill instructions: `plugins/notebooklm-generator/skills/notebooklm-generator/SKILL.md`
- Requires: Google account login in browser

## Install (Claude Code)

```text
/plugins marketplace add ZiminPark/agent-zym
/plugins install linkedin-feed-brief
/plugins install terminal-notifier-hook
/plugins install notebooklm-generator
```

## Install skills (Codex)

```bash
$skill-installer install https://github.com/ZiminPark/agent-zym/tree/main/plugins/linkedin-feed-brief/skills/linkedin-feed-brief
$skill-installer install https://github.com/ZiminPark/agent-zym/tree/main/plugins/notebooklm-generator/skills/notebooklm-generator
```

Restart Codex to pick up new skills.
