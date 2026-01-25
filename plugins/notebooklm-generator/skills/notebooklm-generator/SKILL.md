---
name: notebooklm-generator
description: Generate study materials (Flashcards, Quiz, Infographic, Slide Deck) from a URL using NotebookLM.
argument-hint: "[url]"
model: haiku
allowed-tools: mcp__playwright__browser_navigate, mcp__playwright__browser_click, mcp__playwright__browser_type, mcp__playwright__browser_wait_for, mcp__playwright__browser_snapshot, mcp__playwright__browser_fill_form, mcp__playwright__browser_select_option
---

# NotebookLM Study Materials Generator

Generate study materials (Flashcards, Quiz, Infographic, Slide Deck) from a URL using NotebookLM.

## Usage

```
/notebooklm-generate <url>
```

## Arguments

- `url` (required): A YouTube video URL or website URL to generate study materials from

## Workflow

When this skill is invoked, execute the following steps using Playwright MCP:

### Step 1: Open NotebookLM
Navigate to `https://notebooklm.google.com/`

### Step 2: Create New Notebook
- Wait for the page to fully load (notebooks list should be visible)
- Click the "Create new notebook" button

### Step 3: Add Source URL
- In the dialog that appears, click the "Websites" button
- Paste the provided URL into the "Enter URLs" textbox
- Click the "Insert" button
- Wait for the source to be added (the dialog should close and source should appear in the Sources panel)

### Step 4: Generate Study Materials
Click each of the following buttons in the Studio panel (right side):
1. **Flashcards** button
2. **Quiz** button
3. **Infographic** button
4. **Slide Deck** button

### Step 5: Confirm Completion
Report to the user that all 4 study materials are being generated:
- Flashcards
- Quiz
- Infographic
- Slide Deck

### Step 6: Return Notebook URL
- Get the current browser URL (it should be in the format `https://notebooklm.google.com/notebook/<notebook-id>`)
- Return this URL to the user so they can access the notebook directly

## Example

```
/notebooklm-generate https://www.youtube.com/watch?v=AuZoDsNmG_s
/notebooklm-generate https://openai.com/index/unrolling-the-codex-agent-loop/
```

## Notes

- The user must be logged into Google account in the browser
- YouTube videos must be public and have transcripts available
- Websites must have accessible text content (paid articles may not work)
- Generation may take some time depending on the content length
