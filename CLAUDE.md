# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

agent-zym is a Claude Code plugin marketplace containing plugins that extend Claude's capabilities. The repository hosts marketplace plugins with skills and hooks.

## Repository Structure

- `.claude-plugin/marketplace.json` - Marketplace configuration defining available plugins
- `plugins/` - Plugin directory, each plugin has its own `.claude-plugin/plugin.json`
- `codex/` - Helper utilities for Codex integration

### Current Plugins

1. **linkedin-feed-brief** - Collects and summarizes LinkedIn feed posts using Playwright MCP (Extension Mode)
2. **terminal-notifier-hook** - macOS terminal-notifier hook for Claude Code notifications

## Commands

```bash
# Install dependencies (uses uv package manager)
uv sync

# Run notifier helper (for Codex turn-complete notifications)
python3 codex/notifier.py '{"type": "agent-turn-complete", ...}'
```

## Plugin Development

### Marketplace Configuration

Edit `.claude-plugin/marketplace.json` to add/modify plugins. Each plugin entry needs:
- `name` - Plugin identifier
- `description` - Short description
- `source` - Relative path to plugin directory

### Plugin Structure

Each plugin in `plugins/` contains:
- `.claude-plugin/plugin.json` - Plugin metadata
- `skills/` - Skill definitions with `SKILL.md` files (optional)
- `hooks/` - Hook definitions with `hooks.json` (optional)

### Skills

Skills are defined in `SKILL.md` files with YAML frontmatter (name, description) followed by detailed instructions. Reference files go in `references/` and scripts in `scripts/`.

## Environment Variables

For `codex/notifier.py`:
- `SLACK_BOT_TOKEN` - Slack bot authentication token
- `SLACK_CHANNEL` - Target Slack channel for notifications

## Notes

- Python 3.14+ required
- macOS notifications require `terminal-notifier` to be installed
- The linkedin-feed-brief plugin requires Playwright MCP configured in Extension Mode
