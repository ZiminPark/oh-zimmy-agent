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
3. **notebooklm-generator** - Generates study materials (Flashcards, Quiz, Infographic, Slide Deck) from URLs using NotebookLM with Playwright MCP (Extension Mode)

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

Skills are defined in `SKILL.md` files with YAML frontmatter followed by detailed instructions.

#### Frontmatter fields:
- `name` - Skill identifier (becomes `/slash-command`)
- `description` - What the skill does (Claude uses this to decide when to invoke automatically)
- `argument-hint` - Optional hint showing expected arguments during autocomplete (e.g., `[url]`, `[filename]`)
- `allowed-tools` - Tools Claude can use without asking permission (comma-separated list with MCP prefix, e.g., `mcp__playwright__browser_navigate, mcp__playwright__browser_click`)

#### Supporting files:
- Reference files go in `references/`
- Scripts go in `scripts/`

### Plugin Versioning

**When to update the version:**
- Any changes to skill definitions, frontmatter, workflow, or behavior require a version bump
- Documentation-only changes (README, comments) require a version bump
- Changes to allowed-tools, argument-hint, or any skill YAML frontmatter require a version bump

**How to update the version:**
1. Open `plugins/<plugin-name>/.claude-plugin/plugin.json`
2. Update the `version` field following Semantic Versioning (MAJOR.MINOR.PATCH):
   - **Patch version** (1.1.x): Documentation updates, configuration refinements, bug fixes
   - **Minor version** (1.x.0): New skills, new features, significant improvements
   - **Major version** (x.0.0): Breaking changes, major restructuring

Example:
```json
{
  "name": "notebooklm-generator",
  "version": "1.1.1"
}
```

## Environment Variables

For `codex/notifier.py`:
- `SLACK_BOT_TOKEN` - Slack bot authentication token
- `SLACK_CHANNEL` - Target Slack channel for notifications

## Notes

- Python 3.14+ required
- macOS notifications require `terminal-notifier` to be installed
- The linkedin-feed-brief and notebooklm-generator plugins require Playwright MCP configured in Extension Mode
- The notebooklm-generator plugin requires Google account login in the browser
