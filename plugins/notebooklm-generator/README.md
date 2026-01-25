# notebooklm-generator

This skill generates study materials (Flashcards, Quiz, Infographic, Slide Deck) from URLs using **Playwright MCP** in **Extension Mode** (browser-based). Extension Mode lets the agent operate inside a real Chrome instance to interact with NotebookLM.

Reference: [`https://github.com/microsoft/playwright-mcp/blob/main/extension/README.md`](https://github.com/microsoft/playwright-mcp/tree/main/packages/extension)

## When this skill should run

Use `notebooklm-generate` when the user wants to:

- Generate study materials from a YouTube video URL or website URL
- Create Flashcards for key concepts
- Generate a Quiz to test understanding
- Create an Infographic summarizing the content
- Generate a Slide Deck presentation
- Save the materials for later review

## Install this skill

### Codex

```bash
$skill-installer install https://github.com/ZiminPark/agent-zym/tree/main/plugins/notebooklm-generator/skills/notebooklm-generator
```

Restart Codex to pick up new skills.

### Claude Code

```bash
/plugins marketplace add ZiminPark/agent-zym
/plugins install notebooklm-generator
```

## Minimal setup (Playwright MCP Extension Mode)

1) Install **Google Chrome**.

2) Install the **Playwright MCP** Chrome extension:
   - Download the extension build as described in the reference README.
   - In Chrome, go to `chrome://extensions`, enable **Developer mode**, then **Load unpacked**.

3) Start the MCP server in Extension Mode:
   ```bash
   npx @playwright/mcp@latest --extension
   ```

4) In your MCP client, connect to the Playwright MCP server. Once connected, the agent can drive the same Chrome session to navigate to NotebookLM and generate study materials.

5) Ensure you are logged into your Google account in the browser before running this skill.

## Requirements

- **Google Account**: Must be logged in to NotebookLM
- **YouTube Videos**: Must be public and have transcripts available
- **Websites**: Must have accessible text content (paid articles may not work)
- **Playwright MCP Extension**: Required for browser automation
