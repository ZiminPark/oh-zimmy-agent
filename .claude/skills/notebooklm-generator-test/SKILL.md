---
name: notebooklm-generator-test
description: Test skill to verify the /notebooklm-generate command works with a sample URL
---

# NotebookLM Generate Test

Test the `/notebooklm-generate` command by invoking it with a sample URL.

## Test Steps

1. Display a message explaining that you're testing the NotebookLM generator with a sample URL
2. Invoke the `/notebooklm-generate` command with the following URL: `https://www.youtube.com/watch?v=AuZoDsNmG_s`
3. Wait for the command to complete
4. Report the results back to the user:
   - Success: Study materials generation started (Flashcards, Quiz, Infographic, Slide Deck)
   - Failure: Document any errors or issues encountered

## Notes

- This test requires the user to be logged into a Google account in the browser
- The test URL is a public YouTube video
- The skill should validate that all 4 study material types are being generated
