# agent-zym



## What’s in this repo?

- `plugins/`: Marketplace plugins (each plugin ships its own `.claude-plugin/plugin.json` and optional Codex skills).
- `codex/notifier.py`: Optional helper that can send macOS + Slack notifications when a Codex turn completes.

## Plugins

### `linkedin-feed-brief`

Collect and summarize LinkedIn home feed posts using **Playwright MCP** (Extension Mode).

- Docs: `plugins/linkedin-feed-brief/skills/linkedin-feed-brief/README.md`
- Skill instructions: `plugins/linkedin-feed-brief/skills/linkedin-feed-brief/SKILL.md`

## Install (Claude Code)

```text
/plugins marketplace add ZiminPark/agent-zym
/plugins install linkedin-feed-brief
```

## Install skill (Codex)

```bash
$skill-installer install https://github.com/ZiminPark/agent-zym/tree/main/plugins/linkedin-feed-brief/skills/linkedin-feed-brief
```

Restart Codex to pick up new skills.
